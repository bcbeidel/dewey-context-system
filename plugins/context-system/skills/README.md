# Context System Skills

These skills are included with the context-system plugin. Once installed, they're available globally across all your projects.

---

## Context Management

### `/context-curator`
**Location**: `skills/context-curator/`

Bootstrap context system on first run, then extract learnings from conversations to maintain and evolve it.

**Pattern**: Automated bootstrap → domain-agnostic extraction → quality validation

**Use when**: First run (bootstrap), after significant work sessions, when you notice patterns worth capturing.

**Key features**:
- **Bootstrap**: Creates context system with best practices for distributed skills (first run)
- Discovers your domains dynamically from context/_index.md
- Maps context to appropriate domain by topic
- Automated quality gates (Steps 7.5, 12.9)
- Index validation script

---

## Research & Planning Skills

### `/researcher`
**Location**: `skills/researcher/`

Multi-methodology research orchestrator with intelligent methodology selection for technology, marketing, and software contexts.

**Pattern**: Guided methodology selection → structured execution → evidence-based synthesis

**Use when**: Academic research, market analysis, user research, organizational studies, evidence synthesis

**Key features**:
- 7 research methodologies (Design Science, UX Research, Market Research, Mixed Methods, Case Study, Organizational Culture, Evidence Synthesis)
- Intelligent methodology selection wizard
- PRISMA 2020 compliance (evidence synthesis)
- Quality assessment and validation

---

### `/planner`
**Location**: `skills/planner/`

Create structured, evidence-based plans for multi-step tasks with hierarchical decomposition and quality validation.

**Pattern**: Requirements gathering → structured planning → quality validation → human approval

**Use when**: Multi-step tasks (3+ steps), complex problems requiring decomposition, long-horizon work (hours to days)

**Key features**:
- 3 planning strategies (decompose-first, interleaved, milestone-based)
- 5-dimension quality validation (completeness, feasibility, efficiency, maintainability, adaptability)
- Saves plans to /projects/ for resumable execution
- Markdown + YAML frontmatter format

---

## Meta-Skills (Advanced Patterns)

### `/auditor`
**Location**: `skills/auditor/`

Orchestrate systematic audits (quality, compliance, security, performance) across any artifact type using ISO 19011:2018 principles.

**Pattern**: Risk-based prioritization, automated + manual checks, trend tracking, standards feedback loop.

**Use when**: Quarterly comprehensive audits, monthly light checks, before major releases, when quality degrades.

**Key features**:
- Configurable artifact types (skills, docs, code, etc.)
- Evidence-based assessment
- Automated validation scripts
- Remediation tracking

---

### `/standards-sync`
**Location**: `skills/standards-sync/`

Orchestrate synchronization between external best practices (OWASP, PRISMA, ISO, Anthropic docs) and internal standards.

**Pattern**: Continuous improvement cycle (Monitor → Evaluate → Update → Migrate → Measure).

**Use when**: Quarterly sync cycles, after external updates, when standards feel outdated.

**Key features**:
- Tracks external authoritative sources
- Two-way flow (external informs internal, learnings feed back)
- Migration assistance
- Trend measurement

---

## Installation

These skills are automatically available after installing the context-system plugin:

```bash
# Add marketplace
/plugin marketplace add bcbeidel/context-system

# Install plugin (via Discover tab)
/plugin

# Verify installation
/auditor --help
```

---

## Skill Categories

**Context Management**: context-curator
**Research & Planning**: researcher, planner
**Meta-Skills**: auditor, standards-sync (operationalize patterns)

---

## Documentation

Each skill includes:
- **SKILL.md** - Complete documentation
- **Quick Start** - Get started in minutes
- **Reference** - Detailed phase-by-phase instructions
- **Examples** - Real-world usage patterns

See individual skill directories for detailed docs.

---

## Why These Skills?

These are **universally useful** tools, not personal workflows:
- ✅ Grounded in standards (ISO 19011, PRISMA 2020, OWASP)
- ✅ Configurable for your context
- ✅ Demonstrated through production use
- ✅ Well-documented with clear "When to Use"

**All skills are grounded in standards**: See [Standards & Sources](../../docs/standards-sources.md) for external authority mapping
