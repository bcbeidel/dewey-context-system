---
title: Architectural Decisions (ADRs)
type: index
domain: decisions
created: YYYY-MM-DD
---

# Architectural Decisions (ADRs)

**Purpose**: Document important decisions with rationale to prevent re-litigating past choices.

**When to Create**: When making decisions about architecture, patterns, workflows, or standards that will affect future work.

---

## What is an ADR?

An **Architectural Decision Record (ADR)** captures:
- **Problem**: What challenge are we addressing?
- **Decision**: What did we decide to do?
- **Rationale**: Why this choice over alternatives?
- **Alternatives**: What other options were considered?
- **Implications**: What are the consequences (positive and negative)?

---

## ADR Template

```markdown
---
title: [Decision Title]
type: decision
status: accepted  # proposed | accepted | deprecated | superseded
date: YYYY-MM-DD
---

# [Decision Title]

**Status**: Accepted
**Date**: YYYY-MM-DD

## Problem

[What problem are we solving? What is the context?]

## Decision

[What did we decide to do?]

## Rationale

[Why did we choose this approach?]

## Alternatives Considered

### Alternative 1: [Name]
**Pros**: [Benefits]
**Cons**: [Drawbacks]
**Why not chosen**: [Reasoning]

### Alternative 2: [Name]
**Pros**: [Benefits]
**Cons**: [Drawbacks]
**Why not chosen**: [Reasoning]

## Implications

**Positive**:
- [Benefit 1]
- [Benefit 2]

**Negative**:
- [Trade-off 1]
- [Trade-off 2]

**Actions Required**:
- [ ] [Follow-up action 1]
- [ ] [Follow-up action 2]

## Related Decisions

- [[decisions/YYYY-MM-DD-related-decision]]

---

**Created**: YYYY-MM-DD
**Last Reviewed**: YYYY-MM-DD
**Next Review**: [When to revisit this decision]
```

---

## Naming Convention

`YYYY-MM-DD-short-descriptive-title.md`

**Examples**:
- `2026-02-09-concept-based-context-organization.md`
- `2026-01-25-template-first-skill-architecture.md`
- `2025-12-10-adopt-progressive-disclosure-pattern.md`

---

## When to Create an ADR

**✅ Create ADR for**:
- Architectural patterns (how we organize code/context)
- Tool/library selection (picking a framework)
- Process changes (workflow modifications)
- Standards adoption (following external best practices)

**❌ Skip ADR for**:
- Obvious fixes (bug corrections)
- Temporary solutions (quick hacks)
- Personal preferences without broader impact
- Routine tasks (daily operations)

---

## ADR Lifecycle

1. **Proposed**: Draft ADR, gather feedback
2. **Accepted**: Decision finalized, implement
3. **Deprecated**: No longer recommended, but not blocking
4. **Superseded**: Replaced by newer decision (link to replacement)

---

## Example ADRs

See the following for well-formed examples:
- Template-first skill architecture
- Concept-based context organization
- Progressive disclosure pattern for skills

---

**Last Updated**: [Date]
