# Knowledge Record Specification

A knowledge record is a single markdown file that distills external sources into
curated, structured knowledge optimized for both AI agent consumption and human
cognition.

This spec defines what makes one excellent.

---

## The Contract

Every knowledge record makes three promises:

1. **Grounded in sources.** Every claim traces to a primary source. The record
   is a guide, not a replacement — when the reader needs more, the path to the
   original is always clear.

2. **Earns every line.** Context rot degrades LLM performance 13–85% as length
   increases. 300 focused tokens outperform 113K unfocused tokens. If a line
   doesn't serve the reader, it doesn't belong.

3. **Works for both audiences.** Agents need predictable structure and token
   efficiency. Humans need readable prose and clear navigation. When these
   conflict, favor human readability — agents are more adaptable readers.

---

## Frontmatter

```yaml
---
summary: "1–3 sentence standalone description. Must make sense without
  reading the body. This is the 'lead section' — it lets a reader decide
  whether to continue."
sources:
  - url: https://example.com/primary-source
    title: "Source Title"
  - url: https://example.com/another-source
    title: "Another Source"
last_validated: 2026-02-16
relevance: "Who this helps and when — one line of information scent"
depth: working
tags: [optional, cross-cutting, keywords]
related:
  - ../other-area/related-topic.md
---
```

| Field | Required | What It Does |
|-------|----------|-------------|
| `summary` | Yes | The single most important metadata field. A standalone description that lets agents and humans decide whether to load the full file. 1–3 sentences, no jargon that requires the body for context. |
| `sources` | Yes | Primary source URLs with titles. Every record must point back to at least one authoritative source. |
| `last_validated` | Yes | ISO date when content was last verified against its sources. Drives freshness health checks. |
| `relevance` | Yes | One line: who does this help and when? Information scent for scanning. Always a description, never a category. |
| `depth` | Yes | `overview` (area orientation) or `working` (actionable knowledge). |
| `tags` | No | Flat list of lowercase, hyphenated keywords for cross-cutting discovery. |
| `related` | No | Relative paths to non-hierarchical peer topics. |

### The Summary Field

The summary is not a teaser or introduction — it is a **standalone micro-document**.
A reader who only sees the summary should walk away with the key insight.

**Good:** "Tic-tac-toe is a solved game where perfect play always draws. Forks —
creating two simultaneous threats — are the only winning mechanism. The Newell &
Simon priority list gives an optimal decision procedure."

**Bad:** "This document covers tic-tac-toe strategy including openings, forks,
and optimal play." *(Describes the document, not the knowledge.)*

**Bad:** "An overview of optimal strategy." *(Says nothing.)*

---

## Body Structure

### Working Depth

Working records carry actionable knowledge. They are organized for the
U-shaped attention curve: beginning and end get the most attention, middle
gets the least.

```
# Topic Title

## Guidance
## Context
## In Practice
## Pitfalls
## Quick Reference       ← optional
## Go Deeper
```

**Guidance** — First position (primacy effect). Actionable recommendations the
reader can apply immediately. If an agent can only read one section, this is it.

Format: Numbered items. Each starts with a **bold declarative statement**,
followed by explanation and an inline source citation.

```markdown
**1. The first player cannot lose with perfect play.** A strategy-stealing
argument proves this: if the second player had a winning strategy, the first
player could steal it by going first ([Hamkins][hamkins]).
```

---

