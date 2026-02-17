# Knowledge Record Specification v2 — Clean-Slate Recommendation

> If we threw away all existing templates and designed the ideal knowledge record
> format from first principles, optimizing for both agentic consumption and human
> cognition, this is what I'd build.

---

## The Core Insight

The `summary` field changes everything. Today, the body has to serve double duty:
orient the reader *and* deliver the goods. With a frontmatter summary, the body
is free to lead with the most valuable content. The summary provides context;
the body provides depth.

This unlocks the attention-optimal structure: **Guidance first, context second,
examples third, warnings last.** No preamble needed — the reader already knows
what this topic is about from the summary.

---

## Frontmatter

```yaml
---
summary: "1–3 sentence standalone description. Must make sense without
  reading the body. This is the Wikipedia lead section — it orients the
  reader and lets agents decide whether to load the full file."
sources:
  - url: https://example.com/primary-source
    title: "Source Title"
  - url: https://example.com/another-source
    title: "Another Source"
last_validated: 2026-02-16
relevance: "Who this helps and when — one line of information scent"
depth: working
tags: [optional, cross-cutting, discovery-keywords]
related:
  - ../other-area/related-topic.md
---
```

### Field Definitions

| Field | Required | Type | Purpose |
|-------|----------|------|---------|
| `summary` | Yes (working, overview) | string, 1–3 sentences | Standalone description for Tier 2 progressive disclosure. An agent loading all summaries for a domain area (~500 tokens for 10 topics) can decide what to fully load. |
| `sources` | Yes | list of `{url, title}` | Primary sources. Enforces source primacy. Agents cite these when making recommendations. |
| `last_validated` | Yes | ISO date | When content was last verified against sources. Drives freshness health checks. |
| `relevance` | Yes | string | Information scent for manifest scanning. Always a description, never a tier. Example: `"First-move advantage, forcing draws, forks, and the solved game tree"` |
| `depth` | Yes | enum | `overview` \| `working` \| `reference` — position in the progressive disclosure chain |
| `tags` | No | list of strings | Cross-cutting keywords for discovery. Flat list, no controlled vocabulary. |
| `related` | No | list of relative paths | Explicit non-hierarchical connections to other topics (SKOS `related`). Distinct from Go Deeper links (which are sources/references, not peer relationships). |

### Why `relevance` is Always a Description

The old `core`/`supporting`/`peripheral` tiers served curation prioritization.
That's a curation-plan concern, not a record-level property. At the record level,
relevance should answer "why would I load this?" — which requires a description,
not a category. The curation plan already tracks priority.

### Why `summary` is Not Required for Reference Depth

Reference files are already terse and scannable — their entire body is
effectively a summary. Requiring a summary field would just duplicate the content.

---

## Working Depth — The Core Format

Working-depth files carry the actionable knowledge. This is the format that
matters most.

### Section Structure

```
---
[frontmatter]
---

# Topic Title

## Guidance

[Numbered, bold-principle items. Each starts with a declarative statement
followed by explanation and source citation. This is the section an agent
reads if it can only read one section.]

## Context

[1–3 paragraphs. Why this topic matters. When it applies. How it connects
to the broader domain. Explains the "why" — causal reasoning, not just facts.]

## In Practice

[Concrete examples first, then generalize. Walked scenarios, code blocks,
step sequences, decision tables. The most engaging section for human readers.]

## Pitfalls

[Bold heading per pitfall. Brief explanation. Counter-evidence from research.
Positioned late to benefit from the recency effect — warnings stick when
they're the last substantive content read.]

## Go Deeper

[Bullet list: reference companion first, then primary sources, then further
reading. Serves as the bridge to Tier 4 progressive disclosure.]
```

### Why This Order

```
Attention
  ▲
  │  ██                                           ██
  │  ██ ██                                     ██ ██
  │  ██ ██ ██                               ██ ██ ██
  │  ██ ██ ██ ██                         ██ ██ ██ ██
  │  ██ ██ ██ ██ ██                   ██ ██ ██ ██ ██
  │  ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██
  └──────────────────────────────────────────────────→
     Guidance  Context  In Practice  Pitfalls  Go Deeper
     ▲ primacy          ▲ middle     ▲ recency
       effect             valley       effect
```

