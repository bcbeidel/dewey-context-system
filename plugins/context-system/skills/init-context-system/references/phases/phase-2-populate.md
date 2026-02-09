## Phase 2: Populate Core Domains (20-30 min)

**Goal**: Create initial context files in each domain with relevant standards.

### Step 2.1: Create Communication Domain

**Create `context/communication/_index.md`**:
```markdown
---
title: Communication Preferences
type: index
created: [YYYY-MM-DD]
---

# Communication Domain

How Claude should interact and communicate.

## When to Use

Load this domain when:
- Starting any conversation
- User asks for review or feedback
- Planning significant work

## Files

- style-preferences.md - Communication style and workflow patterns

## External Authorities

This domain implements patterns from:
- Anthropic Prompt Engineering: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering

---

*Created: [YYYY-MM-DD]*
```

**Extract communication preference** from Phase 1 answers:
```markdown
---
title: Communication Style Preferences
created: [YYYY-MM-DD]
keywords: [communication, style, workflow]
applies-to: [all-tasks]
tags: [context, communication]
---

# Communication Style Preferences

## Summary

[Based on user's answer to Question 6, e.g., "Review-first workflow: propose plans before executing"]

## Details

### Workflow Pattern

**Preference**: [Review-first/Action-first/Balanced]

**In practice**:
[Specific guidance based on their choice]

## Examples

**Good**:
```
[Example following their preference]
```

**Avoid**:
```
[Example not following their preference]
```

## Related Context

- [[context/communication/_index]]

---

*Last updated: [YYYY-MM-DD]*
```

### Step 2.2: Create Domain-Specific Content

For each user domain, create `_index.md` and initial content:

#### If Python Domain Selected:

**Create `context/python/_index.md`**:
```markdown
---
title: Python Standards
type: index
created: [YYYY-MM-DD]
---

# Python Domain

Python coding conventions and best practices.

## When to Use

Load this domain when:
- Writing Python code
- Developing Python-based Claude Code skills
- Reviewing Python code

## Files

- coding-conventions.md - PEP 8 compliance, style guide

## External Authorities

Grounded in:
- PEP 8: https://peps.python.org/pep-0008/
- PEP 484 (Type Hints): https://peps.python.org/pep-0484/

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#5-python-conventions) for complete mapping.

---

*Created: [YYYY-MM-DD]*
```

**Create `context/python/coding-conventions.md`**:
```markdown
---
title: Python Coding Conventions
created: [YYYY-MM-DD]
keywords: [python, pep8, style, conventions]
applies-to: [python-development, code-review]
tags: [context, python]
---

# Python Coding Conventions

## Summary

Python code follows PEP 8 style guide with type hints (PEP 484).

## Standards Source

**Authority**: [PEP 8](https://peps.python.org/pep-0008/)

## Key Conventions

### Code Layout
- 4 spaces per indentation level (no tabs)
- Maximum line length: 79 characters (code), 72 (docstrings)
- 2 blank lines between top-level functions/classes
- 1 blank line between methods

### Naming
- `snake_case` for functions and variables
- `PascalCase` for classes
- `UPPER_CASE` for constants
- Private: prefix with `_` (single underscore)

### Imports
```python
# Standard library
import os
import sys

# Third-party
import requests
import numpy as np

# Local
from myproject import module
```

### Type Hints (PEP 484)
```python
def greeting(name: str) -> str:
    return f"Hello, {name}"
```

## Related Context

- [[context/python/_index]]
- [[context/security/best-practices]] (if security domain exists)

---

*Last updated: [YYYY-MM-DD]*
```

#### If Security Domain Selected:

**Create `context/security/_index.md`**:
```markdown
---
title: Security Standards
type: index
created: [YYYY-MM-DD]
---

# Security Domain

Security best practices grounded in OWASP and OAuth 2.1 standards.

## When to Use

Load this domain when:
- Developing production applications
- Handling credentials or sensitive data
- Implementing authentication/authorization
- Reviewing code for security issues

## Files

- best-practices.md - OWASP Top 10 compliance

## External Authorities

Grounded in:
- OWASP Top 10 (2025): https://owasp.org/www-project-top-ten/
- OAuth 2.1: https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#3-security-standards) for complete mapping.

---

*Created: [YYYY-MM-DD]*
```

**Create `context/security/best-practices.md`**:
```markdown
---
title: Security Best Practices
created: [YYYY-MM-DD]
keywords: [security, owasp, credentials, authentication]
applies-to: [development, code-review, production]
tags: [context, security]
---

# Security Best Practices

## Summary

Security practices grounded in OWASP Top 10 (2025) standards.

## Standards Source

**Authority**: [OWASP Top 10](https://owasp.org/www-project-top-ten/)

## Key Principles

### A02: Cryptographic Failures
**Requirement**: Protect sensitive data in transit and at rest

**In practice**:
- Store credentials in OS keychain (never plaintext)
- Use HTTPS for all API calls
- Encrypt sensitive data at rest

**Example**:
```python
# ✓ Good: OS keychain
import keyring
token = keyring.get_password("app", "api_token")