**Context** — Why this topic matters. When it applies. How it connects to the
broader domain. This is the "why" section — causal reasoning, not just facts
(Principle #10).

Format: 1–3 paragraphs of prose. Establishes motivation without repeating
the summary.

---

**In Practice** — Concrete examples and worked scenarios (Principle #11:
concrete before abstract). Sits in the middle position, which has the lowest
attention — but examples are inherently engaging and resist the attention
valley better than abstract content.

Format: Step sequences, code blocks, decision tables, case studies. Lead with
the concrete scenario, then generalize.

---

**Pitfalls** — Mistakes, anti-patterns, and misconceptions. Positioned near
the end to benefit from the recency effect — warnings stick when they're the
last substantive content a reader encounters.

Format: Bold heading per pitfall. Brief explanation. Include counter-evidence
found during research.

---

**Quick Reference** — Optional. Include only when the topic has significant
lookup data (tables, formulas, decision trees, cheat sheets). When present,
it sits near the end where the recency effect supports recall of factual data.

Format: Tables and lists only. No prose paragraphs. Terse and scannable.

---

**Go Deeper** — Links to primary sources and further reading. Always the last
section. Primary sources first (already cited in the body), then supplementary
material.

Format: Bullet list with brief annotations.

---

### Overview Depth

Overview records orient the reader within a domain area.

```
# Area Name

## What This Covers
## Topics
## Key Sources
```

**What This Covers** — 1–2 paragraphs describing the scope and boundaries of
this domain area.

**Topics** — Table of topics in this area with links and one-line descriptions.

**Key Sources** — Area-level primary sources (not topic-specific).

---

## Size Discipline

| Depth | Lines | Token Guidance |
|-------|-------|---------------|
| Overview | 5–150 | ~200–2,000 |
| Working | 10–500 | ~500–5,000 |
| Summary | 1–3 sentences | ~30–80 |

Line counts are enforced. Token budgets are guidance.

---

## Source Integration

### Citation Style

Use Markdown reference-style links. Define URLs once at the bottom of the file.
This keeps the body clean and avoids URL repetition.

```markdown
The strategy-stealing argument proves X cannot lose ([Hamkins][hamkins]).

[hamkins]: https://www.infinitelymore.xyz/p/tic-tac-toe-and-variants
```

### Source Selection Criteria

Every source included in the frontmatter should meet these criteria:

| Criterion | Question |
|-----------|----------|
| **Authority** | Is the author/organization credible in this domain? |
| **Accuracy** | Are the claims verifiable and consistent with other sources? |
| **Currency** | Is the information current enough for this topic? |
| **Purpose fit** | Does this source serve the knowledge base reader's needs? |
| **Corroboration** | Is the claim supported by at least one other independent source? |

Aim for 2–5 sources per topic. Prefer diversity — multiple domains and
perspectives over multiple pages from the same site.

### Grounding Claims

Every factual claim and recommendation in the Guidance section should have an
inline citation. Claims in other sections should cite sources when the claim
is non-obvious or the reader might want to verify.

The standard is: **a skeptical reader should be able to trace any key claim
back to a primary source within one click.**

### Counter-Evidence

During research, actively search for counter-evidence: "X is wrong," "X doesn't
work," "alternatives to X." Findings go in the Pitfalls section. The goal is not
to present a balanced debate — it's to make the record more trustworthy by
showing the author looked for reasons the guidance might be wrong.

---

## Content Quality Principles

### Explain the Why

Don't just state what to do — explain *why* it works. Causal reasoning produces
better comprehension and retention than prescriptive rules.

**Good:** "Center is the strongest opening because it touches 4 winning lines —
both diagonals, the middle row, and the middle column. Corners touch only 3."

**Bad:** "Always open with center."

### Concrete Before Abstract

Lead with specific examples, then build toward the generalization. Concrete
scenarios create stronger memory traces than abstract principles.

**Good:** Start In Practice with "Consider the opening from X's perspective,
starting with a corner move: ..." and then generalize to the principle.

**Bad:** Start with "There are three types of openings..." and then give
examples later.

### One Level of Depth

Don't mix beginner and expert content in the same record. The depth field
signals who this is for. Overview records orient newcomers. Working records
serve practitioners. Content that helps novices can actively hinder experts
(expertise reversal effect) — write for one audience.

### Self-Contained

Each record should make sense without reading other records. Establish enough
context in the Context section that a reader arriving at this file for the
first time can orient themselves. Link to related topics in Go Deeper, but
don't depend on them for comprehension.

### Honest About Limitations

If the guidance has known limitations, edge cases, or conditions where it
doesn't apply — say so. In the Pitfalls section or inline in Guidance. A
record that acknowledges its boundaries is more trustworthy than one that
doesn't.

---

## Curation Metadata

Source evaluations and research provenance are recorded separately from the
knowledge record, in `.dewey/provenance/<topic-slug>.json`. This metadata
serves the curation process (evaluating and maintaining sources), not the
consumer (using the knowledge). Keeping it separate means every line in the
topic file serves the reader.

```json
{
  "research_date": "2026-02-16",
  "sources_evaluated": 7,
  "sources_included": 5,
  "sources_excluded": 2,
  "exclusion_reasons": ["redundant coverage", "scope mismatch"],
  "counter_evidence_searched": true,
  "counter_evidence_found": ["finding 1", "finding 2"],
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

---

## Checklist

Before a knowledge record is complete:

- [ ] Summary is standalone — makes sense without the body
- [ ] Every Guidance item has an inline source citation
- [ ] At least 2 sources, from different domains/authors
- [ ] Counter-evidence was searched for and findings recorded
- [ ] Guidance section is first (after the title)
- [ ] No prose in Quick Reference (tables and lists only)
- [ ] All reference-style links resolve
- [ ] `last_validated` is today's date
- [ ] File is within size bounds for its depth
- [ ] Curation metadata written to `.dewey/provenance/`