| Position | Section | Why It Works Here |
|----------|---------|-------------------|
| 1st (primacy) | **Guidance** | Most actionable content. Gets the highest attention. An agent short on context budget reads this and stops. |
| 2nd | **Context** | Motivation and background. The summary already oriented the reader, so this deepens understanding rather than establishing it from zero. |
| 3rd (middle) | **In Practice** | Examples are inherently engaging — they resist the attention valley better than abstract content. Concrete scenarios hold human attention even in the middle position. |
| 4th (recency) | **Pitfalls** | Warnings benefit from the recency effect. The last substantive content a reader encounters is "what can go wrong" — this sticks. |
| 5th (end) | **Go Deeper** | Links/references. Naturally terminal. No content to miss if attention drops. |

### Section Naming Rationale

| Section | Current Name | Clean-Slate Name | Why |
|---------|-------------|-------------------|-----|
| Actionable recommendations | Key Guidance | **Guidance** | Being first makes "Key" redundant. Shorter heading = less noise. |
| Motivation and background | Why This Matters | **Context** | Broader scope — includes not just "why" but "when" and "where this fits." The summary handles the initial "what is this about?" so this section is purely contextual. |
| Concrete examples | In Practice | **In Practice** | Already good. Clear, concise, unambiguous. |
| Common mistakes | Watch Out For | **Pitfalls** | Shorter. Equally clear. More scannable as a heading. |
| Links and references | Go Deeper | **Go Deeper** | Kept. Communicates progressive disclosure ("there's more depth available") rather than just "here are citations." This is the right name for a system built on layered access. |

---

## Overview Depth

Overview files are area-level orientation. They answer: "What is this domain area,
what topics does it contain, and where do I start?"

### Section Structure

```
---
[frontmatter with summary]
---

# Area Name

## What This Covers

[1–2 paragraphs. What this domain area encompasses, its boundaries, and
why it exists as a grouping.]

## Topics

[Table of topics in this area with links and one-line descriptions.
This is the navigation hub — the entry point for progressive disclosure
into the area's working-depth files.]

| Topic | Description |
|-------|-------------|
| [Topic Name](topic-slug.md) | One-line description |

## Key Sources

[Bullet list of primary sources for the area as a whole. These are
area-level references, not topic-specific ones.]
```

### Changes from Current

| Current | Clean-Slate | Why |
|---------|-------------|-----|
| How It's Organized | **Topics** | More direct. The section contains a topic table — call it what it is. "How It's Organized" describes the meta-structure; "Topics" describes the content. |
| No summary field | **`summary` required** | An agent scanning all overviews needs a sentence-level summary per area, not just a topic table. |

---

## Reference Depth

Reference files are terse, scannable, expert-oriented. They are the *opposite*
of working files — minimal prose, maximum information density.

### Structure Rules

