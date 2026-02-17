# Knowledge Record Specification

Version: 1.0-draft
Date: 2026-02-16

## Abstract

A Knowledge Record is a markdown file format for curated, source-grounded
knowledge optimized for consumption by both AI language model agents and human
readers. This specification defines the required metadata, section structure,
ordering constraints, and content conventions.

The format is designed to be implementation-agnostic, delivery-mechanism-agnostic,
and provider-agnostic. It can be consumed by any system that reads markdown files.

## Status

Draft. Open for review.

## Conventions

The key words "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", and "MAY" in this
document are to be interpreted as described in RFC 2119.

---

## 1. File Format

A Knowledge Record MUST be a UTF-8 encoded text file with the `.md` extension.

A Knowledge Record MUST consist of, in order:

1. YAML frontmatter (Section 2)
2. A title heading (Section 3)
3. Body sections (Section 4)
4. Optionally, reference-style link definitions (Section 5)

**Justification:** Every major AI coding agent surveyed — Claude Code, Cursor,
GitHub Copilot, Windsurf, Codex, Gemini CLI — converges on Markdown as the
content format for agent-consumed knowledge. McMillan (2025) tested 9,649
experiments across 11 models and 4 formats and found that format does not
significantly affect aggregate accuracy for frontier models (chi-squared=2.45,
p=0.484), but Markdown provides the best human readability while YAML provides
the most token-efficient metadata encoding [1]. XML encodes the same information
with approximately 80% more tokens than Markdown [2].

---

## 2. Frontmatter

A Knowledge Record MUST begin with YAML frontmatter delimited by `---` lines.

### 2.1 Required Fields

#### `summary`

- Type: String
- Constraint: 1–3 sentences
- Requirement: MUST be present for records with `depth: working` or `depth: overview`

The summary MUST be a standalone description that is meaningful without reading
the body. It MUST NOT describe the document ("This document covers...") — it
MUST describe the knowledge ("Tic-tac-toe is a solved game where...").

A reader who sees only the summary SHOULD walk away with the key insight of
the record.

**Justification:** The summary field creates an intermediate progressive
disclosure tier. The Agent Skills specification defines a 3-tier model:
~100 tokens (description) → <5,000 tokens (body) → unbounded (references) [3].
Without a summary, agents must jump from a ~15-token manifest entry to a
~2,000-token full file. The summary tier (~50 tokens per topic) lets an agent
scan 20 topic summaries for ~1,000 tokens and decide which to fully load.

This pattern is independently validated by: DITA's `<shortdesc>` element, which
serves as a standalone topic summary in search results and link previews [4];
Wikipedia's lead section policy, which requires a 100–400 word standalone
summary before the first heading [5]; Azure AI Search's enrichment pipeline,
which generates document summaries for RAG retrieval [6]; and the llms.txt
specification's blockquote summary format [7].

#### `sources`

- Type: List of objects, each with `url` (string) and `title` (string)
- Constraint: MUST contain at least one entry

Each source MUST be a primary or authoritative reference for the record's content.

**Justification:** Source primacy — the knowledge base is a curated guide, not a
replacement for primary sources. When an agent or human needs to go deeper, the
path must be clear. This principle is grounded in Anthropic's context engineering
guidance: "point to primary sources" rather than duplicating them, because primary
sources are maintained by domain experts and stay current [8]. Dublin Core's
`Source` element serves the same purpose in metadata standards [9].

#### `last_validated`

- Type: ISO 8601 date (YYYY-MM-DD)
- Constraint: MUST be a valid date not in the future

The date when the record's content was last verified against its sources.

**Justification:** Knowledge freshness degrades over time. Guru's verification
model assigns each knowledge card a verification interval and visual staleness
indicators [10]. JATS (Journal Article Tag Suite) tracks multiple dates per
article: received, revised, accepted, published [11]. The `last_validated` field
enables automated freshness checking: a health system can flag records that
haven't been verified within a configurable threshold.

#### `relevance`

- Type: String
- Constraint: MUST be a descriptive phrase, not a category

The relevance field MUST describe who this record helps and when. It serves as
information scent — a signal that helps agents and humans decide whether to load
the full record.

Examples of conforming values:
- `"First-move advantage, forcing draws, forks, and the solved game tree"`
- `"Core principles for the first 10-15 moves of a chess game"`

