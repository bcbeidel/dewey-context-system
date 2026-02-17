# Knowledge Record Specification v2 — Draft

> First draft based on deep research into agent context effectiveness, documentation
> standards (Diataxis, DITA, EPPO, Information Mapping), agentic knowledge systems
> (Agent Skills, MCP, Cursor, Claude Code), and first-principles analysis.

---

## Design Rationale

Three research findings drive every change in this spec:

1. **Position matters.** LLMs exhibit a U-shaped attention curve — the beginning and end of context receive the most attention, the middle receives the least (Liu et al. "Lost in the Middle"; confirmed by 6+ follow-up studies). The most actionable content must be at the top.

2. **Less focused context beats more unfocused context.** 300 focused tokens outperform 113K unfocused tokens (Anthropic). Context rot degrades performance 13.9–85% as length increases (Chroma Research). Every line in a topic file must earn its place.

3. **Progressive disclosure is the strongest lever.** Cutting from full-context to metadata-only reduces tokens up to 98% (Agent Skills pattern). The spec must support agents that scan metadata, read summaries, then optionally load full content.

---

## Frontmatter Schema

### Current Fields (Retained)

| Field | Type | Required | Purpose |
|-------|------|----------|---------|
| `sources` | list of `{url, title}` | Yes | Primary source URLs — enforces source primacy (Principle #1) |
| `last_validated` | ISO date | Yes | Freshness signal for health checks (Principle #5) |
| `depth` | `overview` \| `working` \| `reference` | Yes | Position in the progressive disclosure chain (Principle #9) |

### Changed Fields

| Field | Change | Rationale |
|-------|--------|-----------|
| `relevance` | **Redefine: from free-text to structured** | Currently overloaded — sometimes a relevance tier (`core`), sometimes a description. Split into two clear purposes. |

**`relevance`** becomes a one-line description of **who this helps and when** (information scent for agents scanning the manifest). This is what it already does in the best examples — e.g., `"First-move advantage, forcing draws, forks, and the solved game tree"`.

### New Fields

| Field | Type | Required | Purpose |
|-------|------|----------|---------|
| `summary` | string (1–3 sentences) | **Yes** for `working` and `overview`; No for `reference` | Standalone description that can be consumed without loading the body. Maps to Wikipedia lead section, DITA `<shortdesc>`, Agent Skills `description` field, Azure RAG enrichment. This is the **single highest-value addition** — it enables a 4-tier progressive disclosure chain: manifest line → summary → full body → deep references. |
| `tags` | list of strings | No | Keywords for retrieval enrichment and cross-cutting discovery. Maps to Dublin Core `Subject`, DITA `<keyword>`, SKOS `altLabel`. |
| `related` | list of relative paths | No | Explicit non-hierarchical connections to other topics. Maps to SKOS `related`, DITA relationship tables. Distinct from hierarchical parent–child (which is implicit in directory structure). |

### Full Frontmatter Example (Working Depth)

```yaml
---
summary: "Tic-tac-toe is a solved game where perfect play always draws. Forks — creating two simultaneous threats — are the only winning mechanism. The Newell & Simon priority list gives an optimal decision procedure."
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
  - url: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
    title: "Tic-Tac-Toe and Variants — Joel David Hamkins"
last_validated: 2026-02-16
relevance: "First-move advantage, forcing draws, forks, and the solved game tree"
depth: working
tags: [game-theory, solved-games, minimax, combinatorial-games]
related:
  - ../checkers/endgame-databases.md
---
```

### Full Frontmatter Example (Overview Depth)

```yaml
---
summary: "Tic-tac-toe is the simplest nontrivial combinatorial game — fully solved, with a complete game tree of 255,168 possible games. It serves as a teaching tool for minimax, game trees, and Nash equilibria."
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
last_validated: 2026-02-16
relevance: "core"
depth: overview
---
```

### Full Frontmatter Example (Reference Depth)

```yaml
---
sources:
  - url: https://en.wikipedia.org/wiki/Tic-tac-toe
    title: "Tic-tac-toe — Wikipedia"
last_validated: 2026-02-16
relevance: "First-move advantage, forcing draws, forks, and the solved game tree"
depth: reference
---
```

---

## Section Structure: Working Depth

Working-depth files are the core content. They carry the most actionable guidance and are the most sensitive to attention-curve effects.

### Current Section Order

```
1. # Title
2. ## Why This Matters
3. ## In Practice
4. ## Key Guidance        ← PROBLEM: sitting in attention dead zone
5. ## Watch Out For
6. ## Go Deeper
7. ## Source Evaluation   ← PROBLEM: curation noise for consumer
```

### Proposed Section Order

```
1. # Title
2. ## Key Guidance        ← MOVED TO TOP: highest-value, highest-attention position
3. ## Why This Matters
4. ## In Practice         ← middle position: narrative/example content (tolerates lower attention)
5. ## Watch Out For       ← MOVED TOWARD END: recency effect picks up warnings
6. ## Go Deeper           ← last body section: links/references
```

**What changed:**
- **Key Guidance → position 1** (after title). Research: primacy effect means the first section gets disproportionate attention. Key Guidance is the most actionable section — it should be first.
- **Source Evaluation → removed from body**. Moved to `.dewey/provenance/`. It serves curation (evaluating sources), not consumption (using the knowledge). ~20 lines of curation metadata dilutes the consumer content.
- **Provenance HTML comment → removed from body**. Same reasoning. Moved to `.dewey/provenance/`.

### Proposed Section Definitions

| Section | Purpose | Content Guidance |
|---------|---------|-----------------|
| **Key Guidance** | Actionable recommendations and best practices. The section an agent reads if it can only read one. | Numbered items. Each starts bold with a principle statement, followed by explanation and source citation. |
| **Why This Matters** | Context and motivation. Establishes why this topic exists in the knowledge base. | 1–3 paragraphs. Explains the "why" (Principle #10). Connects to the broader domain. |
| **In Practice** | Concrete examples and worked scenarios. | Concrete-first (Principle #11). Walks through a real scenario. Code blocks, step sequences, or case studies. |
| **Watch Out For** | Pitfalls, anti-patterns, misconceptions. | Bold heading per pitfall. Brief explanation. Counter-evidence from research. |
| **Go Deeper** | Links to companion files, primary sources, and further reading. | Bullet list. Reference companion first, then primary sources, then further reading. |

---

## Section Structure: Overview Depth

Overview files are area-level orientation. They answer "what is this domain area and what topics does it contain?"

### Current Section Order (Retained with Addition)

```
1. # Area Name
2. ## What This Covers
3. ## How It's Organized    ← topic table
4. ## Key Sources
```

### Proposed Change

Add an optional **## Why It Matters** section between "What This Covers" and "How It's Organized" for overviews that need to establish context beyond a one-liner.

```
1. # Area Name
2. ## What This Covers
3. ## Why It Matters        ← OPTIONAL: for areas needing context justification
4. ## How It's Organized    ← topic table
5. ## Key Sources
```

---

## Section Structure: Reference Depth

Reference files are terse, scannable lookup companions. They have **no required section structure** — content should be whatever format makes the information most scannable (tables, bullet lists, decision trees).

### Only Requirements

1. Must start with `# Title` (matching the working companion)
2. Must end with `**See also:** [Title](companion.md)` linking to the working companion
3. No prose paragraphs — tables, lists, and terse bullet points only
4. No Source Evaluation section

---

## Size Budgets

Research shows token budgets are more meaningful than line counts for agent consumption, but line counts remain useful for human authoring. The spec provides both.

### Current Bounds (Line Counts)

| Depth | Min | Max |
|-------|-----|-----|
| overview | 5 | 150 |
| working | 10 | 400 |
| reference | 3 | 150 |

### Proposed Bounds

| Depth | Lines (min–max) | Token Budget (guidance) | Rationale |
|-------|----------------|------------------------|-----------|
| overview | 5–150 | ~200–2,000 tokens | Orientation only. Agent reads to decide whether to load working topics. |
| working | 10–400 | ~500–5,000 tokens | Core content. Fits within Agent Skills Tier 2 budget (<5K tokens). |
| reference | 3–150 | ~100–2,000 tokens | Lookup companion. Dense tables/lists are high-information-per-token. |

**Validator enforcement:** Line counts remain the enforced metric (deterministic, no tokenizer dependency). Token budgets are guidance for authors and curation review.

---

## Progressive Disclosure Chain

The spec defines a 4-tier progressive disclosure chain. Each tier can be consumed independently.

| Tier | Content | Token Cost | When Loaded |
|------|---------|-----------|-------------|
| **1. Manifest** | Topic name + `relevance` one-liner (from AGENTS.md) | ~10–20 tokens/topic | Always (startup) |
| **2. Summary** | `summary` frontmatter field (1–3 sentences) | ~30–80 tokens/topic | When agent needs to decide whether to read the full topic |
| **3. Full Body** | Complete topic file | ~500–5,000 tokens | When task relates to this topic |
| **4. Deep Reference** | `.ref.md` companions, primary source URLs, `.dewey/` metadata | Unbounded | When agent needs lookup data or provenance |

**New capability (from `summary` field):** An agent can now load all summaries for a domain area (~500 tokens for 10 topics) to decide which topics to fully load. Previously, the only options were manifest lines (~10 tokens, too sparse) or full files (~5K tokens, too expensive).

---

## Curation Metadata Separation

### Current State

Source evaluation tables and provenance comments live inside topic files:

```markdown
## Source Evaluation
| Source | Authority | Accuracy | Currency | Purpose | Corroboration | Decision |
...

<!-- dewey:provenance {"research_date":"2026-02-16",...} -->
```

### Proposed State

Move curation metadata to `.dewey/provenance/<topic-slug>.json`:

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
      "authority": 3,
      "accuracy": 5,
      "currency": 4,
      "purpose": 5,
      "corroboration": 5,
      "decision": "include"
    }
  ]
}
```

**Why:** Source evaluation serves the curation process, not the consumer. Including it in the topic file adds ~20 lines of content that dilutes the signal for agents. JSON format is better suited for tooling (health checks, reports) than a Markdown table.

---

## Example: Working Topic (v2 Format)

```markdown
---
summary: "Tic-tac-toe is a solved game where perfect play always draws. Forks — creating two simultaneous threats — are the only winning mechanism. The Newell & Simon priority list gives an optimal decision procedure."
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
tags: [game-theory, solved-games, minimax]
related:
  - ../checkers/endgame-databases.md
---

# Optimal Strategy

## Key Guidance

**1. The first player (X) cannot lose with perfect play.** A strategy-stealing
argument proves this: if O had a winning strategy, X could "steal" it by going
first ([Hamkins](https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants)).

**2. Three strategically distinct first moves exist.** Corner, center, and edge.
Every other first move is equivalent to one of these by symmetry
([Wikipedia](https://en.wikipedia.org/wiki/Tic-tac-toe)).

**3. Center is the strongest opening.** It touches 4 winning lines (both
diagonals, middle row, middle column). Corners touch 3; edges touch 2. But X
can force a draw from any first move
([Talwalkar](https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/)).

**4. Forks are the only winning mechanism.** Every win against a non-perfect
opponent comes from creating two simultaneous threats
([Brilliant.org](https://brilliant.org/wiki/tic-tac-toe/)).

**5. The Newell & Simon priority list gives optimal play.** In order: (1) win,
(2) block, (3) fork, (4) block fork, (5) center, (6) opposite corner, (7) any
corner, (8) any edge ([Wikipedia](https://en.wikipedia.org/wiki/Tic-tac-toe)).

## Why This Matters

Tic-tac-toe is a solved game — with perfect play from both sides, it always ends
in a draw. The complete game tree is small enough that every position has been
exhaustively analyzed: 255,168 possible games, 5,478 reachable board states, and
765 essentially different positions after symmetry reduction.

Understanding *why* certain moves are optimal builds intuition that transfers to
more complex games.

## In Practice

Consider the opening from X's perspective, starting with a **corner move**:

1. **X plays corner.** Touches 3 winning lines — fewer than center's 4, but
   creates asymmetry O must handle precisely.
2. **O must respond with center.** Any other response allows X to force a win.
3. **X plays the opposite corner.** Threatens along the diagonal, sets up a fork.
4. **O must block on an edge** to prevent two simultaneous threats.
5. Correct play from both sides leads to a draw.

## Watch Out For

**"Solved" does not mean "obvious."** The strategy-stealing argument is
non-constructive — it proves X can't lose without showing how to play
([Hamkins](https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants)).

**Edge openings are underestimated.** Most guides dismiss them, but unfamiliarity
increases opponent error rates
([Talwalkar](https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/)).

**The game's value is pedagogical.** Competitive tic-tac-toe between informed
players is pointless. The real value is as a teaching tool for minimax, game
trees, and Nash equilibria.

## Go Deeper

- [Optimal Strategy Reference](optimal-strategy.ref.md) — quick-lookup companion
- [Tic-tac-toe — Wikipedia](https://en.wikipedia.org/wiki/Tic-tac-toe) — comprehensive overview
- [Tic-Tac-Toe and Variants — Hamkins](https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants) — strategy-stealing proof
- [Best Strategy — Talwalkar](https://mindyourdecisions.com/blog/2015/06/02/the-best-strategy-for-tic-tac-toe-game-theory-tuesdays/) — first-move analysis
- [Tic Tac Toe — Brilliant.org](https://brilliant.org/wiki/tic-tac-toe/) — fork strategy
```

---

## Migration Impact

### What Changes in the Codebase

| Component | Change | Effort |
|-----------|--------|--------|
| `validators.py` — `_WORKING_SECTIONS` | Reorder list: Key Guidance first | Small |
| `validators.py` — `check_section_ordering` | Validate new order | Small |
| `validators.py` — `check_frontmatter_fields` | Add `summary` as required for working/overview | Small |
| `validators.py` — new `check_summary_length` | Validate summary is 1–3 sentences | Small |
| `validators.py` — Source Evaluation check | Remove requirement; warn if still present | Small |
| `templates.py` — `render_topic_md` | Reorder sections, add `summary` placeholder, drop Source Evaluation | Small |
| `templates.py` — `render_overview_md` | Add `summary` placeholder | Small |
| `templates.py` — `_frontmatter()` | Handle `summary` field (quoted string) | Small |
| `cross_validators.py` | Validate `tags` uniqueness, `related` path existence | Medium |
| `tier2_triggers.py` | Add trigger for empty/weak summaries | Small |
| Curation workflows | Write provenance to `.dewey/provenance/` instead of inline | Medium |
| Existing sandbox topics | Migrate: reorder sections, add summaries, move Source Evaluation | Medium |
| `auto_fix.py` | Add migration helper for section reordering | Medium |
| Health report | Include summary quality metrics | Small |

### What Doesn't Change

- Directory structure (AGENTS.md, docs/, .dewey/)
- Three depths (overview, working, reference)
- AGENTS.md manifest format
- Line-count bounds (retained alongside token guidance)
- `.ref.md` companion pattern
- `_proposals/` staging workflow
- Curation plan format

---

## Trade-offs Requiring Your Input

### T1: `summary` Field — Required or Optional?

**Option A: Required for working and overview depths (recommended).** Every topic file must have a summary. This enables the Tier 2 progressive disclosure step (load summaries to decide what to fully load). Empty summaries defeat the purpose.

**Option B: Optional for all depths.** Less friction for initial authoring. But progressive disclosure falls back to manifest-only, losing the middle tier.

**Option C: Required for all three depths including reference.** Maximum consistency, but reference files are already terse — their entire body *is* the summary.

*Current lean: Option A. Reference files don't need summaries because they're already scannable.*

---

### T2: Section Reordering — How Aggressive?

**Option A: Move Key Guidance to first position (recommended).** The research evidence is strong (primacy effect). This is the single highest-impact structural change.

**Option B: Keep current order, add guidance to put the most important content first *within* each section.** Less disruptive but doesn't fix the structural attention problem.

**Option C: Make section order flexible (no enforced order, just required sections).** Maximum author freedom, but sacrifices predictable structure that agents can parse reliably (DITA's key insight).

*Current lean: Option A. The attention curve research is unambiguous.*

---

### T3: Source Evaluation — Where Does It Live?

**Option A: Move to `.dewey/provenance/<slug>.json` (recommended).** Cleanest separation. Curation metadata doesn't dilute consumer content. JSON is better for tooling. Health checks can still read it.

**Option B: Keep inline but make optional.** Simpler (no new file pattern), but the ~20 lines of evaluation table remain in the body, consuming attention budget.

**Option C: Move to a `<!-- dewey:source-eval ... -->` HTML comment at the end of the file.** Hidden from rendering but still in the same file. Compromise between separation and simplicity.

*Current lean: Option A. The provenance comment is already JSON — making it a separate file is natural.*

---

### T4: `tags` Field — Worth the Complexity?

**Option A: Add optional `tags` field (recommended).** Enables cross-cutting discovery ("show me all game-theory topics across all areas"). Low cost — just a flat list of strings. Dublin Core, DITA, and SKOS all recommend it.

**Option B: Skip tags entirely.** Directory structure + topic names provide enough organization. Tags add a maintenance burden (tag sprawl, inconsistent naming).

**Option C: Add tags AND a controlled vocabulary validator.** Tags must come from a predefined list. Prevents sprawl but adds a governance burden.

*Current lean: Option A with a soft convention (no validator on specific tag values, just format validation).*

---

### T5: `related` Field — Explicit Links or Inferred?

**Option A: Add optional `related` field in frontmatter (recommended).** Explicit non-hierarchical connections. Enables "related topics" suggestions. SKOS and DITA both model this as first-class.

**Option B: Infer relationships from Go Deeper links and inline references.** No new field needed — the health system could scan for cross-references. But this conflates "further reading" with "related topics."

**Option C: Skip relationship tracking entirely.** Directory hierarchy provides enough structure. Cross-references are organic and don't need formalization.

*Current lean: Option A, but this is the lowest-priority addition. Could defer to a later version.*

---

### T6: Token Budgets — Enforce or Advise?

**Option A: Guidance only (recommended).** Token budgets appear in the spec and in author documentation, but validators only enforce line counts. Reason: token counting requires a tokenizer, which is model-specific and adds a dependency.

**Option B: Enforce token budgets via a simple word-count proxy.** ~0.75 tokens per word is a rough but consistent estimate. Add a validator that warns when word count exceeds budget ÷ 0.75.

**Option C: Enforce token budgets with a real tokenizer.** Most accurate but adds a dependency (tiktoken, sentencepiece, etc.). Breaks the stdlib-only constraint.

*Current lean: Option A. Line counts are good enough for enforcement. Token budgets inform curation judgment.*

---

### T7: Content Type — Separate from Depth?

The research (Diataxis) suggests content *type* (explanation vs. procedural vs. reference) is orthogonal to content *depth*. Currently Dewey conflates them: `depth: working` implies procedural/explanation hybrid, `depth: reference` implies lookup.

**Option A: Keep as-is (recommended).** The conflation works in practice. Adding a `type` field adds complexity for a distinction that rarely matters — most working topics are naturally explanation + procedural, and reference files are naturally lookup.

**Option B: Add optional `type` field.** Values: `explanation`, `procedural`, `reference-lookup`, `troubleshooting`. Enables more specific section structures per type (DITA's approach).

*Current lean: Option A. The three-depth model is Dewey's simplest strength. Adding type creates a 3×4 matrix that's harder to author and validate. But if your knowledge bases tend to have distinct procedural vs. explanatory topics at the same depth, Option B would let validators enforce tighter section structures per type.*

---

### T8: Naming — Rename Any Sections?

**Option A: Keep current names.** "Why This Matters," "In Practice," "Key Guidance," "Watch Out For," "Go Deeper" are clear and established.

**Option B: Rename for consistency with the attention-first ordering.** For example: "Guidance" (shorter), "Context" (instead of "Why This Matters"), "Examples" (instead of "In Practice").

**Option C: Align with Diataxis/DITA naming.** "How-To," "Explanation," "Reference" — but these are content types, not section names within a single document.

*Current lean: Option A. The names are clear and domain-neutral. But if you feel any section name doesn't communicate its purpose at a glance, this is the time to change it — breaking changes are not a concern.*

---

### T9: `relevance` Field — Tier or Description?

Currently `relevance` is overloaded — sometimes used as a tier (`"core"`, `"supporting"`, `"peripheral"`) and sometimes as a free-text description (`"First-move advantage, forcing draws, forks, and the solved game tree"`).

**Option A: `relevance` is always a free-text description (recommended).** The tier information (`core`/`supporting`/`peripheral`) is curation metadata that could live in the curation plan or `.dewey/` instead. The description serves progressive disclosure (information scent).

**Option B: Split into two fields — `relevance_tier` (enum) and `relevance` (description).** Most explicit, but adds a field.

**Option C: `relevance` is always a tier; the description goes into `summary`.** Simplest frontmatter, but loses the information scent for manifest lines (summary is longer than a one-liner).

*Current lean: Option A. In practice, the description form is far more useful for agents scanning the manifest. If we need tier-based filtering, that's a curation-plan concern.*

---

## What This Spec Does NOT Address (Future Work)

- **AGENTS.md format changes** — The manifest format may benefit from including summaries (Tier 2), but that's a separate design decision.
- **Auto-migration tooling** — An `auto_fix.py` enhancement to reorder sections and extract Source Evaluation to `.dewey/provenance/` would smooth adoption.
- **Validator implementation** — This spec defines the target; implementation is a separate task.
- **Cross-provider compatibility** — The format is provider-agnostic by design, but testing with non-Claude agents is deferred.

---

## Sources

Research artifacts that informed this specification:

- `artifacts/research/2026-02-16-agent-context-effectiveness-deep-dive.md`
- `artifacts/research/2026-02-16-knowledge-record-design-research.md`
- `artifacts/research/2026-02-16-documentation-standards-raw.md`
