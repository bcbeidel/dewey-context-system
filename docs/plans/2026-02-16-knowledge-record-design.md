# Design: The Knowledge Record

> A knowledge record is a single markdown file that distills external sources
> into curated, structured knowledge optimized for AI agent consumption and
> human cognition.
>
> This project is a content engine — it produces, validates, and maintains
> high-quality atomic markdown files. How those files reach an agent (Claude
> Code skills, Cursor rules, MCP resources, RAG pipelines, flat directories)
> is a delivery concern, not a content concern.

---

## 1. Why This Exists

Three findings from agent context research drive this design:

**Position matters.** LLMs exhibit a U-shaped attention curve — the beginning
and end of context receive the most attention, the middle the least. The most
actionable content must be at the top.

**Less focused beats more unfocused.** 300 focused tokens outperform 113K
unfocused tokens. Context rot degrades performance 13–85% as length increases.
Every line must earn its place.

**Progressive disclosure is the strongest lever.** Metadata-only access reduces
tokens up to 98% versus full content. The format must support agents that scan
metadata, read summaries, then optionally load full content.

No existing tool or standard addresses all three. A landscape survey of 96
open-source tools found mature creation and distribution layers but an empty
quality and maintenance layer. DITA provides typed topics but uses XML (80%
more tokens). Diataxis provides content-type taxonomy but no file-level
specification. The Agent Skills ecosystem provides progressive disclosure
but no content quality standard.

Research artifacts:
- `artifacts/research/2026-02-16-agent-context-effectiveness-deep-dive.md`
- `artifacts/research/2026-02-16-knowledge-record-design-research.md`
- `artifacts/research/2026-02-16-context-quality-open-source.md`

---

## 2. Core Premise

The project has one job: **produce excellent markdown files from external
sources.** Everything else — the quality checks, the CLI, the operations —
exists to make that job reliable and repeatable.

This means:

- **The file is the product.** Not a database, not an API, not a plugin — a
  markdown file that any system can read.
- **Quality is the differentiator.** Anyone can create markdown. The value is
  in the curation discipline: source grounding, position-aware structure,
  size constraints, counter-evidence, progressive disclosure metadata.
- **Delivery is someone else's problem.** The same file works in Claude Code's
  `references/` directory, Cursor's `.cursor/rules/`, a RAG ingestion
  pipeline, or a static site. The content engine doesn't know or care.

---

## 3. The Format

The full specification lives in `docs/plans/2026-02-16-knowledge-record-specification.md`.
This section summarizes the key structural elements.

### 3.1 Frontmatter

Every knowledge record starts with YAML frontmatter:

```yaml
---
summary: "1-3 sentence standalone description. Must make sense
  without reading the body."
sources:
  - url: https://example.com/primary-source
    title: "Source Title"
last_validated: 2026-02-16
relevance: "Who this helps and when"
depth: working
tags: [optional, keywords]
related:
  - ../other-area/related-topic.md
---
```

| Field | Required | Purpose |
|-------|----------|---------|
| `summary` | Yes | Standalone description for progressive disclosure |
| `sources` | Yes | Primary source URLs — the path to the original is always clear |
| `last_validated` | Yes | When content was last verified against sources |
| `relevance` | Yes | Information scent: who this helps and when |
| `depth` | Yes | `overview` or `working` |
| `tags` | No | Cross-cutting keywords for discovery |
| `related` | No | Non-hierarchical connections to peer topics |

### 3.2 Working Depth

Sections ordered for the U-shaped attention curve:

```
# Title

## Guidance          ← primacy: most actionable content first
## Context           ← why this matters, causal reasoning
## In Practice       ← concrete examples resist the attention valley
## Pitfalls          ← recency: warnings stick at the end
## Quick Reference   ← optional: terse lookup data
## Go Deeper         ← source links and further reading
```

### 3.3 Overview Depth

```
# Area Name

## What This Covers
## Topics
## Key Sources
```

### 3.4 Size Budgets

| Depth | Lines | Token Guidance |
|-------|-------|---------------|
| Overview | 5-150 | ~200-2,000 |
| Working | 10-500 | ~500-5,000 |
| Summary field | 1-3 sentences | ~30-80 |

Line counts are enforceable (deterministic). Token budgets are author guidance.

