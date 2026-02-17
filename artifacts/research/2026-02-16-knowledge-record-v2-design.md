# Design Document: Knowledge Record Specification v2

> Status: Draft
> Date: 2026-02-16
> Branch: research/agent-context-effectiveness

## Problem

Dewey produces curated knowledge bases that agents consume as structured context.
The current format works but has gaps identified through deep research:

1. **No summary field** — agents jump from a 15-token manifest line to a 2,000-token
   full file with nothing in between
2. **Section ordering ignores the attention curve** — Key Guidance sits in the middle
   (lowest attention position), not at the top (highest)
3. **Source Evaluation is consumer-facing noise** — ~20 lines of curation metadata
   dilute the signal for the actual consumer
4. **Custom directory structure** — AGENTS.md, docs/, .claude/rules/dewey-kb.md are
   Dewey-specific; the Agent Skills ecosystem already has a cross-platform structure
5. **Companion files create sync overhead** — .ref.md files must stay in sync with
   their working counterparts; we built cross-validators just for this
6. **Provider-specific discovery** — .claude/rules/ only works in Claude Code

## Research Basis

This design is informed by three research artifacts on this branch:

- `artifacts/research/2026-02-16-agent-context-effectiveness-deep-dive.md` — 30+
  papers on context utilization, attention patterns, and progressive disclosure
- `artifacts/research/2026-02-16-knowledge-record-design-research.md` — 16
  documentation standards surveyed (Diataxis, DITA, EPPO, SKOS, etc.)
- `artifacts/research/2026-02-16-context-quality-open-source.md` — 96 open-source
  tools surveyed; no existing tool solves this problem

Key findings that drive every design choice:

| Finding | Source | Impact |
|---------|--------|--------|
| U-shaped attention curve — beginning/end get most attention | Liu et al. "Lost in the Middle", 6 follow-up studies | Section ordering |
| 300 focused tokens beat 113K unfocused tokens | Anthropic context engineering | Token budget discipline |
| Context rot: 13.9–85% degradation as length increases | Chroma Research, 18 models | Every line must earn its place |
| Progressive disclosure cuts tokens up to 98% | Agent Skills pattern | 3-tier skill structure |
| Structured formatting improves output 10–40% | Multiple benchmarks | Predictable section structure |
| Format doesn't matter for frontier models (p=0.484) | McMillan, arXiv:2602.05447 | Markdown + YAML confirmed |
| Agent Skills adopted by all major platforms | Ecosystem survey | Use skills as the container |
| No tool addresses content quality + maintenance | 96-tool landscape survey | Build, don't buy |

## Design

### Architecture: Knowledge Base as a Skill

The knowledge base IS a skill. It uses the Agent Skills specification as its
container, inheriting cross-platform discovery and progressive disclosure for free.

```
<knowledge-skill>/
├── SKILL.md                        # Role persona + topic manifest
├── references/
│   ├── <domain-area>/
│   │   ├── overview.md             # Area orientation
│   │   └── <topic>.md              # Working knowledge (with optional Quick Reference)
│   └── _proposals/                 # Staged additions pending validation
└── .dewey/
    ├── health/                     # Quality scores per entry
    ├── history/                    # Change log, baselines
    ├── provenance/                 # Source evaluations, research metadata
    │   └── <domain-area>/
    │       └── <topic>.json
    ├── utilization/                # Reference tracking
    └── curation-plan.md            # What knowledge should exist
```

### What's Eliminated

| Removed | Replaced By |
|---------|------------|
| `AGENTS.md` | `SKILL.md` (role persona + manifest) |
| `docs/` directory | `references/` (standard skill directory) |
| `docs/index.md` | Manifest table in SKILL.md body |
| `.claude/rules/dewey-kb.md` | SKILL.md (skill IS the discovery mechanism) |
| Managed-section markers (`dewey:knowledge-base:begin/end`) | SKILL.md is entirely Dewey-owned |
| `.ref.md` companion files | Quick Reference section within working topics |
| `depth: reference` | Only two depths remain: `overview` and `working` |

### Progressive Disclosure Through Skill Tiers