# ✗ Bad: Plaintext .env
token = os.getenv("API_TOKEN")  # Avoid
```

### A04: Insecure Design
**Requirement**: Fail-closed validation

**In practice**:
- Explicit permission checks (hard fail if unclear)
- Validate all inputs
- Secure defaults

### A09: Security Logging Failures
**Requirement**: SIEM-ready logging

**In practice**:
- JSON structured logs
- Sanitize sensitive data from logs
- Include context (timestamp, user, action)

## Related Context

- [[context/security/_index]]
- [[context/python/coding-conventions]] (if Python domain exists)

---

*Last updated: [YYYY-MM-DD]*
```

#### If Skills Domain Selected:

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

*Last updated: [YYYY-MM-DD]*
```

### Step 2.3: Create Context System Meta Documentation

**IMPORTANT**: This domain provides foundational guidance about context management itself. Always create all primer files.

**Create `context/context-system/_index.md`**:
```markdown
---
title: Context System Meta
type: index
created: [YYYY-MM-DD]
---

# Context System Domain

Meta documentation about the context system itself.

## When to Use

Load this domain when:
- Maintaining the context system
- Adding new domains
- Understanding the architecture

## Files

- what-is-context.md - Primer on what belongs in context
- organizing-principles.md - Concept-based organization rationale
- quality-standards.md - What makes good context
- loading-map.md - Task-to-domain mappings
- maintenance.md - How to maintain the system

## Architecture

This context system follows Anthropic's best practices:
- **Concept-based organization**: By topic (python, security), not type (standards, workflows)
- **Flat structure**: Max 2 levels (domain/_index.md, domain/file.md)
- **Clear entry points**: Every domain has _index.md with "When to Use"

See: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices

---

*Created: [YYYY-MM-DD]*
```

**Create `context/context-system/what-is-context.md`**:
```markdown
---
title: What Is Context?
created: [YYYY-MM-DD]
keywords: [context-management, boundaries, primer]
applies-to: [all-tasks]
tags: [context, context-system]
---

# What Is Context?

## Summary

Context is **instructions for how Claude should work with you**. It's what you'd need to re-explain to Claude in a new conversation.

## Context Is

✅ **Preferences** - How you like to work
- "I prefer review-first workflow"
- "Avoid using emojis in responses"
- "Explain reasoning before executing"

✅ **Standards** - Quality and conventions you follow
- "Python code follows PEP 8"
- "Store credentials in OS keychain (OWASP A02)"
- "Skills must be <400 lines (Anthropic best practices)"

✅ **Decisions** - Choices with rationale
- "Use flat folder structure because it scales to 100+ files"
- "Chose OAuth 2.1 over basic auth for API security"
- "Organize by concept (topic) not type, per Anthropic guidance"

✅ **Domain Knowledge** - Topic-specific expertise
- Python conventions you follow
- Security practices you apply
- Research methods you use

## Context Is NOT

❌ **Public Documentation** - Use README, docs/ folder
❌ **General Knowledge** - Use wiki, learning resources
❌ **Project Planning** - Use project management tools
❌ **Code/Implementation** - Use source files
❌ **One-Off Instructions** - Just tell Claude directly

## Rule of Thumb

**If you'd need to re-explain it to Claude in a new conversation**, it's context.

**If it's for other humans or external audiences**, it's not.

## Examples

### ✅ Good Context

**Example 1**: Communication preference
```markdown
# Review-First Workflow

When proposing changes:
1. Explain what you'll do
2. Wait for approval
3. Execute after confirmation

Never: Execute without explaining first
```
→ **Why**: Repeated pattern Claude needs to follow

**Example 2**: Technical standard
```markdown
# Credential Storage

Store credentials in OS keychain (OWASP A02).

**Good**:
```python
import keyring
token = keyring.get_password("app", "token")
```

**Avoid**:
```python
token = os.getenv("TOKEN")  # Plaintext
```

**Authority**: OWASP Top 10 A02 (Cryptographic Failures)
```
→ **Why**: Security standard grounded in external authority

### ❌ Not Context

**Example 1**: Public README
```markdown
# MyProject

This project does X, Y, Z...
Installation: npm install...
```
→ **Why**: For external users, not Claude instructions

**Example 2**: One-off instruction
```markdown
# Fix Bug in Line 42

Change `x = 5` to `x = 10`
```
→ **Why**: Specific task, not a reusable pattern

## Related Context

