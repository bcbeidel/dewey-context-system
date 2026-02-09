---
title: Context System Overview
type: index
domain: context-system
created: YYYY-MM-DD
---

# Context System Overview

**Purpose**: Persistent, structured context that helps Claude remember your preferences, decisions, and patterns across conversations.

**Organization**: Concept-based domains (organized by topic, not type).

---

## How This Works

### For Claude (LLMs)
1. Read task/question from user
2. Check [[context-system/_loading-map|loading map]] to identify relevant domains
3. Load domain `_index.md` files for those domains
4. Review "When to Use" guidance
5. Load specific files as needed

### For Humans
- Browse domains below by category
- Click domain index to see all files
- Use wikilinks to navigate between related concepts

---

## All Domains

### Core Skill Support

**[[skills/_index|Skill Development]]**
- Standards for Claude Code skill structure, execution, and quality
- **When to use**: Developing, auditing, or refactoring Claude Code skills

**[[research/_index|Research Standards]]**
- Research methodologies (Design Science, UX, Market, Mixed Methods, Case Study, Org Culture, Evidence Synthesis)
- **When to use**: Conducting research, systematic reviews, or evidence synthesis

**[[auditing/_index|Quality Auditing]]**
- ISO 19011 audit standards, security validation, quality checklists
- **When to use**: Quality audits, compliance checks, security validation

**[[processes/_index|General Processes]]**
- Planning best practices, note creation, phased execution
- **When to use**: Planning tasks, creating documentation, executing projects

### User Customization

**[[communication/_index|Communication Preferences]]**
- Personal communication style, feedback preferences, interaction patterns
- **When to use**: Always (foundational preferences)

**[[decisions/_index|Architectural Decisions]]**
- Decision records documenting important choices with rationale
- **When to use**: Referencing past decisions, making new architectural choices

### Meta (Context System Itself)

**[[context-system/_loading-map|Loading Map]]**
- Task → Context mappings (what to load when)

**[[context-system/_navigation-guide|Navigation Guide]]**
- How to find what you need

---

## Organization Principles

1. **Concept-Based**: Organized by topic (skills/, research/), not type (standards/, workflows/)
2. **Flat Structure**: Max 2 levels deep (domain/file.md)
3. **Progressive Disclosure**: Main files <150 lines, details in references/
4. **Cross-Referenced**: Related domains linked for easy navigation
5. **Index-Driven**: Every domain has `_index.md` with "When to Use" guidance

---

## How to Extend

### Adding a New Domain

1. **Create directory**: `context/new-domain/`
2. **Create index**: `context/new-domain/_index.md` with:
   - Description
   - "When to Use" guidance
   - List of files
3. **Add to main index**: Update `context/_index.md`
4. **Update loading map**: Add task mappings to `context-system/_loading-map.md`

### Adding Files to Existing Domain

1. **Create file**: `context/domain/topic.md`
2. **Update domain index**: Add to domain's `_index.md`
3. **Run validation**: Use `/context-curator` quality gates to verify indexes

---

## Quality Standards

**File Requirements**:
- ✅ Frontmatter (title, type, domain, created)
- ✅ Clear purpose statement
- ✅ "When to Use" guidance
- ✅ Related context links
- ✅ <150 lines (main files), extract details to references/

**Index Requirements**:
- ✅ All files listed in domain `_index.md`
- ✅ All domains listed in main `context/_index.md`
- ✅ File counts accurate
- ✅ No broken wikilinks

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

**Created**: [Date]
**Last Updated**: [Date]
**Next Review**: [Quarterly]