| Tier | Content | Token Cost | When Loaded |
|------|---------|-----------|-------------|
| **1. Skill description** | Skill name + description from SKILL.md frontmatter | ~50–80 tokens | Always (session start) |
| **2. Manifest + summaries** | Full SKILL.md body: persona, topic table with summaries, usage guide | ~500–2,000 tokens | Skill activation |
| **3. Topic files** | Individual files from references/ | ~500–3,000 per file | On demand per topic |

The `summary` field in each topic's frontmatter is surfaced in the SKILL.md
manifest table. An agent reading Tier 2 sees every topic's summary without
loading any files — filling the gap between the 80-token skill description and
the 2,000-token full file.

---

## SKILL.md Specification

### Frontmatter

```yaml
---
name: <skill-name>
description: >
  2–4 sentence description of the knowledge domain. Must standalone —
  this is the only content loaded at Tier 1 across all sessions.
---
```

### Body Structure

```markdown
## Who You Are

[Role persona: tone, expertise level, behavioral expectations. 2–4 sentences.]

## What You Have Access To

### <Domain Area>

| Topic | Summary |
|-------|---------|
| [Topic Name](references/<area>/<topic>.md) | [summary from frontmatter] |

[Repeat per domain area]

## How To Use This Knowledge

- Load topic files from `references/` when the task relates to a domain area
- Read the Summary column before loading full files — it may be enough
- Cite primary sources from the `sources` frontmatter when making recommendations
- Defer to primary sources for detailed reference
- Check `.dewey/curation-plan.md` for planned topics and curation priorities
- When a conversation touches uncovered knowledge areas, suggest adding them
```

### Size Constraint

SKILL.md body must stay under 5,000 tokens (Agent Skills Tier 2 limit). With
~50 tokens per manifest row, this supports ~60 topics before the manifest itself
needs pagination or hierarchy.

---

## Topic File Specification: Working Depth

Working-depth files carry the actionable knowledge. This is the primary content
type.

### Frontmatter

```yaml
---
summary: "1–3 sentence standalone description. Must make sense without
  reading the body. Surfaced in SKILL.md manifest table."
sources:
  - url: https://example.com/primary-source
    title: "Source Title"
last_validated: 2026-02-16
relevance: "Who this helps and when — one line of information scent"
depth: working
tags: [optional, cross-cutting, keywords]
related:
  - ../other-area/related-topic.md
---
```

| Field | Required | Purpose |
|-------|----------|---------|
| `summary` | Yes | Standalone description for Tier 2 progressive disclosure |
| `sources` | Yes | Primary source URLs — enforces source primacy |
| `last_validated` | Yes | Freshness signal for health checks |
| `relevance` | Yes | Information scent — always a description, never a tier |
| `depth` | Yes | `overview` or `working` |
| `tags` | No | Cross-cutting keywords for discovery |
| `related` | No | Explicit non-hierarchical connections (SKOS `related`) |

### Section Structure (Attention-Optimized)

```
# Topic Title

## Guidance              ← primacy position: highest-value, highest-attention
## Context               ← motivation, background, "why"
## In Practice           ← concrete examples (engaging — resists attention valley)
## Pitfalls              ← warnings (recency effect — sticks)
## Quick Reference       ← OPTIONAL: terse lookup data (tables, lists, cheat sheets)
## Go Deeper             ← links to primary sources and further reading
```

```
Attention
  ▲
  │  ██                                                    ██
  │  ██ ██                                              ██ ██
  │  ██ ██ ██                                        ██ ██ ██
  │  ██ ██ ██ ██                                  ██ ██ ██ ██
  │  ██ ██ ██ ██ ██ ██                      ██ ██ ██ ██ ██ ██
  │  ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██
  └────────────────────────────────────────────────────────────→
     Guidance  Context  In Practice   Pitfalls  Quick Ref  Go Deeper
```