Examples of non-conforming values:
- `"core"` (category, not description)
- `"important"` (subjective, not informative)

**Justification:** Information scent theory (Pirolli & Card, 1999) predicts that
users follow cues that signal the likelihood of finding relevant information [12].
A descriptive relevance field provides stronger scent than a category label. In
the Agent Skills specification, the skill `description` field serves this purpose
at the skill level [3]; `relevance` serves it at the topic level.

#### `depth`

- Type: Enum string
- Values: `overview` | `working`
- Constraint: MUST be one of the specified values

Indicates the record's position in the progressive disclosure chain.

| Value | Purpose |
|-------|---------|
| `overview` | Area orientation: what this domain covers, what topics exist |
| `working` | Actionable knowledge with guidance, examples, and sources |

**Justification:** The two-depth model derives from Diataxis's four-quadrant
taxonomy reduced for agent consumption. Diataxis distinguishes tutorials
(learning by doing), how-to guides (goal-oriented steps), explanations
(understanding), and reference (lookup) [13]. For AI agents, tutorials are
irrelevant — agents don't learn by doing. The remaining three types map to:
explanation → `overview`, how-to/procedural → `working`, reference → integrated
as a section within `working` records. This reduction from three file types to
two (with reference content as an optional section) eliminates companion file
synchronization overhead while preserving the progressive disclosure chain.

The expertise reversal effect (Kalyuga et al., 2003) demonstrates that material
designed for novices can actively hinder experts and vice versa [14]. The depth
field allows readers to self-select the appropriate level.

### 2.2 Optional Fields

#### `tags`

- Type: List of strings
- Convention: lowercase, hyphenated
- Constraint: No duplicates within a record

Keywords for cross-cutting discovery.

**Justification:** Dublin Core's `Subject` element [9], DITA's `<keyword>`
element [4], and SKOS's `altLabel` [15] all recommend keyword metadata for
retrieval enrichment. Tags enable queries like "all game-theory topics across
all domain areas" that hierarchical directory structure alone cannot serve.

#### `related`

- Type: List of relative file paths
- Constraint: Each path SHOULD resolve to an existing file

Explicit non-hierarchical connections to peer topics.

**Justification:** SKOS defines `skos:related` for non-hierarchical associations
between concepts [15]. DITA uses relationship tables for the same purpose [4].
These connections are distinct from hierarchical parent-child relationships
(implicit in directory structure) and from source links (in Go Deeper).

---

## 3. Title

The record body MUST begin with a single H1 heading (`# Title`).

There MUST be exactly one H1 heading in the record. All subsequent headings
MUST be H2 (`##`).

**Justification:** Markdown best practice (markdownlint MD025) and DITA's
requirement that every topic has exactly one `<title>` element [4]. A single
H1 provides an unambiguous topic identifier for manifest generation and
cross-referencing.

---

## 4. Sections

### 4.1 Working Depth

A record with `depth: working` MUST contain these sections in this order:

1. `## Guidance`
2. `## Context`
3. `## In Practice`
4. `## Pitfalls`
5. `## Go Deeper`

A record with `depth: working` MAY contain a `## Quick Reference` section.
If present, it MUST appear between `## Pitfalls` and `## Go Deeper`.

#### 4.1.1 Section Ordering Rationale

The ordering is driven by the U-shaped attention curve in language models.

Liu et al. (2024) demonstrated that LLM performance degrades significantly
when relevant information is placed in the middle of input context, with the
effect confirmed across 6+ follow-up studies and shown to be architectural
rather than training-dependent [16]. The Chroma Research "Context Rot" study
(2025) measured 13.9–85% performance degradation as context length increases
across 18 models [17]. Anthropic's context engineering guidance notes that 300
focused tokens outperform 113,000 unfocused tokens [8].

The section order exploits three attentional effects:

**Primacy effect (Guidance, position 1):** The beginning of input receives
the highest attention weight. Guidance contains the most actionable content —
the section an agent reads if it can only read one section. Placing it first
ensures it occupies the highest-attention position.

**Engagement resistance (In Practice, position 3):** Concrete examples are
inherently more engaging than abstract content. Cognitive science research on
concrete vs. abstract processing (Paivio, 1986) shows concrete material creates
stronger memory traces [18]. Positioning examples in the middle — the lowest-
attention zone — leverages their natural engagement to partially counteract the
attention valley.

