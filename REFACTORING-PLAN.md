# Skill Refactoring Plan

**Goal**: Ensure all skills follow Anthropic's progressive disclosure best practice (<400 lines main file).

**Authority**: [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

---

## Violations

| Skill | Current Lines | Target | Overage | Priority |
|-------|--------------|--------|---------|----------|
| init-context-system | 1707 | <400 | 1307 lines | 🔴 CRITICAL |
| context-update | 687 | <400 | 287 lines | 🔴 HIGH |
| audit | 390 | <400 | -10 lines | 🟡 MINOR |
| standards-sync | 389 | <400 | -11 lines | 🟡 MINOR |
| compare | 387 | <400 | -13 lines | 🟡 MINOR |
| systematic-review | 310 | <400 | ✅ | ✅ COMPLIANT |
| diagram | 163 | <400 | ✅ | ✅ COMPLIANT |

---

## Refactoring Strategy

### Pattern: Progressive Disclosure

**Main SKILL.md** (<400 lines):
```
---
frontmatter
---

# Title

## Overview
- What this skill does
- When to use it
- Core principle/pattern

## Quick Start
- Minimal steps to get started

## Core Workflow
- Phase 1: ...
- Phase 2: ...
- Phase 3: ...

## Reference Documentation
- [Detailed Phase Guides](./references/phases/)
- [Templates & Examples](./references/templates/)
- [Troubleshooting](./references/troubleshooting.md)
```

**references/** directory:
- `/phases/` - Detailed phase-by-phase instructions
- `/templates/` - File templates and examples
- `/domains/` - Domain-specific content
- `/troubleshooting.md` - Edge cases and solutions
- `/examples.md` - Real-world usage patterns

---

## 1. init-context-system (1707 → <400 lines)

**Current structure** (single 1707-line file):
- Core principle explanation
- Pre-flight checks
- Discovery questions (6 questions with mapping logic)
- Phase 1: Create structure (200+ lines of templates)
- Phase 2: Populate domains (300+ lines)
- Phase 3: Evolution framework (200+ lines)
- Main index template (100+ lines)
- Domain-specific templates (Python, Security, Research, Skills, Learning - 500+ lines)

**Proposed structure**:

**SKILL.md** (target: 300 lines):
```
---
frontmatter
---

# Context System Setup

## Overview
- Discovery-driven setup
- Concept-based organization
- Grounded in Anthropic best practices

## Quick Start
```bash
/init-context-system              # Full guided setup
/init-context-system --phase 2    # Resume at phase 2
```

## Core Workflow

### Phase 1: Discovery & Structure (15-20 min)
1. Ask discovery questions → [Question Guide](./references/discovery-questions.md)
2. Map to relevant domains → [Domain Mapping](./references/domain-mapping.md)
3. Create folder structure → [Structure Template](./references/structure-template.md)

### Phase 2: Populate Core Domains (20-30 min)
1. Create context-system/ primer → [Primer Templates](./references/primers/)
2. Create communication/ domain → [Communication Template](./references/domains/communication.md)
3. Create decisions/ domain → [Decisions Template](./references/domains/decisions.md)

### Phase 3: Evolution Framework (10-15 min)
1. Create maintenance schedule → [Maintenance Guide](./references/maintenance.md)
2. Set up loading map → [Loading Map Template](./references/loading-map-template.md)
3. Validate structure → [Validation Checklist](./references/validation.md)

## Domain Templates

User-specific domains created based on discovery:
- [Python Domain](./references/domains/python.md)
- [Security Domain](./references/domains/security.md)
- [Research Domain](./references/domains/research.md)
- [Skills Domain](./references/domains/skills.md)
- [Learning Domain](./references/domains/learning.md)

## Troubleshooting

See [Troubleshooting Guide](./references/troubleshooting.md) for:
- Existing context/ directory handling
- Migration from type-based to concept-based
- Custom domain creation

## Related Skills

- `/context-update` - Extract and update context regularly
- `/audit` - Validate context quality
```

**references/** structure:
```
init-context-system/
├── SKILL.md (300 lines)
└── references/
    ├── discovery-questions.md      # 6 discovery questions + mapping logic
    ├── domain-mapping.md            # How responses map to domains
    ├── structure-template.md        # Folder structure creation
    ├── phases/
    │   ├── phase-1-discovery.md     # Detailed Phase 1 guide
    │   ├── phase-2-populate.md      # Detailed Phase 2 guide
    │   └── phase-3-evolution.md     # Detailed Phase 3 guide
    ├── primers/
    │   ├── what-is-context.md       # Template
    │   ├── organizing-principles.md # Template
    │   └── quality-standards.md     # Template
    ├── domains/
    │   ├── communication.md         # Communication domain template
    │   ├── decisions.md             # Decisions domain template
    │   ├── python.md                # Python domain template
    │   ├── security.md              # Security domain template
    │   ├── research.md              # Research domain template
    │   ├── skills.md                # Skills domain template
    │   └── learning.md              # Learning domain template
    ├── loading-map-template.md      # Task-to-domain mappings
    ├── maintenance.md               # Maintenance schedule
    ├── validation.md                # Quality checklist
    └── troubleshooting.md           # Edge cases, migration

Extracted: ~1400 lines to references/
Remaining: ~300 lines in SKILL.md
```

---

## 2. context-update (687 → <400 lines)

**Current structure**:
- Core principle explanation (50 lines)
- Phase 1: Discover context structure (50 lines)
- Phase 2: Extract context (150 lines)
- Phase 3: Update context files (200 lines)
- Phase 4: Validate quality (100 lines)
- Phase 5: Optional maintenance (50 lines)
- Domain discovery algorithm (50 lines)
- Context extraction patterns (100 lines)
- Quality standards (50 lines)
- Edge cases (100 lines)

**Proposed structure**:

**SKILL.md** (target: 350 lines):
```
---
frontmatter
---

# Context Update

## Overview
- Domain-agnostic extraction
- Discovers YOUR domains dynamically
- Validates quality after updates

## Quick Start
```bash
/context-update    # Extract from current conversation
```

## Core Workflow

### Phase 1: Discover Structure
Read context/_index.md to discover user's domains → [Discovery Algorithm](./references/discovery-algorithm.md)

### Phase 2: Extract Context
Identify patterns → [Extraction Patterns](./references/extraction-patterns.md)
Map to domains → [Domain Mapping](./references/domain-mapping.md)

### Phase 3: Update Files
Create or update files → [File Operations](./references/file-operations.md)
Update indexes → [Index Management](./references/index-management.md)

### Phase 4: Validate Quality
Run validation checks → [Validation Guide](./references/validation.md)
Report results

### Phase 5: Maintenance (Optional)
Check for standards sync needs → [Maintenance Guide](./references/maintenance.md)

## Reference Documentation
- [Extraction Patterns](./references/extraction-patterns.md) - 4 pattern types
- [Quality Standards](./references/quality-standards.md) - What makes good context
- [Edge Cases](./references/edge-cases.md) - Handling conflicts, unclear domains
- [Examples](./references/examples.md) - Real extraction examples
```

**references/** structure:
```
context-update/
├── SKILL.md (350 lines)
└── references/
    ├── discovery-algorithm.md      # How to discover domains dynamically
    ├── extraction-patterns.md      # 4 patterns: preference, standard, decision, workflow
    ├── domain-mapping.md           # Map context to appropriate domain
    ├── file-operations.md          # Create/update operations with templates
    ├── index-management.md         # Updating _index.md, loading-map.md
    ├── validation.md               # Quality checks (frontmatter, links, size)
    ├── quality-standards.md        # What makes good context extraction
    ├── edge-cases.md               # Unclear domain, conflicts, too much context
    ├── maintenance.md              # When to run standards-sync, split files
    └── examples.md                 # Real extraction examples

Extracted: ~350 lines to references/
Remaining: ~350 lines in SKILL.md
```

---

## 3. audit (390 → <350 lines)

**Minor refactoring** - Already has audit-setup-guide.md and audit-types.md, just move them to references/.

**Action**:
```bash
mkdir audit/references/
mv audit/audit-setup-guide.md audit/references/setup-guide.md
mv audit/audit-types.md audit/references/audit-types.md
```

Update SKILL.md to reference these files, trim to <350 lines.

---

## 4. standards-sync (389 → <350 lines)

**Minor refactoring** - Extract detailed sections to references/.

**references/** structure:
```
standards-sync/
├── SKILL.md (300 lines)
└── references/
    ├── authorities.md       # List of tracked authorities by domain
    ├── evaluation.md        # How to evaluate relevance
    ├── migration.md         # Migration patterns
    └── registry-format.md   # Registry file format
```

---

## 5. compare (387 → <350 lines)

**Minor refactoring** - Extract examples and detailed scoring to references/.

**references/** structure:
```
compare/
├── SKILL.md (300 lines)
└── references/
    ├── examples.md          # Real decision matrix examples
    ├── criteria-library.md  # Common criteria patterns
    └── scoring-guide.md     # How to score objectively
```

---

## Implementation Order

1. **init-context-system** (Priority: CRITICAL)
   - Most over limit (1307 lines over)
   - Foundation skill that creates structure

2. **context-update** (Priority: HIGH)
   - Significantly over limit (287 lines over)
   - Maintenance skill used regularly

3. **audit, standards-sync, compare** (Priority: MINOR)
   - Close to threshold but not critical
   - Quick wins with minor extraction

---

## Success Criteria

✅ All skills <400 lines in main SKILL.md
✅ references/ directory with clear organization
✅ Main file has overview + workflow + links to details
✅ No functionality lost, just reorganized
✅ Follows Anthropic's progressive disclosure pattern

---

**Ready to implement?**