1. Starts with `# Title` (matching the working companion's title)
2. **No required sections.** Content should be whatever format makes the data most
   scannable: tables, bullet lists, decision trees, property lists, cheat sheets.
3. Ends with `**See also:** [Topic Title](companion.md)` linking back to the
   working companion
4. No summary in frontmatter (the file *is* the summary)
5. No Source Evaluation, no provenance block
6. Tables > prose. Lists > paragraphs. Terse > thorough.

### Why No Required Sections

DITA's reference type (`<refbody>`) allows sections/tables/properties in any
sequence — because reference content is shaped by its data, not by a prescribed
narrative flow. A reference for API endpoints looks nothing like a reference for
game theory numbers. Forcing both into the same section template would produce
worse content.

---

## Progressive Disclosure Chain

The complete chain, from cheapest to most expensive:

| Tier | What | Token Cost | Source | When Used |
|------|------|-----------|--------|-----------|
| **1. Manifest line** | Topic name + `relevance` description | ~10–20 tokens | AGENTS.md | Always loaded at session start |
| **2. Summary** | `summary` frontmatter field | ~30–80 tokens | Frontmatter | Agent deciding whether to load a topic |
| **3. Full body** | Complete topic file | ~500–5,000 tokens | Topic `.md` file | Task directly relates to this topic |
| **4. Deep reference** | `.ref.md` companion, primary source URLs, `.dewey/` metadata | Variable | Companion files, external | Agent needs lookup data or provenance details |

**The gap this fills:** Today, an agent goes from ~15 tokens (manifest line) to
~2,000 tokens (full topic) with nothing in between. The summary tier fills that
gap at ~50 tokens per topic — an agent can scan 20 summaries for 1,000 tokens
and decide which 1–2 topics to fully load.

---

## Size Budgets

| Depth | Lines | Token Guidance | Notes |
|-------|-------|---------------|-------|
| overview | 5–150 | ~200–2,000 | Orientation only. Should be loadable alongside other overviews. |
| working | 10–400 | ~500–5,000 | Core content. Fits within Agent Skills Tier 2 (<5K tokens). |
| reference | 3–150 | ~100–2,000 | Dense data. High information-per-token ratio. |
| summary (fm) | 1–3 sentences | ~30–80 | Must standalone. No jargon that requires body context. |

**Enforcement:** Line counts are validated (deterministic, no tokenizer dependency).
Token budgets are guidance for authors and curation review.

---

## Curation Metadata

### Where It Lives

All curation metadata moves to `.dewey/provenance/<domain-area>/<topic-slug>.json`:

```json
{
  "research_date": "2026-02-16",
  "sources_evaluated": 7,
  "sources_included": 5,
  "sources_excluded": 2,
  "exclusion_reasons": ["redundant coverage", "scope mismatch"],
  "counter_evidence_searched": true,
  "counter_evidence_found": [
    "strategy-stealing is non-constructive",
    "edge openings viable"
  ],
  "cross_validation": {
    "total_claims": 6,
    "supported_by_2_plus": 6,
    "consensus": "strong"
  },
  "source_evaluations": [
    {
      "url": "https://en.wikipedia.org/wiki/Tic-tac-toe",
      "title": "Tic-tac-toe — Wikipedia",
      "scores": {
        "authority": 3,
        "accuracy": 5,
        "currency": 4,
        "purpose_fit": 5,
        "corroboration": 5
      },
      "decision": "include"
    }
  ]
}
```

### Why Separate Files

1. **Consumer signal quality.** The Source Evaluation table is ~20 lines of content
   that serves curation, not consumption. Removing it means every remaining line
   in a topic file serves the reader.

2. **Better tooling.** JSON is natively parseable. Health checks, reports, and
   dashboards can read structured provenance data without parsing Markdown tables.

3. **Cleaner separation of concerns.** The topic file is the *product*. The
   provenance file is the *audit trail*. Mixing them is like putting a factory
   inspection report inside the product box.

---

## Complete Example: Working Topic

```markdown
---
summary: "Tic-tac-toe is a solved game where perfect play always draws.
  Forks — creating two simultaneous threats — are the only winning mechanism.
  The Newell & Simon priority list gives an optimal decision procedure."
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
  - url: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
    title: "Tic-Tac-Toe and Variants — Joel David Hamkins"
  - url: https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/
    title: "The Best Strategy For Tic-Tac-Toe — Presh Talwalkar"
  - url: https://brilliant.org/wiki/tic-tac-toe/
    title: "Tic Tac Toe — Brilliant.org"
  - url: https://www.sethcoulson.com/tic-tac-toe/counting/
    title: "Counting (Tic-Tac-Toe) — Seth Coulson"
last_validated: 2026-02-16
relevance: "First-move advantage, forcing draws, forks, and the solved game tree"
depth: working
tags: [game-theory, solved-games, minimax, combinatorial-games]
related:
  - ../checkers/endgame-databases.md
---

# Optimal Strategy

## Guidance

**1. The first player (X) cannot lose with perfect play.** A strategy-stealing
argument proves this: if O had a winning strategy, X could "steal" it by going
first ([Hamkins][hamkins]).

**2. Three strategically distinct first moves exist.** Corner, center, and edge.
Every other first move is equivalent to one of these by rotation or reflection
([Wikipedia][wiki]).

**3. Center is the strongest opening.** It touches 4 winning lines — both
diagonals, middle row, middle column. Corners touch 3; edges touch 2. But X can
force a draw from any first move ([Talwalkar][talwalkar]).

**4. Forks are the only winning mechanism.** Every win against a non-perfect
opponent comes from creating two simultaneous threats. The opponent can only
block one per turn ([Brilliant.org][brilliant]).

**5. The Newell & Simon priority list gives optimal play.** In order: (1) win,
(2) block, (3) fork, (4) block fork, (5) center, (6) opposite corner, (7) any
corner, (8) any edge ([Wikipedia][wiki]).

## Context

Tic-tac-toe is a solved game — with perfect play from both sides, it always
ends in a draw. The complete game tree is small enough that every position has
been exhaustively analyzed: 255,168 possible games, 5,478 reachable board
states, and 765 essentially different positions after symmetry reduction
([Wikipedia][wiki], [Coulson][coulson]).

Being "solved" doesn't mean the strategy is trivial. Under random play, the
first player wins 58% of the time, loses 29%, and draws only 13%
([Coulson][coulson]). Understanding *why* certain moves are optimal builds
intuition that transfers to more complex games.

## In Practice

Consider the opening from X's perspective, starting with a **corner move**:

1. **X plays corner.** Touches 3 winning lines — fewer than center's 4, but
   creates asymmetry O must handle precisely.
2. **O must respond with center.** Any other response allows X to force a win.
3. **X plays the opposite corner.** Threatens along the diagonal, sets up a
   potential fork.
4. **O must block on an edge** to prevent two simultaneous threats.
5. Correct play from both sides leads to a draw.

The critical concept is the **fork** — placing a mark so it creates two winning
threats at once. Since a player can only block one threat per turn, a fork
guarantees a win.

## Pitfalls

**"Solved" does not mean "obvious."** The strategy-stealing argument is a
non-constructive proof — it proves X can't lose without telling you *how* to
play optimally ([Hamkins][hamkins]).

**Edge openings are underestimated.** Most guides dismiss them, but
unfamiliarity increases opponent error rates. They can be effective precisely
because they're unexpected ([Talwalkar][talwalkar]).

**The game's value is pedagogical, not competitive.** Competitive tic-tac-toe
between informed players is pointless. The real value is as a teaching tool
for minimax, game trees, and Nash equilibria.

**Variants restore complexity.** Ultimate Tic-Tac-Toe (a 3×3 grid of 3×3
boards) is *not* solved and has genuine strategic depth
([Hamkins][hamkins]).

## Go Deeper

- [Optimal Strategy Reference](optimal-strategy.ref.md) — quick-lookup companion
- [Tic-tac-toe — Wikipedia][wiki] — comprehensive overview with game enumeration
- [Tic-Tac-Toe and Variants — Hamkins][hamkins] — strategy-stealing proof
- [Best Strategy — Talwalkar][talwalkar] — first-move analysis
- [Tic Tac Toe — Brilliant.org][brilliant] — fork strategy explained

[wiki]: https://en.wikipedia.org/wiki/Tic-tac-toe
[hamkins]: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
[talwalkar]: https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/
[brilliant]: https://brilliant.org/wiki/tic-tac-toe/
[coulson]: https://www.sethcoulson.com/tic-tac-toe/counting/
```

---

## Complete Example: Overview

```markdown
---
summary: "Tic-tac-toe is the simplest nontrivial combinatorial game — fully
  solved, with a complete game tree of 255,168 possible games. It serves as a
  teaching tool for minimax, game trees, and Nash equilibria."
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
last_validated: 2026-02-16
relevance: "core"
depth: overview
---

# Tic-Tac-Toe

## What This Covers

Optimal play, game-theoretic foundations, and strategic analysis of tic-tac-toe
and its variants. Covers the solved 3×3 game and connects to broader
combinatorial game theory concepts.

## Topics

| Topic | Description |
|-------|-------------|
| [Optimal Strategy](optimal-strategy.md) | First-move advantage, forks, and the solved game tree |

## Key Sources

- [Tic-tac-toe — Wikipedia](https://en.wikipedia.org/wiki/Tic-tac-toe) — comprehensive overview
- [Tic-Tac-Toe and Variants — Hamkins](https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants) — strategy-stealing proof
- [Best Strategy — Talwalkar](https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/) — first-move analysis
```

---

## Complete Example: Reference

```markdown
---
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
  - url: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
    title: "Tic-Tac-Toe and Variants — Joel David Hamkins"
last_validated: 2026-02-16
relevance: "First-move advantage, forcing draws, forks, and the solved game tree"
depth: reference
---

# Optimal Strategy

## Game Numbers

| Metric | Value |
|--------|-------|
| Total possible games | 255,168 |
| Games after symmetry reduction | 26,830 |
| Reachable board states | 5,478 |
| Unique positions (after symmetry) | 765 |
| First-player random-play win rate | 58% |

## Winning Lines Per Square

| Square type | Winning lines | Count on board |
|-------------|--------------|----------------|
| Center | 4 | 1 |
| Corner | 3 | 4 |
| Edge | 2 | 4 |

## Newell & Simon Priority List

1. **Win** — complete a line if possible
2. **Block** — prevent opponent's line
3. **Fork** — create two simultaneous threats
4. **Block fork** — prevent opponent's fork
5. **Center** — take if open
6. **Opposite corner** — mirror opponent's corner
7. **Any corner** — take any empty corner
8. **Any edge** — take any empty edge

## Key Results

- Perfect play from both sides always draws
- X cannot lose (strategy-stealing argument)
- Three distinct first moves: center, corner, edge
- Forks are the only winning mechanism

**See also:** [Optimal Strategy](optimal-strategy.md)
```

---

## What Changed From Current (Summary)

| Aspect | Current | Clean-Slate | Research Basis |
|--------|---------|-------------|----------------|
| **First body section** | Why This Matters | **Guidance** | U-shaped attention: primacy position for highest-value content |
| **Summary** | None | **Frontmatter field (required)** | Wikipedia lead, DITA shortdesc, Agent Skills description, Azure RAG enrichment |
| **Source Evaluation** | Inline Markdown table | **`.dewey/provenance/` JSON** | Curation metadata ≠ consumer content; 20 lines of signal dilution |
| **Provenance comment** | HTML comment in body | **`.dewey/provenance/` JSON** | Same as above |
| **Section names** | Key Guidance, Why This Matters, Watch Out For | **Guidance, Context, Pitfalls** | Shorter, equally clear; "Key" redundant when first; "Context" broader than "Why" |
| **Overview nav section** | How It's Organized | **Topics** | Direct label for what the section contains |
| **`relevance` field** | Overloaded (tier or description) | **Always description** | Tier is curation-plan concern; description serves progressive disclosure |
| **Progressive disclosure** | 3 tiers (manifest, body, reference) | **4 tiers (+ summary)** | Fills the 15-token → 2,000-token gap |
| **Inline citations** | Repeated full URLs | **Reference-style links** | Cleaner body text; URLs defined once at bottom |
| **`tags`** | None | **Optional list** | Cross-cutting discovery (Dublin Core, SKOS) |
| **`related`** | None | **Optional list of paths** | Explicit non-hierarchical connections (SKOS related) |

---

## Decisions Still Needed

### D1: Reference-Style Links — Convention or Requirement?

The example above uses Markdown reference-style links (`[text][ref]` with
`[ref]: url` at the bottom) instead of inline links (`[text](url)`). This
produces cleaner body text and avoids URL repetition. But it's a style choice,
not a structural one.

**Recommendation:** Convention, not requirement. Mention in authoring guidance
but don't validate.

### D2: `tags` — When Should We Introduce Them?

Tags are useful but could wait until there's a cross-cutting search feature that
consumes them. Adding fields that nothing reads yet creates maintenance burden
without benefit.

**Recommendation:** Include in the spec now. Implement validation and consumption
later. Authors who want them can use them; authors who don't can omit them.

### D3: `related` — Same Question

The `related` field enables "related topics" suggestions, but nothing currently
consumes it.

**Recommendation:** Same as tags — include in spec, defer consumption. The health
system could validate that related paths actually exist.

### D4: How Should the Provenance Migration Work?

When we rewrite existing topics to v2, the Source Evaluation table and provenance
comment need to be extracted into `.dewey/provenance/` JSON files. This could be:

- **Manual:** Author moves data during content review
- **Scripted:** A migration script parses the Markdown table and HTML comment
- **Gradual:** New topics use v2 format; old topics migrate during next validation cycle

**Recommendation:** Scripted migration for the sandbox content, gradual for any
user-created knowledge bases.
