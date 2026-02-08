# Context System Skills

These skills are included with the context-system plugin. Once installed, they're available globally across all your projects.

---

## Setup & Maintenance Skills

### `/init-context-system`
**Location**: `skills/init-context-system/`

Discovery-driven setup wizard that identifies YOUR key domains through guided questions.

**Pattern**: Concept-based organization grounded in [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

**Use when**: First-time setup, or setting up a new project.

**Key features**:
- Asks discovery questions (work type, languages, security needs)
- Maps to relevant domains (python, security, research, skills)
- Grounds domains in external authorities (PEP 8, OWASP, Anthropic)
- Creates personalized structure (not generic categories)

---

### `/context-update`
**Location**: `skills/context-update/`

Extract learnings from conversations and update your concept-based context system.

**Pattern**: Domain-agnostic extraction (discovers YOUR domains dynamically)

**Use when**: After significant work sessions, when you notice patterns worth capturing.

**Key features**:
- Discovers your domains from context/_index.md
- Works with ANY structure from init-context-system
- Maps context to appropriate domain by topic
- Validates quality after extraction

---

## Meta-Skills (Advanced Patterns)

### `/audit`
**Location**: `skills/audit/`

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

## Utility Skills

### `/compare`
**Location**: `skills/compare/`

Create weighted decision matrices for evaluating multiple options against defined criteria.

**Pattern**: Structured decision-making with explicit criteria and weighting.

**Use when**: Comparing technology choices, evaluating options, making trade-off decisions.

**Key features**:
- Define criteria with weights
- Score options systematically
- Automatic weighted score calculation
- Decision rationale capture

---

### `/diagram`
**Location**: `skills/diagram/`

Generate Mermaid diagrams from mental models, processes, and relationships for visual learning.

**Pattern**: Visual representation of complex concepts.

**Use when**: Explaining architecture, documenting processes, teaching concepts, visualizing workflows.

**Key features**:
- Supports flowcharts, sequence diagrams, class diagrams, etc.
- Natural language → Mermaid syntax
- Optimized for learning and documentation
- Integration with Obsidian and markdown

---

### `/systematic-review`
**Location**: `skills/systematic-review/`

Conduct PRISMA 2020 compliant systematic reviews with protocol registration, quality assessment, and publication-ready reporting.

**Pattern**: Academic rigor for research synthesis.

**Use when**: Literature reviews, thesis research, understanding research landscape, academic analysis.

**Key features**:
- PRISMA 2020 compliance
- Protocol registration guidance (PROSPERO)
- Quality assessment (AMSTAR-2, ROBIS)
- Methodology comparison
- Research gap identification

---

## Installation

These skills are automatically available after installing the context-system plugin:

```bash
# Add marketplace
/plugin marketplace add bcbeidel/context-system

# Install plugin (via Discover tab)
/plugin

# Verify installation
/audit --help
```

---

## Skill Categories

**Setup**: init-context-system, context-update
**Meta-Skills**: audit, standards-sync (operationalize patterns)
**Utilities**: compare, diagram, systematic-review (generally useful tools)

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