**Recency effect (Pitfalls, position 4):** The end of input receives elevated
attention. Warnings and pitfalls benefit from recency — they are the last
substantive content the reader encounters, making them more likely to be
retained and applied.

#### 4.1.2 Guidance

Content: Actionable recommendations the reader can apply immediately.

Format: Numbered items. Each MUST begin with a **bold declarative statement**,
followed by explanation and an inline source citation.

```markdown
**1. The first player cannot lose with perfect play.** A strategy-stealing
argument proves this: if the second player had a winning strategy, the first
player could steal it ([Hamkins][hamkins]).
```

**Justification:** Information Mapping's "principle" information type prescribes
guidelines and rules as the highest-value content in a reference document [19].
DITA's `<taskbody>` places the step sequence (the actionable content) as the
primary body element [4]. The bold-statement-then-explanation pattern provides
dual-speed reading: the bold text is scannable for quick reference, the
explanation provides depth for full reading.

#### 4.1.3 Context

Content: Why this topic matters. When it applies. How it connects to the
broader domain.

The Context section SHOULD contain causal reasoning — explaining *why* guidance
works, not just *what* to do.

**Justification:** Dunlosky et al. (2013) found that elaborative interrogation
(asking "why") produces significantly better learning outcomes than re-reading
or highlighting [20]. Records that explain causal mechanisms produce better
agent outputs than records that state prescriptive rules, because the agent can
adapt the reasoning to novel situations rather than pattern-matching against
specific instructions.

#### 4.1.4 In Practice

Content: Concrete examples, worked scenarios, code blocks, decision tables.

The In Practice section SHOULD lead with a specific scenario before generalizing.

**Justification:** Concrete-before-abstract ordering is grounded in Paivio's
dual coding theory (1986), which demonstrates that concrete concepts create both
verbal and imaginal memory representations, producing stronger encoding [18].
Sweller's cognitive load theory (1988) supports worked examples as reducing
extraneous cognitive load compared to abstract problem-solving [21].

#### 4.1.5 Pitfalls

Content: Mistakes, anti-patterns, and misconceptions.

Each pitfall SHOULD begin with a **bold heading** followed by a brief
explanation.

The Pitfalls section SHOULD include counter-evidence found during research —
reasons the guidance might be wrong or limited.

**Justification:** Bjork's desirable difficulty framework (1994) shows that
encountering and resolving difficulties during learning produces more durable
understanding [22]. Counter-evidence signals intellectual honesty, increasing
reader trust. Wikipedia's neutral point of view policy requires presenting
significant viewpoints — this principle adapts it for curated knowledge, where
the author has a recommendation but acknowledges limitations.

#### 4.1.6 Quick Reference (Optional)

Content: Terse lookup data — tables, lists, decision trees, cheat sheets.

A Quick Reference section MUST NOT contain prose paragraphs. Content MUST be
tables, bullet lists, or other scannable formats.

This section is OPTIONAL. It SHOULD be included only when the topic has
significant factual data that benefits from tabular presentation.

**Justification:** This replaces the previous `.ref.md` companion file pattern.
DITA's reference topic type (`<refbody>`) allows tables and property lists in
any sequence because reference content is shaped by its data, not a narrative
flow [4]. Integrating reference data into the working record eliminates
companion file synchronization overhead and places the data in a high-attention
position (recency effect at the end of the file).

#### 4.1.7 Go Deeper

Content: Links to primary sources and further reading.

Primary sources (already cited in the body) SHOULD appear first, followed by
supplementary material.

**Justification:** EPPO's "links richly" principle makes connections to related
content first-class [23]. Positioning Go Deeper last mirrors Wikipedia's
convention of placing "References" and "External links" at the end of articles
[5], and DITA's `<related-links>` element at the end of topics [4].

### 4.2 Overview Depth

A record with `depth: overview` MUST contain these sections in this order:

1. `## What This Covers`
2. `## Topics`
3. `## Key Sources`

The Topics section SHOULD contain a table with columns for topic name (as a
link) and description.

**Justification:** Overview records serve the "orientation" function identified
by Diataxis as the explanation quadrant [13] and by EPPO's "establishes context"
characteristic [23]. The Topics table provides a navigation hub for progressive
disclosure into working-depth records.

---

## 5. Link Definitions

A Knowledge Record SHOULD use reference-style Markdown links.