| Section | Purpose | Content Guidance |
|---------|---------|-----------------|
| **Guidance** | Actionable recommendations. The section an agent reads if it can only read one. | Numbered items. Bold principle statement + explanation + source citation. |
| **Context** | Why this matters. When it applies. How it connects. | 1–3 paragraphs. Causal reasoning (Principle #10). |
| **In Practice** | Concrete examples and worked scenarios. | Concrete-first (Principle #11). Walkthroughs, code blocks, decision tables. |
| **Pitfalls** | Mistakes, anti-patterns, misconceptions. | Bold heading per pitfall. Brief explanation. Counter-evidence. |
| **Quick Reference** | Optional. Terse lookup data. | Tables, bullet lists, decision trees. No prose. Only when topic has significant lookup data. |
| **Go Deeper** | Primary sources and further reading. | Bullet list. Primary sources first, then further reading. |

### Size Budget

| Metric | Bound | Enforcement |
|--------|-------|-------------|
| Lines | 10–500 | Validator (deterministic) |
| Tokens (guidance) | ~500–5,000 | Author guidance only |
| Summary | 1–3 sentences | Validator |

---

## Topic File Specification: Overview Depth

Overview files are area-level orientation. One per domain area.

### Frontmatter

```yaml
---
summary: "1–3 sentence standalone description of this domain area."
sources:
  - url: https://example.com/area-level-source
    title: "Source Title"
last_validated: 2026-02-16
relevance: "core"
depth: overview
---
```

### Section Structure

```
# Area Name

## What This Covers       ← 1–2 paragraphs: scope and boundaries
## Topics                 ← table of topics with descriptions
## Key Sources            ← area-level primary sources
```

### Size Budget

| Metric | Bound |
|--------|-------|
| Lines | 5–150 |
| Tokens (guidance) | ~200–2,000 |
| Summary | 1–3 sentences |

---

## Curation Metadata

Source evaluation and research provenance move out of topic files into
`.dewey/provenance/<domain-area>/<topic-slug>.json`:

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
      "url": "https://example.com/source",
      "title": "Source Title",
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

**Why separate:** The Source Evaluation table is ~20 lines that serve curation,
not consumption. Removing it means every remaining line in a topic file serves
the reader. JSON is natively parseable by health tooling.

---

## Health Validator Changes

### Removed Validators

| Validator | Reason |
|-----------|--------|
| Companion file sync check | No more .ref.md files |
| `depth: reference` validation | Only two depths remain |
| Source Evaluation section check | Moved to .dewey/provenance/ |
| AGENTS.md manifest sync | Replaced by SKILL.md manifest sync |

### Modified Validators

| Validator | Change |
|-----------|--------|
| `_VALID_DEPTHS` | Remove `reference`, keep `overview` and `working` |
| `_SIZE_BOUNDS` | Remove `reference` entry; adjust `working` upper bound (400 → 500) |
| `_WORKING_SECTIONS` | New list: `["Guidance", "Context", "In Practice", "Pitfalls", "Go Deeper"]` |
| `_OVERVIEW_SECTIONS` | New list: `["What This Covers", "Topics"]` |
| `check_frontmatter_fields` | Add `summary` as required for working/overview |
| `check_section_ordering` | Enforce new order (Guidance first) |
| Manifest sync | Check SKILL.md manifest table matches references/ directory |
| Path references | `docs/` → `references/` throughout |

### New Validators

| Validator | What It Checks |
|-----------|---------------|
| `check_summary_quality` | Summary is 1–3 sentences, doesn't start with the topic name, is standalone |
| `check_provenance_exists` | Working topics have a corresponding .dewey/provenance/ JSON file |
| `check_tags_format` | Tags are lowercase, hyphenated, no duplicates within a file |
| `check_related_paths` | Paths in `related` field resolve to existing files |
| `check_skill_md` | SKILL.md body stays under 5K tokens; manifest matches references/ |

### Tier 2 Trigger Changes

| Trigger | Change |
|---------|--------|
| Summary quality trigger | Flag summaries that are weak, generic, or just repeat the title |
| Quick Reference trigger | Flag working topics with significant tabular data but no Quick Reference section |

---

## Migration

### Sandbox (Scripted)

A migration script transforms the existing sandbox:

1. Create `SKILL.md` from AGENTS.md content + summary fields
2. Move `docs/` → `references/`
3. Merge `.ref.md` content into parent topic as `## Quick Reference` section
4. Delete `.ref.md` files
5. Add `summary` field to all topic frontmatter
6. Reorder sections in working topics (Guidance first)
7. Rename sections (Key Guidance → Guidance, Why This Matters → Context, Watch Out For → Pitfalls)
8. Extract Source Evaluation tables → `.dewey/provenance/` JSON
9. Remove Source Evaluation sections and provenance HTML comments from topic files
10. Delete `AGENTS.md`, `docs/index.md`, `.claude/rules/dewey-kb.md`
11. Update `_proposals/` path if any exist

### Scaffolding (templates.py)

All `render_*` functions updated:

| Function | Change |
|----------|--------|
| `render_agents_md` | **Remove** — replaced by `render_skill_md` |
| `render_agents_md_section` | **Remove** |
| `render_index_md` | **Remove** — SKILL.md manifest replaces index |
| `render_claude_md` | **Remove** — skill discovery replaces .claude/rules |
| `render_claude_md_section` | **Remove** |
| `render_dewey_rules` | **Remove** |
| `render_dewey_rules_section` | **Remove** |
| `render_topic_ref_md` | **Remove** — no more .ref.md files |
| `render_skill_md` | **New** — generates SKILL.md with frontmatter, persona, manifest |
| `render_topic_md` | **Update** — new section order, new names, summary placeholder, no Source Evaluation |
| `render_overview_md` | **Update** — add summary placeholder, rename "How It's Organized" → "Topics" |
| `render_proposal_md` | **Update** — new section order, new names |
| `render_curation_plan_md` | **No change** |

### Cross-Validator Updates

| Validator | Change |
|-----------|--------|
| `check_manifest_sync` | Parse SKILL.md manifest table instead of AGENTS.md |
| `check_companion_files` | **Remove** — no more companions |
| `check_link_graph` | Update paths: docs/ → references/ |
| `check_duplicate_content` | No companion pair exclusion needed |

---

## Complete Example: Working Topic (v2)

```markdown
---
summary: "Tic-tac-toe is a solved game where perfect play always draws.
  Forks — creating two simultaneous threats — are the only winning
  mechanism. The Newell & Simon priority list gives optimal play."
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
---

# Optimal Strategy

## Guidance

**1. The first player (X) cannot lose with perfect play.** A strategy-stealing
argument proves this: if O had a winning strategy, X could "steal" it by going
first ([Hamkins][hamkins]).

**2. Three strategically distinct first moves exist.** Corner, center, and edge.
Every other first move is equivalent by rotation or reflection
([Wikipedia][wiki]).

**3. Center is the strongest opening.** It touches 4 winning lines — both
diagonals, middle row, middle column. Corners touch 3; edges touch 2. But X can
force a draw from any first move ([Talwalkar][talwalkar]).

**4. Forks are the only winning mechanism.** Every win against a non-perfect
opponent comes from creating two simultaneous threats
([Brilliant.org][brilliant]).

**5. The Newell & Simon priority list gives optimal play.** In order: (1) win,
(2) block, (3) fork, (4) block fork, (5) center, (6) opposite corner, (7) any
corner, (8) any edge ([Wikipedia][wiki]).

## Context

Tic-tac-toe is a solved game — with perfect play from both sides, it always
ends in a draw. The complete game tree is small enough that every position has
been exhaustively analyzed: 255,168 possible games, 5,478 reachable board
states, and 765 essentially different positions after symmetry reduction
([Wikipedia][wiki], [Coulson][coulson]).

Understanding *why* certain moves are optimal builds intuition that transfers
to more complex games.

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
threats at once.

## Pitfalls

**"Solved" does not mean "obvious."** The strategy-stealing argument is a
non-constructive proof — it proves X can't lose without telling you how to play
optimally ([Hamkins][hamkins]).

**Edge openings are underestimated.** Most guides dismiss them, but
unfamiliarity increases opponent error rates
([Talwalkar][talwalkar]).

**The game's value is pedagogical, not competitive.** Competitive tic-tac-toe
between informed players is pointless. The real value is as a teaching tool for
minimax, game trees, and Nash equilibria.

## Quick Reference

| Metric | Value |
|--------|-------|
| Total possible games | 255,168 |
| Reachable board states | 5,478 |
| Unique positions (after symmetry) | 765 |
| First-player random-play win rate | 58% |

**Newell & Simon Priority List:** Win → Block → Fork → Block fork → Center →
Opposite corner → Any corner → Any edge

**Winning lines per square:** Center: 4, Corner: 3, Edge: 2

## Go Deeper

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

## Complete Example: SKILL.md

```yaml
---
name: board-game-strategy
description: >
  Domain expertise in classic board game strategy — optimal play, game theory,
  and strategic analysis for chess, checkers, and tic-tac-toe. Covers openings,
  endgames, solved games, and the mathematical foundations behind them.
---
```

```markdown
## Who You Are

A board game strategy expert who explains not just what to do, but why it works.
Ground recommendations in primary sources and game-theoretic principles. When
advising on strategy, cite the sources from topic frontmatter.

## What You Have Access To

### Chess

| Topic | Summary |
|-------|---------|
| [Overview](references/chess/overview.md) | Chess domain orientation — what's covered, key sources, topic map |
| [Opening Principles](references/chess/opening-principles.md) | The first 10-15 moves follow three principles: control the center, develop pieces, castle early. Deviations are punished by concrete tactical refutations, not abstract rules. |

### Checkers

| Topic | Summary |
|-------|---------|
| [Overview](references/checkers/overview.md) | Checkers domain orientation — what's covered, key sources, topic map |

### Tic-Tac-Toe

| Topic | Summary |
|-------|---------|
| [Overview](references/tic-tac-toe/overview.md) | Tic-tac-toe is the simplest nontrivial combinatorial game — fully solved, with 255,168 possible games. Teaching tool for minimax and Nash equilibria. |
| [Optimal Strategy](references/tic-tac-toe/optimal-strategy.md) | Tic-tac-toe is a solved game where perfect play always draws. Forks — creating two simultaneous threats — are the only winning mechanism. The Newell & Simon priority list gives optimal play. |

## How To Use This Knowledge

- Load topic files from `references/` when the task relates to a domain area
- Read the Summary column before loading full files — it may be enough
- Cite primary sources from the `sources` frontmatter when making recommendations
- Defer to primary sources for detailed reference
- Check `.dewey/curation-plan.md` for planned topics and curation priorities
- When a conversation touches uncovered knowledge areas, suggest adding them
```

---

## Design Principles Alignment

| Principle | How v2 Serves It |
|-----------|-----------------|
| #1 Source Primacy | `sources` frontmatter retained; Go Deeper links to primary sources |
| #2 Dual Audience | Skill structure serves agents (tiers); markdown serves humans (readable) |
| #3 Three-Dimensional Quality | Health validators check relevance, accuracy/freshness, structural fitness |
| #5 Provenance | `last_validated`, `sources`, `.dewey/provenance/` JSON |
| #6 Domain-Shaped Organization | `references/<domain-area>/` structure |
| #9 Progressive Disclosure | 3-tier skill structure with summary field bridging Tier 1→3 |
| #10 Explain the Why | Context section (renamed from "Why This Matters") |
| #11 Concrete Before Abstract | In Practice section positioned before Pitfalls |
| #12 Multiple Representations | Summary → full body → Quick Reference within one file |
| **New: Position-Aware** | Guidance first (primacy), Pitfalls near end (recency) |

---

## Research Artifacts

| File | Contents |
|------|----------|
| `2026-02-16-agent-context-effectiveness-deep-dive.md` | 6 research questions, 30+ papers, design alignment matrix |
| `2026-02-16-knowledge-record-design-research.md` | 16 documentation standards, 8 identified gaps |
| `2026-02-16-documentation-standards-raw.md` | Raw Diataxis, DITA, EPPO, Information Mapping details |
| `2026-02-16-context-quality-open-source.md` | 96 tools surveyed across 5 layers |
| `2026-02-16-knowledge-record-spec-v2-draft.md` | Initial spec with 9 trade-off analyses |
| `2026-02-16-knowledge-record-spec-v2-recommendation.md` | Clean-slate recommendation with examples |
