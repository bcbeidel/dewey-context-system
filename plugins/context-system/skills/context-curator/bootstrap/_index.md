---
title: Context System Index
type: index
created: YYYY-MM-DD
---

# Context System Index

**Welcome to your context system** - structured guidance for Claude Code organized by domain.

This system helps Claude remember your preferences, decisions, and workflows across conversations.

**Total**: 27 files (19 content + 8 indexes) across 7 domains

---

## Quick Start

**Common tasks** → **Relevant domains**:

| Task | Load These Domains |
|------|-------------------|
| Skill development | [[skills/_index\|Skills]], [[auditing/_index\|Auditing]] |
| Research & synthesis | [[research/_index\|Research]], [[processes/_index\|Processes]] |
| Planning tasks | [[processes/_index\|Processes]], [[skills/_index\|Skills]] |
| Quality auditing | [[auditing/_index\|Auditing]], [[skills/_index\|Skills]] |
| Decision making | [[decisions/_index\|Decisions]], [[processes/_index\|Processes]] |

See [[context-system/_loading-map|Context Loading Map]] for complete task-to-context mappings.

---

## All Domains

### Core Skill Support

**[[skills/_index|Skill Development Standards]]** (4 files)
Standards for Claude Code skill structure, execution, refactoring, and quality validation

**[[research/_index|Research Standards]]** (7 files)
Research methodologies (Design Science, UX, Market, Mixed Methods, Case Study, Org Culture, Evidence Synthesis)

**[[auditing/_index|Quality Auditing]]** (2 files)
ISO 19011 audit standards and security validation practices

**[[processes/_index|General Processes]]** (1 file)
Planning best practices and phased execution approaches

### User Customization

**[[communication/_index|Communication Preferences]]** (1 file)
Personal communication style, feedback preferences, interaction patterns

**[[decisions/_index|Architectural Decisions]]** (1 file)
Decision records documenting important choices with rationale (ADR template)

### Meta (Context System Itself)

**[[context-system/_index|Context System Meta]]** (2 files)
Context system overview, organization principles, and task-based loading map

---

## How to Use This System

### For Claude (LLMs)
1. Read task/question from user
2. Check [[context-system/_loading-map|loading map]] to identify relevant domains
3. Load domain `_index.md` files for those domains
4. Review "When to Use" guidance
5. Load specific files as needed

### For Humans
- Browse domains by category above
- Click domain index to see all files
- Use wikilinks to navigate between related concepts
- Run `/context-curator` regularly to extract new learnings

---

## Organization Principles

1. **Concept-Based**: Organized by topic (skills/, research/), not type (standards/, workflows/)
2. **Flat Structure**: Max 2 levels deep (domain/file.md)
3. **Progressive Disclosure**: Overview in index, details in individual files
4. **Cross-Referenced**: Related domains linked for easy navigation
5. **Index-Driven**: Every domain has `_index.md` with "When to Use" guidance

---

## Maintenance

**Run `/context-curator` to**:
- Extract new context from conversations
- Validate index completeness (automated checks)
- Maintain cross-references
- Archive outdated content

**Cadence**:
- After major work sessions (extract decisions)
- Monthly (comprehensive review)
- Quarterly (validation + cleanup)

---

## Key Files

- [[context-system/_loading-map|Context Loading Map]] - Task → Context mappings
- [[context-system/_index|Context System Overview]] - Organization and maintenance
- [[communication/style-preferences|Communication Preferences]] - Your style preferences
- [[decisions/_index|Decision Template]] - ADR guidance

---

**Created**: [Bootstrap date]
**Structure Version**: 1.0 (bootstrapped by /context-curator)
**Next Review**: [30 days after creation]
