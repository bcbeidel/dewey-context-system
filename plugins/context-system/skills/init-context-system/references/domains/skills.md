
**Create `context/skills/_index.md`**:
```markdown
---
title: Skill Development Standards
type: index
created: [YYYY-MM-DD]
---

# Skills Domain

Standards for developing Claude Code skills.

## When to Use

Load this domain when:
- Creating new Claude Code skills
- Refactoring existing skills
- Reviewing skill quality

## Files

- structure-standard.md - Progressive disclosure, max 2-level depth

## External Authorities

Grounded in:
- Anthropic Skill Best Practices: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#1-skill-structure--best-practices) for complete mapping.

---

*Created: [YYYY-MM-DD]*
```

**Create `context/skills/structure-standard.md`**:
```markdown
---
title: Skill Structure Standard
created: [YYYY-MM-DD]
keywords: [skills, progressive-disclosure, anthropic]
applies-to: [skill-development, skill-review]
tags: [context, skills]
---

# Skill Structure Standard

## Summary

Claude Code skills follow Anthropic's progressive disclosure pattern: main file <400 lines, details extracted to references/.

## Standards Source

**Authority**: [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

## Key Principles

### 1. Progressive Disclosure
> "Start with clear overview, provide details progressively"

**Size thresholds**:
- ✓ Ideal: 200-300 lines
- ✓ Acceptable: <400 lines
- ⚠️ Proactive refactor: >400 lines
- ❌ Violation: >500 lines

### 2. Flat Structure (Max 2 Levels)
> "Keep directory structure shallow"

**Structure**:
```
.claude/skills/skill-name/
├── SKILL.md              # Main file (<400 lines)
└── references/           # Optional details
    ├── setup.md
    └── examples.md
```

### 3. Clear Entry Points
> "Provide index with 'When to Use' guidance"

**SKILL.md must include**:
- name, description in frontmatter
- "When to Use" section
- Quick Start
- Phase-based instructions

## Related Context

- [[context/skills/_index]]

---