- [[context/context-system/organizing-principles]] - How to organize context
- [[context/context-system/quality-standards]] - What makes good context

---

*Last updated: [YYYY-MM-DD]*
```

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
```

**Create `context/context-system/quality-standards.md`**:
```markdown
---
title: Quality Standards
created: [YYYY-MM-DD]
keywords: [quality, standards, best-practices, validation]
applies-to: [context-creation, context-review]
tags: [context, context-system]
---

# Context Quality Standards

## Summary

Quality standards for context files ensure consistency, usability, and maintainability.

## All Context Files Must Have

### 1. Frontmatter

```yaml
---
title: [Clear, descriptive title]
created: [YYYY-MM-DD]
keywords: [keyword1, keyword2, keyword3]
applies-to: [task-type1, task-type2]
tags: [context, domain-name]
---
```

**Why**: Enables search, filtering, task-based loading

### 2. Summary Section

```markdown
## Summary

[One-paragraph overview of what this context provides]
```

**Why**: Quick understanding without reading full file

### 3. Standards Grounding (If Applicable)

```markdown
## Standards Source

**Authority**: [Standard Name]([URL])

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md) for complete mapping.
```

**Why**: Context grounded in external authorities is more credible

### 4. Examples

```markdown
## Examples

**Good**:
\```
[Example following this guidance]
\```

**Avoid**:
\```
[Example not following this guidance]
\```
```

**Why**: Concrete examples are more actionable than abstract guidance

### 5. Cross-References

```markdown
## Related Context

- [[context/domain/_index]]
- [[context/other-domain/related-file]]
```

**Why**: Helps navigate related context

## Good Context Is

### ✅ Specific and Actionable

**Good**: "Use snake_case for Python function names (PEP 8)"
**Bad**: "Use good naming conventions"

**Good**: "Store credentials in OS keychain, never plaintext files"
**Bad**: "Handle credentials securely"

### ✅ Evidence-Based

**Good**: Extracted from actual repeated patterns
**Bad**: "Might need this someday"

**Signal**: User says same thing 2+ times → Extract as context

### ✅ Includes Examples

**Good**: Shows good and bad examples with code
**Bad**: Only abstract description

### ✅ Grounded in Standards

**Good**: "Python follows PEP 8: https://peps.python.org/pep-0008/"
**Bad**: "Python should follow conventions" (which ones?)

**Good**: "Security follows OWASP Top 10 A02"
**Bad**: "Use security best practices"

### ✅ Right Level of Detail

**Good**: Specific enough to be actionable
- "Skills must be <400 lines (progressive disclosure)"
- "Review-first workflow: propose before executing"

**Bad**: Too vague to apply
- "Write good code"
- "Be helpful"

## Avoid

### ❌ Vague Guidance

"Write clean code" → What does "clean" mean?
"Use best practices" → Which practices?

**Fix**: Be specific with examples

### ❌ Obvious Information

"Use proper grammar" → Claude already does this
"Don't make mistakes" → Not actionable

**Fix**: Only document what differs from Claude's defaults

### ❌ Contradictory Context

Check for conflicts with existing context before adding new.

**Process**: Search existing files before creating new

### ❌ Stale Context

Context that's outdated or no longer applies.

**Fix**: Run `/context-curator` validation monthly, archive old content

### ❌ Hypothetical Context

"If we ever need to do X..." → Don't create until you actually do X

**Fix**: Extract context from real use, not imagined futures

## Size Thresholds

**File sizes**:
- ✓ Ideal: 100-300 lines
- ✓ Acceptable: <400 lines
- ⚠️ Consider splitting: >400 lines

**If file >400 lines**:
1. Create overview file (summary + links)
2. Extract focused topic files
3. Update cross-references
4. Update loading map

**Example**:
```
Before: context/python/conventions.md (500 lines)

After:
- context/python/_index.md (overview, 80 lines)
- context/python/coding-conventions.md (150 lines)
- context/python/error-handling.md (130 lines)
- context/python/type-hints.md (140 lines)
```

## Validation Checklist

Run these checks regularly (monthly):

**Structure**:
- [ ] All domains have _index.md
- [ ] All files have frontmatter
- [ ] No files >400 lines
- [ ] Max 2-level depth

**Content**:
- [ ] All files have summary section
- [ ] Standards grounded (where applicable)
- [ ] Examples included
- [ ] Cross-references present

**Links**:
- [ ] All wikilinks resolve
- [ ] Loading map references valid files
- [ ] No orphaned files

**Freshness**:
- [ ] No stale context (>6 months without update)
- [ ] Archived old decisions/retrospectives

**Use `/context-curator` with validation option to automate checks**

## Related Context

