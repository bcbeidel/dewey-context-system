---
name: init-context-system
description: "Set up a context management system for persistent Claude preferences, decisions, and workflows"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Context System Setup

**Purpose**: Guide users through creating a concept-based context management system grounded in [Anthropic's best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices).

**Approach**: Discovery-driven setup that identifies YOUR key domains, not generic categories.

**Time**: 1-2 hours total (can pause after any phase)

---

## Overview

This skill creates a **concept-based** context management system following Anthropic's guidance:

> "Organize by **topic/purpose**, not document type. Keep structure shallow (max 2 levels)."

**This means**:
- ❌ **Not**: `context/standards/` (type-based - standards about what?)
- ✅ **Instead**: `context/python/`, `context/security/` (topic-based - instantly discoverable)

**Why**: LLMs can find relevant context immediately. "Need Python conventions?" → `context/python/`

**See**: [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md) for complete rationale.

---

## Quick Start

```bash
# Full guided setup (all 3 phases)
/init-context-system

# Resume at specific phase
/init-context-system --phase 2
/init-context-system --phase 3
```

**Pre-flight check**: If `context/` already exists, see [Troubleshooting](./references/troubleshooting.md#existing-context-directory)

---

## Core Workflow

### Phase 1: Domain Discovery (15-30 min)

**Goal**: Identify YOUR key domains through guided questions.

**Process**:
1. Explain concept-based approach to user
2. Ask discovery questions → [Question Guide](./references/discovery-questions.md)
   - Primary work type (development, research, knowledge management)
   - Programming languages (if applicable)
   - Security needs (if applicable)
   - Research methods (if applicable)
   - Note types (if applicable)
   - Communication preferences
3. Map responses to domains → [Phase 1 Detailed Guide](./references/phases/phase-1-discovery.md)
   - Software Development → `skills/`, `python/`, `security/`, `patterns/`
   - Research → `research/`, `learning/`, `patterns/`
   - Knowledge Management → `obsidian/` or `note-system/`, `learning/`
4. Always include core domains:
   - `communication/` - Communication preferences
   - `decisions/` - Architectural decisions
   - `context-system/` - Meta documentation
5. Ensure **at least ONE user domain** beyond core (recommend starter domain if unclear)
6. Present structure, get user approval
7. Create directory structure

**Validation**: Must have 3 core + at least 1 user domain.

**Output**: `context/` directory with concept-based structure.

---

### Phase 2: Populate Core Domains (20-30 min)

**Goal**: Create initial context files in each domain with relevant standards.

**Process**:
1. **Create Communication Domain** → [Communication Template](./references/domains/communication.md)
   - `context/communication/_index.md`
   - `context/communication/style-preferences.md` (from Q6 answer)

2. **Create Context System Meta Documentation** → [Primer Templates](./references/primers/)
   - `context/context-system/_index.md`
   - `context/context-system/what-is-context.md` - What belongs in context
   - `context/context-system/organizing-principles.md` - Concept-based rationale
   - `context/context-system/quality-standards.md` - Validation criteria
   - `context/context-system/loading-map.md` - Task-to-domain mappings
   - `context/context-system/maintenance.md` - Maintenance schedule

3. **Create User-Specific Domains** → [Domain Templates](./references/domains/)
   - Python → [Python Template](./references/domains/python.md)
   - Security → [Security Template](./references/domains/security.md)
   - Skills → [Skills Template](./references/domains/skills.md)
   - (Other domains as identified in Phase 1)

4. **Create Decisions Domain** → [Decisions Template](./references/domains/decisions.md)
   - `context/decisions/_index.md`
   - `context/decisions/README.md` (ADR template reference)

5. **Create Main Context Index**
   - `context/_index.md` - Navigation hub with "For Claude" and "For Humans" sections

6. **Update or Create CLAUDE.md**
   - Reference context system in `.claude/CLAUDE.md`

**See**: [Phase 2 Detailed Guide](./references/phases/phase-2-populate.md) for complete templates and step-by-step.

**Output**: Populated domains with _index.md, initial files, and templates.

---

### Phase 3: Evolution Framework (15-20 min)

**Goal**: Establish maintenance practices for long-term evolution.

**Process**:
1. Review maintenance schedule (quarterly audits, standards sync)
2. Explain context update workflow (`/context-update` skill)
3. Set up validation process (`/audit` skill)
4. Document evolution practices in `context/context-system/maintenance.md`
5. Show navigation workflow

**See**: [Phase 3 Detailed Guide](./references/phases/phase-3-evolution.md)

**Output**: Self-sustaining system with clear maintenance practices.

---

## Phase Summary

**Phase 1 Output**:
```
context/
├── communication/
├── decisions/
├── context-system/
└── [user-domains]/    # python/, security/, research/, etc.
```

**Phase 2 Output**:
```
context/
├── _index.md                              # Main navigation
├── communication/
│   ├── _index.md
│   └── style-preferences.md
├── decisions/
│   ├── _index.md
│   └── README.md
├── context-system/
│   ├── _index.md
│   ├── what-is-context.md
│   ├── organizing-principles.md
│   ├── quality-standards.md
│   ├── loading-map.md
│   └── maintenance.md
└── [user-domains]/
    ├── _index.md
    └── [initial-files].md
```

**Phase 3 Output**:
- Maintenance schedule established
- Validation process documented
- Evolution practices in place

---

## Reference Documentation

### Phase Guides
- [Phase 1: Domain Discovery](./references/phases/phase-1-discovery.md) - Detailed discovery process with all questions and mapping logic
- [Phase 2: Populate Domains](./references/phases/phase-2-populate.md) - Complete templates for all domains and primers
- [Phase 3: Evolution Framework](./references/phases/phase-3-evolution.md) - Maintenance and validation setup

### Discovery & Mapping
- [Discovery Questions](./references/discovery-questions.md) - All 6 questions with options and conditional logic
- [Troubleshooting](./references/troubleshooting.md) - Existing context, migrations, custom domains

### Templates

**Primers** (context-system/ domain):
- [what-is-context.md](./references/primers/what-is-context.md) - What belongs in context vs docs/code
- [organizing-principles.md](./references/primers/organizing-principles.md) - Concept-based organization explained
- [quality-standards.md](./references/primers/quality-standards.md) - Validation checklist

**Domain Templates**:
- [Communication Domain](./references/domains/communication.md) - Communication preferences and style
- [Decisions Domain](./references/domains/decisions.md) - Architectural Decision Records (ADRs)
- [Python Domain](./references/domains/python.md) - Python conventions grounded in PEP 8
- [Security Domain](./references/domains/security.md) - Security standards grounded in OWASP
- [Skills Domain](./references/domains/skills.md) - Claude Code skill development standards

---

## Standards Grounding

All domains ground context in external authorities:
- **Skill Structure**: [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- **Python**: [PEP 8](https://peps.python.org/pep-0008/)
- **Security**: [OWASP Top 10](https://owasp.org/www-project-top-ten/), [OAuth 2.1](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11)
- **Research**: [PRISMA 2020](http://www.prisma-statement.org/)
- **Audit Framework**: [ISO 19011:2018](https://www.iso.org/standard/70017.html)

**See**: [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md) for complete mapping and verification URLs.

---

## Key Principles

1. **Concept-Based Organization** - Organize by topic (python/, security/) not type (standards/, preferences/)
2. **Flat Structure** - Max 2 levels deep (context/domain/file.md)
3. **Clear Entry Points** - Every domain has _index.md with "When to Use"
4. **Standards Grounding** - Link to external authorities (Anthropic, OWASP, ISO)
5. **Progressive Disclosure** - Overview files + focused topic files
6. **Evidence-Based** - Extract from real work, not hypothetical
7. **Task-Based Loading** - Load only relevant domains per task
8. **Maintenance-First** - Built-in evolution via `/context-update` and `/audit`

**Grounded in**: [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

---

## Related Skills

After setup, use these skills to maintain and evolve your context:

- **`/context-update`** - Extract learnings from conversations (run regularly)
- **`/audit`** - Validate context quality (run quarterly)
- **`/standards-sync`** - Sync external best practices (run quarterly)
- **`/compare`** - Create decision matrices for trade-offs
- **`/diagram`** - Generate Mermaid diagrams for documentation

---

## Success Criteria

✅ Concept-based structure (domains by topic, not type)
✅ 3 core domains + at least 1 user domain created
✅ All domains have _index.md with "When to Use"
✅ context-system/ primer includes organizing principles
✅ Main context/_index.md provides navigation
✅ Grounded in external authorities
✅ Maintenance schedule established

---

**Next**: After setup completes, run `/context-update` regularly to extract learnings and evolve your system.

**Authority**: [Anthropic Skill Best Practices - Progressive Disclosure](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

*Last updated: February 2026*
