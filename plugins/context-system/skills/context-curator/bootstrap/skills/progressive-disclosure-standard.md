---
title: Progressive Disclosure Standard
created: 2026-02-08
updated: 2026-02-08
tags: [context, skills, standards, anthropic]
type: project
---

# Progressive Disclosure Standard

## Summary

All Claude Code skills must follow Anthropic's progressive disclosure pattern: main SKILL.md <400 lines with detailed content in references/ directory. This improves discoverability, agent performance, and maintainability.

## Standards Source

**Authority**: [Anthropic Skill Best Practices - Progressive Disclosure](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

> "Start with a clear, concise overview. Provide details progressively as needed."

## Details

### Line Count Thresholds

Based on Q1 2026 refactoring of 7 skills:

- **Ideal**: 200-300 lines (sweet spot for readability)
- **Acceptable**: <400 lines (compliant with Anthropic guidance)
- **Watch**: >300 lines (monitor for growth)
- **Proactive action**: >400 lines (schedule refactoring)
- **Violation**: >500 lines (immediate refactoring required)

### Main SKILL.md Structure

```markdown
---
frontmatter (name, description, allowed-tools)
---

# Title

## Overview (what, when, why)
Brief 2-3 paragraphs

## Quick Start
Minimal commands to get started

## Core Workflow
High-level phases with links to references/

Phase 1: Brief description
**See**: [Phase 1 Guide](./references/phases/phase-1.md)

Phase 2: Brief description
**See**: [Phase 2 Guide](./references/phases/phase-2.md)

## Reference Documentation
- Links to all detailed guides

## Standards Grounding
- Links to external authorities

## Related Skills
- Integration points
```

### references/ Directory Structure

```
skill-name/
├── SKILL.md (<400 lines)
└── references/
    ├── phases/              # Detailed phase guides
    │   ├── phase-1-[name].md
    │   ├── phase-2-[name].md
    │   └── phase-3-[name].md
    ├── domains/ or templates/  # Domain-specific content
    │   ├── [domain-1].md
    │   └── [domain-2].md
    ├── [specific-guide].md    # Focused guidance
    └── troubleshooting.md     # Edge cases
```

## Examples

### Example: init-context-system Refactoring

**Before**: 1707 lines (single monolithic file)

**After**: 260 lines main + 13 reference files
- references/discovery-questions.md
- references/phases/ (3 detailed guides)
- references/primers/ (3 primer templates)
- references/domains/ (7 domain templates)
- references/troubleshooting.md

**Result**: 85% reduction in main file, all functionality preserved

### Example: context-update Refactoring

**Before**: 687 lines

**After**: 434 lines main + 5 reference files
- references/discovery-algorithm.md
- references/extraction-patterns.md
- references/quality-standards.md
- references/edge-cases.md
- references/file-operations.md

**Result**: 37% reduction, includes comprehensive inline examples

## Related Context

- [[skills/structure-standard]] - SKILL.md template requirements
- [[skills/reference-organization]] - How to organize references/ directory
- [[skills/refactoring-workflow]] - Process for refactoring large skills
- [[skills/discoverability-requirements]] - Ensuring skills expose tenets

## Notes

**Benefits of progressive disclosure**:
- ✅ Improved discoverability (overview vs monolith)
- ✅ Better agent performance (smaller files load faster)
- ✅ Easier maintenance (logical separation of concerns)
- ✅ Standards compliance (follows Anthropic best practices)
- ✅ Reduced cognitive load (progressive detail revelation)

**When to refactor**:
- Proactively when skill exceeds 400 lines
- During skill audits
- When adding significant new functionality
- When skills become hard to navigate

---

*Last updated: 2026-02-08*
*Evidence: Refactored 7 skills in context-system plugin Q1 2026*