- [[context/context-system/what-is-context]] - What belongs in context
- [[context/context-system/organizing-principles]] - How to organize
- [[context/context-system/maintenance]] - Maintenance schedule

---

*Last updated: [YYYY-MM-DD]*
```

**Create `context/context-system/loading-map.md`**:
```markdown
---
title: Context Loading Map
created: [YYYY-MM-DD]
---

# Context Loading Map

Maps tasks to relevant domains for automatic context loading.

## Task Mappings

### General Communication
**Load**:
- context/communication/

**When**:
- Starting conversation
- User asks for review

---

[Add mappings for each user domain based on Phase 1 discovery]

[If Python domain]:
### Python Development
**Load**:
- context/python/
- context/security/ (if exists)

**When**:
- Writing Python code
- Reviewing Python code
- Developing Python-based skills

---

[If Security domain]:
### Security Review
**Load**:
- context/security/
- context/python/ (if exists)

**When**:
- Reviewing code for security
- Handling credentials
- Implementing authentication

---

[If Skills domain]:
### Skill Development
**Load**:
- context/skills/
- context/python/ (if exists)
- context/security/ (if exists)

**When**:
- Creating Claude Code skills
- Refactoring skills
- Reviewing skill quality

---

*Last updated: [YYYY-MM-DD]*
```

### Step 2.4: Create Main Context Index

**Create `context/_index.md`**:
```markdown
---
title: Context System Index
type: index
created: [YYYY-MM-DD]
---

# Context System Index

Context organized by **concept (topic)**, following [Anthropic's best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices).

**Principle**: "Organize by topic, not document type. Max 2-level depth."

**Total**: [N] domains

---

## How to Use This Index

**For Claude**:
1. Read task/question from user
2. Check loading map: [[context/context-system/loading-map]]
3. Load relevant domain _index.md files
4. Load specific files as needed

**For Humans**:
- Browse domains below
- Click domain _index for "When to Use" guidance
- See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md) for external authority mapping

---

## All Domains

### Core (Everyone)
- [[context/communication/_index|Communication]] - How Claude should interact
- [[context/decisions/_index|Decisions]] - Architectural decisions with rationale
- [[context/context-system/_index|Context System]] - Meta documentation

[Add user's specific domains based on Phase 1]

[If Python]:
### Development
- [[context/python/_index|Python]] - PEP 8 conventions, type hints

[If Security]:
- [[context/security/_index|Security]] - OWASP Top 10, OAuth 2.1

[If Skills]:
- [[context/skills/_index|Skills]] - Claude Code skill development

[If Research]:
### Research & Learning
- [[context/research/_index|Research]] - Research methods and synthesis

[If Learning]:
- [[context/learning/_index|Learning]] - Learning preferences and frameworks

---

## Standards Grounding

All domains anchored to external authorities:
- **Skills** → [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- **Python** → [PEP 8](https://peps.python.org/pep-0008/)
- **Security** → [OWASP](https://owasp.org/www-project-top-ten/), [OAuth 2.1](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11)

See complete mapping: https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md

---

*Created: [YYYY-MM-DD]*
```

### Step 2.5: Update or Create CLAUDE.md

Check if `.claude/CLAUDE.md` exists:
- If **exists**: Add section about context system
- If **not exists**: Create minimal CLAUDE.md

**If creating new CLAUDE.md**:
```markdown
# Project Context

This project uses a concept-based context management system following [Anthropic's best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices).

## Context System

Context organized by **topic** in `/context` folder:

[List user's domains with brief descriptions]

## How It Works

1. **Task-Based Loading**: Context loads automatically based on task type
   - See: [[context/context-system/loading-map]]

2. **Grounded in Standards**: All patterns anchored to external authorities
   - Skills → Anthropic docs
   - Python → PEP 8
   - Security → OWASP, OAuth 2.1
   - See: https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md

3. **Progressive Growth**: System starts small, grows based on real use

## Quick Reference

- [[context/_index]] - Domain overview
- [[context/context-system/loading-map]] - Task mappings

---

**Reference**: https://github.com/bcbeidel/context-system
```

### Step 2.6: Phase 2 Complete

Say:
```
✓ Phase 2 Complete!

Context system created with [N] domains:

Core:
  - communication/ - Your communication preferences
  - decisions/ - Architectural decisions
  - context-system/ - System documentation

[User domains]:
  - [domain 1]/ - [description]
  - [domain 2]/ - [description]

All domains grounded in external authorities (Anthropic, OWASP, PEP 8).

**Test it**: Try asking me to [relevant task for their domain], and I'll automatically load the right context.

Ready for Phase 3? (Evolution framework for long-term maintenance)

Options:
1. Continue to Phase 3 (15-20 min)
2. Pause here, resume with `/init-context-system --phase 3`
3. Stop here and start using the system
```

---

