**Create `context/context-system/organizing-principles.md`**:
```markdown
---
title: Organizing Principles
created: [YYYY-MM-DD]
keywords: [organization, anthropic, concept-based, flat-structure]
applies-to: [context-maintenance, adding-domains]
tags: [context, context-system]
---

# Context Organizing Principles

## Summary

This context system follows [Anthropic's best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices): organize by **concept (topic)**, not document type. Keep structure shallow (max 2 levels).

## Standards Source

**Authority**: [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#1-skill-structure--best-practices) for complete mapping.

## Core Principles

### 1. Concept-Based Organization

**Anthropic guidance**: "Organize by topic/purpose, not document type"

**This means**:
- ❌ **Not**: `context/standards/` (type-based)
- ✅ **Instead**: `context/python/`, `context/security/` (topic-based)

**Why it works**: LLMs can instantly find relevant context
- "Need Python conventions?" → `context/python/`
- "Need security standards?" → `context/security/`
- "Need communication preferences?" → `context/communication/`

**Bad (type-based)**:
```
context/
├── standards/
│   ├── python-standards.md
│   ├── security-standards.md
│   └── skill-standards.md
└── preferences/
    ├── communication-prefs.md
    └── workflow-prefs.md
```
→ Problem: Where's Python? In standards/ or preferences/? Hard to find.

**Good (concept-based)**:
```
context/
├── python/              # All Python-related
│   ├── coding-conventions.md
│   └── error-handling.md
├── security/            # All security-related
│   └── best-practices.md
└── communication/       # All communication-related
    └── style-preferences.md
```
→ Clear: Everything about Python is in python/

### 2. Flat Structure (Max 2 Levels)

**Anthropic guidance**: "Keep directory structure shallow"

**Structure**:
```
context/
├── domain/_index.md         # Level 1: Domain index
└── domain/file.md           # Level 2: Topic file
```

**Why 2 levels maximum**:
- ✅ Easy navigation
- ✅ Clear hierarchy
- ✅ Fast to scan
- ❌ Deep nesting (3+) is hard to discover

**If domain gets large**: Use overview + focused files pattern
```
context/python/
├── _index.md                  # Overview + links
├── coding-conventions.md      # Focused on conventions
├── error-handling.md          # Focused on errors
└── type-hints.md              # Focused on types
```

### 3. Clear Entry Points

**Anthropic guidance**: "Provide index files with 'When to Use' guidance"

**Every domain has `_index.md`**:
```markdown
# Domain Name

## When to Use

Load this domain when:
- [Trigger 1]
- [Trigger 2]

## Files

- file1.md - Description
- file2.md - Description

## External Authorities

Grounded in:
- [Standard name]: [URL]
```

**Why**: Claude knows when to load each domain

### 4. Task-Based Loading

**How it works**:
1. User works on task (e.g., "Write Python code")
2. Claude checks `context/context-system/loading-map.md`
3. Loading map says: "Python development → Load context/python/, context/security/"
4. Claude loads only relevant domains

**Why**: Efficient context loading, not everything at once

## Your Domains

[List user's specific domains created during setup]

Core (everyone):
- communication/ - How you prefer to work
- decisions/ - Architectural decisions
- context-system/ - This meta documentation

Your domains:
[Generated based on Phase 1 discovery]

## When to Add New Domains

Add a new domain when:
- Work expands into new topic area
- Multiple files would fit the topic
- Topic has external authority to ground in

**Process**:
1. Create `context/new-domain/_index.md`
2. Add "When to Use" guidance
3. Create initial files
4. Update `context/_index.md`
5. Update `context/context-system/loading-map.md`

## Related Context

- [[context/context-system/what-is-context]] - What belongs in context
- [[context/context-system/quality-standards]] - Quality guidelines
- [[context/context-system/loading-map]] - Task mappings

---

*Last updated: [YYYY-MM-DD]*