### 3.5 Source Integration

**Citation style:** Reference-style links. URLs defined once at the bottom.

```markdown
The strategy-stealing argument proves X cannot lose ([Hamkins][hamkins]).

[hamkins]: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
```

**Grounding standard:** Every factual claim in Guidance has an inline citation.
A skeptical reader can trace any key claim to a primary source in one click.

**Counter-evidence:** During research, actively search for reasons the guidance
might be wrong. Findings go in Pitfalls.

### 3.6 Curation Metadata

Source evaluations and research provenance are stored separately from the
record. This metadata serves the curation process, not the consumer. Every
line in the record serves the reader.

---

## 4. The Data Model

A knowledge record decomposes into four parts:

```
KnowledgeRecord
+-- frontmatter: dict          # YAML key-value pairs
+-- title: string              # H1 heading text
+-- sections: ordered list     # H2 sections with content
|   +-- Section
|       +-- heading: string    # heading text (without ##)
|       +-- content: string    # everything between this ## and next
+-- link_defs: ordered list    # reference-style [ref]: url lines
```

**Round-trip invariant:** Parsing a record and rendering it back produces
semantically identical output. Whitespace normalization (consistent blank
lines between sections) is acceptable.

---

## 5. Atomic Operations

These operations are the complete interface for manipulating knowledge records.
Everything else — validation, scaffolding, migration, workflows — composes
from these primitives.

### 5.1 Parse and Render

| Operation | Input | Output |
|-----------|-------|--------|
| `parse` | file path or text | KnowledgeRecord |
| `render` | KnowledgeRecord | markdown text |
| `write` | KnowledgeRecord + path | file on disk |

### 5.2 Frontmatter

| Operation | Input | Output |
|-----------|-------|--------|
| `get_field` | record, key | value or null |
| `set_field` | record, key, value | new record |
| `remove_field` | record, key | new record |

### 5.3 Sections

| Operation | Input | Output |
|-----------|-------|--------|
| `get_section` | record, heading | Section or null |
| `add_section` | record, heading, content, after? | new record |
| `remove_section` | record, heading | new record + removed section |
| `replace_section` | record, heading, new content | new record |
| `rename_section` | record, old heading, new heading | new record |
| `reorder_sections` | record, ordered heading list | new record |

**Matching:** Section lookup uses case-insensitive substring matching.
`get_section(record, "guidance")` matches `## Guidance`, `## Key Guidance`.

### 5.4 Links

| Operation | Input | Output |
|-----------|-------|--------|
| `get_link_defs` | record | dict of {ref: url} |
| `set_link_def` | record, ref, url | new record |
| `inline_to_ref_links` | record | new record with [text][ref] style |

### 5.5 Provenance

| Operation | Input | Output |
|-----------|-------|--------|
| `extract_source_eval` | record | structured evaluation data or null |
| `write_provenance` | path, data | JSON file on disk |
| `read_provenance` | path | data or null |

### 5.6 Scaffolding

| Operation | Input | Output |
|-----------|-------|--------|
| `create_record` | title, depth, frontmatter, sections? | KnowledgeRecord |
| `stub_sections` | depth | list of Section with placeholder content |

**Canonical section lists:**

```
working:  [Guidance, Context, In Practice, Pitfalls, Go Deeper]
overview: [What This Covers, Topics, Key Sources]
```

### 5.7 Structural Validation

| Operation | Input | Output |
|-----------|-------|--------|
| `validate_structure` | record | list of issues |

Checks what can be determined from the record alone:

- Has frontmatter with required fields
- Has a title (H1)
- Has required sections for its depth
- Sections are in canonical order
- Within size bounds for its depth
- `depth` value is valid
- `summary` is 1-3 sentences
- `sources` has at least one entry

---

## 6. Quality Layers

The operations compose into layers, each with a clear boundary:

```
+-----------------------------------------------------------+
|  Layer 4: Content Creation                                 |
|  LLM-driven: research, author, evaluate, revise            |
|  Composes operations from all layers below                  |
+-----------------------------------------------------------+
|  Layer 3: Intelligence                                     |
|  LLM-assisted quality triggers                              |
|  Input: KnowledgeRecord + context -> flags for review       |
+-----------------------------------------------------------+
|  Layer 2: Cross-File Consistency                           |
|  Deterministic cross-file validation                        |
|  Input: list[KnowledgeRecord] -> issues                     |
+-----------------------------------------------------------+
|  Layer 1: Single-File Quality                              |
|  Deterministic per-file validation                          |
|  Input: KnowledgeRecord -> issues                           |
+-----------------------------------------------------------+
|  Layer 0: Record                                           |
|  Data model, parse, render, CRUD, structural validation     |
|  The foundation everything else imports from                |
+-----------------------------------------------------------+
```

| Layer | Concern | Deterministic? | Examples |
|-------|---------|---------------|---------|
| **0. Record** | What a record IS | Yes | Parse, render, CRUD, structural validation |
| **1. Quality** | Whether a record is GOOD | Yes | Readability, source diversity, citation grounding, freshness, size |
| **2. Consistency** | Whether records agree with EACH OTHER | Yes | Duplicate detection, link graph, naming conventions |
| **3. Intelligence** | Whether a record needs REVIEW | No (LLM) | Source drift, depth accuracy, summary quality |
| **4. Creation** | PRODUCING and MAINTAINING records | No (LLM) | Research, author, evaluate, revise |

**Dependency rule:** Each layer depends only on the layers below it.

**Portability:** Layers 0-2 are pure deterministic code — any language, any
platform, no LLM required. Layer 3 needs an LLM but no specific provider.
Layer 4 is the orchestration layer where delivery mechanism matters.

---

## 7. CLI

Every atomic operation is exposed as a CLI subcommand:

```
record parse <file>                              -> JSON
record render <json-file>                        -> markdown to stdout
record create --title T --depth D --output PATH  -> new file
record validate <file>                           -> JSON issues list

record get-field <file> <key>                    -> value
record set-field <file> <key> <value>            -> updates file
record remove-field <file> <key>                 -> updates file

record get-section <file> <heading>              -> section content
record add-section <file> <heading> [--after H] [--content-file F | --content C]
record remove-section <file> <heading>           -> prints removed content
record replace-section <file> <heading> [--content-file F | --content C]
record rename-section <file> <old> <new>
record reorder-sections <file> <h1> <h2> ...

record migrate <file>                            -> deterministic v1->v2

record extract-provenance <file>                 -> JSON to stdout
record write-provenance <file> <json>            -> writes provenance file
```

All commands that modify files print a JSON action summary to stdout.
All commands exit 0 on success, non-zero on error.

The CLI is the boundary between the LLM (which decides what content to write)
and the record module (which handles structural manipulation). Any LLM —
Claude, GPT, Gemini, local models — can call these commands.

---

## 8. Content Principles

These principles govern what gets written into records. They are the authoring
standard that the quality layers check after the fact.

**Grounded in sources.** Every claim traces to a primary source. The record
is a guide, not a replacement.

**Earns every line.** If a line doesn't serve the reader, it doesn't belong.
Context rot degrades performance as length increases.

**Explain the why.** Causal reasoning, not prescriptive rules. "Center is
strongest because it touches 4 winning lines" not "always play center."

**Concrete before abstract.** Lead with specific examples, then generalize.

**One level of depth.** Don't mix beginner and expert content. The depth
field signals the audience. Content that helps novices hinders experts.

**Self-contained.** Each record makes sense without reading other records.

**Honest about limitations.** If the guidance has conditions where it doesn't
apply, say so.

---

## 9. Progressive Disclosure

The format supports multi-tier progressive disclosure. The specific tiers
depend on the delivery mechanism, but the record provides content for each:

| Tier | Record Provides | Typical Cost |
|------|----------------|-------------|
| **Discovery** | `relevance` field | ~10-20 tokens |
| **Summary** | `summary` field | ~30-80 tokens |
| **Full content** | Complete record body | ~500-5,000 tokens |
| **Lookup** | Quick Reference section | Subset of full |
| **Provenance** | Separate metadata file | Out-of-band |

Each tier is independently useful — an agent can stop at any level and act
on what it has.

---

## 10. Delivery Adapters

The content engine produces files. Delivery adapters package those files
for specific consumers. This is an explicit architectural boundary.

### 10.1 The Boundary