Reference-style link definitions MUST appear at the end of the file, after
all sections:

```markdown
[wiki]: https://en.wikipedia.org/wiki/Tic-tac-toe
[hamkins]: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
```

**Justification:** Reference-style links produce cleaner body text by
separating content from URLs. They eliminate URL duplication when the same
source is cited multiple times. This convention is RECOMMENDED but not REQUIRED
because inline links are semantically equivalent and some authoring tools
handle them better.

---

## 6. Source Integration

### 6.1 Citation Density

Every factual claim in the Guidance section MUST have an inline source citation.

Claims in other sections SHOULD have inline citations when the claim is
non-obvious or the reader might want to verify.

**Justification:** The grounding standard is: a skeptical reader can trace any
key claim to a primary source within one click. This implements the Source
Primacy principle — the record is a curated guide, not a replacement for primary
sources [8].

### 6.2 Source Diversity

A record SHOULD include sources from at least 2 different domains or authors.

**Justification:** Wikidata's provenance model requires references from
independent sources for claim verification [24]. Source diversity reduces the
risk of systematic bias from a single perspective.

### 6.3 Counter-Evidence

During record creation, the author SHOULD actively search for counter-evidence:
reasons the guidance might be wrong, limited, or context-dependent.

Counter-evidence findings SHOULD be incorporated into the Pitfalls section.

**Justification:** Wikipedia's neutral point of view policy and the scientific
method both require consideration of opposing evidence. The Beyond Accuracy
framework (ESEC/FSE 2020) identifies accuracy as only one of ten documentation
quality dimensions — completeness and relevance require addressing edge cases
and limitations [25].

---

## 7. Size Constraints

### 7.1 Working Depth

A record with `depth: working` MUST be between 10 and 500 lines.

The recommended token budget is 500–5,000 tokens.

### 7.2 Overview Depth

A record with `depth: overview` MUST be between 5 and 150 lines.

The recommended token budget is 200–2,000 tokens.

### 7.3 Summary Field

The `summary` field MUST be 1–3 sentences.

The recommended token budget is 30–80 tokens.

### 7.4 Enforcement

Line counts are normative (MUST). Token budgets are informative (SHOULD).

**Justification:** Line counts are deterministic and require no external
dependencies to verify. Token counts vary by tokenizer and model. The Agent
Skills specification uses a similar approach: "<500 lines" as the enforceable
constraint, with token guidance (~5,000 tokens) as the design target [3].

The upper bound of 5,000 tokens aligns with the Agent Skills Tier 2 limit and
with Anthropic's guidance that effective context utilization drops significantly
beyond this range for individual documents within a larger context assembly [8].

---

## 8. Curation Metadata

Source evaluations and research provenance MUST NOT appear in the record body.

Curation metadata SHOULD be stored in a separate file (e.g., JSON) outside
the record's file path.

**Justification:** Source evaluation tables consume approximately 20 lines of
content that serves the curation process, not the consumer. Anthropic's context
engineering guidance emphasizes that "every token matters" and non-essential
content dilutes the signal [8]. The Chroma Research context rot study quantifies
this: additional context that doesn't contribute to the task measurably degrades
performance [17]. Separating curation metadata from consumer content ensures
every line in the record serves the reader.

---

## 9. Conformance

A document conforms to this specification if it satisfies all MUST requirements
defined in Sections 1–8.

A document partially conforms if it satisfies all MUST requirements in Sections
1–3 (file format, frontmatter required fields, title) but not all requirements
in Sections 4–8.

Partial conformance enables incremental adoption — a record can have valid
metadata and structure while its section content is being developed.

---

## References

[1] McMillan, J. (2025). "Structured Context Engineering for AI Models."
arXiv:2602.05447. 9,649 experiments across 11 models and 4 formats. Format
does not significantly affect aggregate accuracy (chi-squared=2.45, p=0.484).

[2] OASIS DITA Technical Committee (2017). "Darwin Information Typing
Architecture (DITA) Version 1.3." OASIS Standard.
https://docs.oasis-open.org/dita/dita/v1.3/dita-v1.3-part3-all-inclusive.html

[3] Agent Skills Specification. https://agentskills.io/specification —
Three-tier progressive disclosure: ~100 tokens (Tier 1), <5,000 tokens
(Tier 2), unbounded (Tier 3).