```
+---------------------------+     +---------------------------+
|     Content Engine         |     |    Delivery Adapters       |
|                           |     |                           |
|  Record format & spec      |     |  Claude Code skill        |
|  Atomic operations         |     |  Cursor rules             |
|  Quality validation        | --> |  MCP resource server      |
|  Content creation          |     |  RAG ingestion pipeline   |
|  Provenance tracking       |     |  Static site generator    |
|                           |     |  GitHub Action             |
|  Produces: .md files       |     |  Consumes: .md files      |
+---------------------------+     +---------------------------+
```

### 10.2 What Adapters Do

A delivery adapter reads knowledge record files and packages them for a
specific platform. The adapter's responsibilities:

1. **Discovery** — how the platform finds available records (manifest,
   directory scan, API endpoint)
2. **Loading** — how the platform reads record content (file read, HTTP
   fetch, tool call)
3. **Progressive disclosure** — how the platform implements tiered access
   (frontmatter-only scan, summary extraction, full load)
4. **Integration** — platform-specific conventions (file paths, naming,
   configuration)

### 10.3 Example Adapters

**Claude Code:** Records live in a skill's `references/` directory. SKILL.md
provides the manifest with summaries extracted from frontmatter. Workflows
guide Claude through creation and maintenance.

**Cursor:** Records live in `.cursor/rules/` or a referenced directory.
A `.cursorrules` file provides the manifest.

**MCP Server:** Records exposed as MCP resources. The server reads
frontmatter for the resource list, serves full content on request.

**RAG Pipeline:** Records chunked by section. Frontmatter fields become
metadata for retrieval filtering. Summary field becomes the document
description.

**CI/CD:** Quality validation (Layers 0-2) runs as a GitHub Action or
pre-commit hook. No LLM required.

---

## 11. Workflows

Workflows are sequences of operations that create and maintain records.
They define the boundary between deterministic operations (code) and
judgment (LLM).

### 11.1 Create

```
LLM                                 Code (record operations)
---                                 -----------------------
Research topic from sources
Evaluate source quality
Search for counter-evidence
Write section content
Write summary
                                    create_record(title, depth, fm, sections)
                                    write(path, record)
                                    write_provenance(prov_path, eval_data)
                                    validate_structure(record)
Review validation issues
Fix and re-render if needed
                                    write(path, revised_record)
```

### 11.2 Update Section

```
                                    record = parse(path)
                                    section = get_section(record, heading)
Review existing content
Write revised content
                                    record = replace_section(record, heading, new)
                                    record = set_field(record, "last_validated", today)
                                    write(path, record)
```

### 11.3 Validate

```
                                    record = parse(path)
                                    structural = validate_structure(record)
                                    quality = validate_quality(record)
                                    consistency = validate_consistency(all_records)
Report issues
                                    triggers = check_triggers(record)
Evaluate flagged items (Layer 3)
Decide: pass / needs update / stale
```

### 11.4 Refresh Sources

```
                                    record = parse(path)
                                    sources = get_field(record, "sources")
                                    prov = read_provenance(prov_path)
Check each source for changes
Assess content accuracy
                                    record = set_field(record, "last_validated", today)
                                    write(path, record)
(If content stale, hand off to Update)
```

---

## 12. What This Enables

**Platform independence.** The same knowledge records work in Claude Code,
Cursor, Copilot, Windsurf, Codex, Gemini CLI, MCP servers, RAG pipelines,
and static sites. The content engine doesn't know which platform will
consume its output.

**Quality without lock-in.** Layers 0-2 are pure deterministic code with
no dependencies. They can be implemented in any language, run in any
environment, and validate any conforming markdown file — regardless of
how it was created or where it will be consumed.

**LLM independence.** The CLI is the interface between the LLM and the
record module. Any model that can call shell commands can create and
maintain knowledge records. The content principles tell the LLM what
to write. The validators tell it whether it succeeded.

**Composable tooling.** New tools (linters, formatters, converters,
importers, exporters) compose from the same atomic operations without
understanding the full system.

**Progressive disclosure by default.** Every record carries its own
discovery metadata, summary, and full content — enabling any delivery
mechanism to implement tiered loading without additional infrastructure.

---

## 13. Example Record

```markdown
---
summary: "Tic-tac-toe is a solved game where perfect play always draws.
  Forks -- creating two simultaneous threats -- are the only winning
  mechanism. The Newell & Simon priority list gives optimal play."
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe -- Wikipedia"
  - url: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
    title: "Tic-Tac-Toe and Variants -- Joel David Hamkins"
  - url: https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/
    title: "The Best Strategy For Tic-Tac-Toe -- Presh Talwalkar"
  - url: https://brilliant.org/wiki/tic-tac-toe/
    title: "Tic Tac Toe -- Brilliant.org"
  - url: https://www.sethcoulson.com/tic-tac-toe/counting/
    title: "Counting (Tic-Tac-Toe) -- Seth Coulson"
last_validated: 2026-02-16
relevance: "First-move advantage, forcing draws, forks, and the solved game tree"
depth: working
tags: [game-theory, solved-games, minimax]
---

# Optimal Strategy

## Guidance

**1. The first player (X) cannot lose with perfect play.** A strategy-stealing
argument proves this: if O had a winning strategy, X could "steal" it by going
first ([Hamkins][hamkins]).

**2. Three strategically distinct first moves exist.** Corner, center, and edge.
Every other first move is equivalent by symmetry ([Wikipedia][wiki]).

**3. Center is the strongest opening.** It touches 4 winning lines -- both
diagonals, middle row, middle column. Corners touch 3; edges touch 2. But X
can force a draw from any first move ([Talwalkar][talwalkar]).

**4. Forks are the only winning mechanism.** Every win against a non-perfect
opponent comes from creating two simultaneous threats
([Brilliant.org][brilliant]).

**5. The Newell & Simon priority list gives optimal play.** In order: (1) win,
(2) block, (3) fork, (4) block fork, (5) center, (6) opposite corner, (7) any
corner, (8) any edge ([Wikipedia][wiki]).

## Context

Tic-tac-toe is a solved game -- with perfect play from both sides, it always
ends in a draw. The complete game tree has 255,168 possible games, 5,478
reachable board states, and 765 essentially different positions after symmetry
reduction ([Wikipedia][wiki], [Coulson][coulson]).

Understanding *why* certain moves are optimal builds intuition that transfers
to more complex games.

## In Practice

Consider the opening from X's perspective, starting with a **corner move**:

1. **X plays corner.** Touches 3 winning lines -- creates asymmetry O must
   handle precisely.
2. **O must respond with center.** Any other response lets X force a win.
3. **X plays opposite corner.** Threatens along the diagonal, sets up a fork.
4. **O must block on an edge** to prevent two simultaneous threats.
5. Correct play from both sides -> draw.

The critical concept is the **fork**: placing a mark that creates two winning
threats at once.

## Pitfalls

**"Solved" does not mean "obvious."** The strategy-stealing argument is
non-constructive -- it proves X can't lose without showing how ([Hamkins][hamkins]).

**Edge openings are underestimated.** Unfamiliarity increases opponent error
rates ([Talwalkar][talwalkar]).

**The game's value is pedagogical.** Competitive tic-tac-toe between informed
players is pointless. The real value: teaching minimax, game trees, Nash
equilibria.

## Quick Reference

| Metric | Value |
|--------|-------|
| Total possible games | 255,168 |
| Reachable board states | 5,478 |
| Unique positions (symmetry) | 765 |
| First-player random-play win rate | 58% |

**Newell & Simon:** Win -> Block -> Fork -> Block fork -> Center -> Opposite
corner -> Any corner -> Any edge

**Winning lines:** Center: 4, Corner: 3, Edge: 2

## Go Deeper

- [Tic-tac-toe -- Wikipedia][wiki] -- game enumeration and strategy
- [Tic-Tac-Toe and Variants -- Hamkins][hamkins] -- strategy-stealing proof
- [Best Strategy -- Talwalkar][talwalkar] -- first-move analysis
- [Tic Tac Toe -- Brilliant.org][brilliant] -- fork strategy

[wiki]: https://en.wikipedia.org/wiki/Tic-tac-toe
[hamkins]: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
[talwalkar]: https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/
[brilliant]: https://brilliant.org/wiki/tic-tac-toe/
[coulson]: https://www.sethcoulson.com/tic-tac-toe/counting/
```