[4] OASIS DITA 1.3 — Topic types (concept, task, reference), `<shortdesc>`
element, `<prolog>` metadata, `<related-links>`, relationship tables.

[5] Wikipedia Manual of Style: Layout.
https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Layout — Lead section
policy: 100-400 words, standalone summary, no heading.

[6] Microsoft Azure AI Search Documentation. RAG enrichment pipelines
generate document summaries for improved retrieval.

[7] llms.txt Specification. https://llmstxt.org/ — Blockquote summary format
for LLM-consumed documentation.

[8] Anthropic (2025). "Effective Context Engineering for AI Agents."
https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
— Write, Select, Compress, Isolate framework. 300 focused tokens outperform
113K unfocused tokens.

[9] Dublin Core Metadata Element Set.
https://www.dublincore.org/specifications/dublin-core/dces/ — 15 core elements
including Title, Subject, Description, Source, Date, Relation.

[10] Guru Verification Model.
https://help.getguru.com/docs/verifying-and-unverifying-cards — Verification
intervals, assigned verifiers, visual staleness indicators.

[11] JATS (Journal Article Tag Suite). NISO Z39.96-2019. Structured dates:
received, revised, accepted, published. Structured abstracts.

[12] Pirolli, P. & Card, S.K. (1999). "Information Foraging." Psychological
Review, 106(4), 643-675. Information scent theory: users follow cues that
signal the likelihood of finding relevant information.

[13] Diataxis Framework. https://diataxis.fr/ — Four documentation quadrants:
tutorials, how-to guides, explanations, references. Two axes: practical/
theoretical, acquisition/application.

[14] Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). "The
Expertise Reversal Effect." Educational Psychologist, 38(1), 23-31. Material
that assists novices can hinder expert performance due to redundancy.

[15] SKOS Reference (W3C Recommendation).
https://www.w3.org/TR/skos-reference/ — `broader`, `narrower`, `related`,
`prefLabel`, `altLabel`, `definition`, `scopeNote`.

[16] Liu, N.F., Lin, K., Hewitt, J., Paranjape, A., Bevilacqua, M., Petroni,
F., & Liang, P. (2024). "Lost in the Middle: How Language Models Use Long
Contexts." Transactions of the ACL, 12, 157-173. U-shaped attention curve
confirmed across multiple models and tasks.

[17] Chroma Research (2025). "Context Rot." https://research.trychroma.com/context-rot
— 13.9–85% performance degradation as context length increases. 18 models
tested. Architectural, not a training artifact.

[18] Paivio, A. (1986). "Mental Representations: A Dual Coding Approach."
Oxford University Press. Concrete concepts create both verbal and imaginal
memory representations, producing stronger encoding than abstract concepts.

[19] Horn, R.E. (1998). "Structured Writing as a Paradigm." In A. Romiszowski
& C. Dills (Eds.), Instructional Development Paradigms. Six information types:
procedure, process, principle, concept, structure, fact.

[20] Dunlosky, J., Rawson, K.A., Marsh, E.J., Nathan, M.J., & Willingham,
D.T. (2013). "Improving Students' Learning With Effective Learning Techniques."
Psychological Science in the Public Interest, 14(1), 4-58. Elaborative
interrogation and self-explanation rated as moderate-to-high utility.

[21] Sweller, J. (1988). "Cognitive Load During Problem Solving: Effects on
Learning." Cognitive Science, 12(2), 257-285. Worked examples reduce extraneous
cognitive load compared to means-ends problem solving.

[22] Bjork, R.A. (1994). "Memory and Metamemory Considerations in the Training
of Human Beings." In J. Metcalfe & A. Shimamura (Eds.), Metacognition.
Desirable difficulties during learning produce more durable understanding.

[23] Baker, M. (2013). "Every Page is Page One: Topic-based Writing for
Technical Communication and the Web." XML Press. Seven characteristics:
self-contained, specific purpose, domain-typed, establishes context, assumes
qualified reader, stays on one level, links richly.

[24] Wikidata Data Model. https://www.wikidata.org/wiki/Wikidata:Data_model —
Statement model with claims, qualifiers, references, and rank
(preferred/normal/deprecated).

[25] Aghajani, E., et al. (2020). "Software Documentation: The Practitioners'
Perspective." ESEC/FSE 2020. Ten quality dimensions: organization, internal
consistency, accuracy, completeness, currency, relevance, readability,
conciseness, consistency, appeal.
