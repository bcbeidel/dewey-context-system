# File Operations

## Creating New Files

### Step 1: Determine Target Domain

Based on topic keywords:
- Python code → `python/`
- Security/credentials → `security/`
- Skill development → `skills/`
- Research methods → `research/`
- Communication style → `communication/`

If architectural decision → `decisions/`
If meta (about context system) → `context-system/`
If unclear → Ask user

### Step 2: Check if Domain Exists

```bash
Read: context/[domain]/_index.md

# If doesn't exist:
# User may need new domain - suggest creating it
```

### Step 3: Choose Action

**Create new file** (new topic in domain):
- Topic doesn't have existing file
- Distinct from other files in domain

**Update existing file** (add to existing topic):
- Topic already has a file
- Content complements existing guidance

**Create decision log** (architectural decision):
- Choice between alternatives
- Rationale provided
- Significant implications

### Step 4: Create or Update

**If creating new file in domain**:
```bash
# Read domain _index.md to understand structure
Read: context/[domain]/_index.md

# Read template if exists
Read: extras/templates/Template, [type].md

# Create new file following domain pattern
Write: context/[domain]/[descriptive-name].md
```

**Standard file structure**:
```markdown
---
title: [Title]
created: [YYYY-MM-DD]
keywords: [keyword1, keyword2]
applies-to: [task-type1, task-type2]
tags: [context, domain-name]
---

# [Title]

## Summary

[One-paragraph overview]

## Standards Source (if applicable)

**Authority**: [External standard with URL]

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md) for mapping.

## Details

[Specific guidance]

## Examples

**Good**:
```
[Example following this]
```

**Avoid**:
```
[Example not following this]
```

## Related Context

- [[context/domain/_index]]
- [[other related files]]

---

*Last updated: [YYYY-MM-DD]*
```

**If updating existing file**:
```bash
# Read current file
Read: context/[domain]/[file].md

# Add new content to appropriate section
Edit: context/[domain]/[file].md

# Update "Last updated" timestamp
```

**If creating decision log**:
```bash
# Read decision template
Read: extras/templates/Template, Decision.md

# Create with date prefix
Write: context/decisions/YYYY-MM-DD-[decision-name].md
```

Follow template structure with:
- Context (why needed)
- Decision (what chosen)
- Rationale (why chosen, pros/cons)
- Alternatives (what else considered)
- Consequences (implications)
- Standards grounding (if applicable)

---

## Updating Indexes

### Update Domain _index.md

**If new file created**:
```bash
Read: context/[domain]/_index.md
Edit: context/[domain]/_index.md
# Add new file to "Files" section
```

Example:
```markdown
## Files

- existing-file.md - Existing description
- new-file.md - New file description    # ADD THIS
```

### Update Main _index.md

**If new file represents significant new capability**:
```bash
Read: context/_index.md
Edit: context/_index.md
# Add cross-reference if needed
```

### Update Loading Map

**If new task mapping needed**:
```bash
Read: context/context-system/loading-map.md
Edit: context/context-system/loading-map.md
# Add or update task mapping
```

Example:
```markdown
**Python Development**:
- context/python/_index.md
- context/python/new-file.md    # ADD THIS if relevant to task
- context/security/best-practices.md
```

---

## Validation After Updates

After creating/updating files:

1. **Check frontmatter**:
   - All required fields present (title, created, keywords, applies-to, tags)
   - Date format correct (YYYY-MM-DD)

2. **Check links**:
   - All wikilinks resolve
   - External links valid

3. **Check size**:
   - If file >400 lines, warn user (suggest splitting)

4. **Check cross-references**:
   - Domain _index.md updated
   - Loading map updated if needed
   - Related Context section has bidirectional links

---

## Examples

### Example 1: Creating New File

**Extracted context**: "Use snake_case for Python functions (PEP 8)"

**Mapping**: Python code → `python/` domain

**Action**: Check if `context/python/coding-conventions.md` exists
- If yes → Update existing file
- If no → Create new file

**Result**:
```markdown
---
title: Python Coding Conventions
created: 2026-02-08
keywords: [python, pep8, conventions, style]
applies-to: [python-development]
tags: [context, python]
---

# Python Coding Conventions

## Summary

Python code follows PEP 8 style guide for consistency and readability.

## Standards Source

**Authority**: [PEP 8 - Style Guide for Python Code](https://peps.python.org/pep-0008/)

## Details

### Naming Conventions

**Functions and variables**: snake_case
```python
# Good
def calculate_total():
    user_count = 10

# Avoid
def calculateTotal():
    userCount = 10
```

## Related Context

- [[context/python/_index]]
- [[context/security/best-practices]]

---

*Last updated: 2026-02-08*
```

### Example 2: Updating Existing File

**Extracted context**: "Always validate inputs at API boundaries"

**Mapping**: Security → `security/` domain

**Action**: Read `context/security/best-practices.md`, add section

**Result**: New section added:
```markdown
### Input Validation

**OWASP A03:2025 - Injection Prevention**

Always validate inputs at system boundaries (user input, external APIs).

**Examples**:
```python
# Good - Validate at boundary
def create_user(name: str, email: str):
    validate_name(name)     # Validate first
    validate_email(email)
    # ... proceed with creation
```

### Example 3: Creating Decision Log

**Extracted context**: "Use flat folder structure with MOCs for navigation instead of nested folders because it scales better with 100+ files"

**Mapping**: Architectural decision → `decisions/`

**Action**: Create decision log

**Result**:
```markdown
---
title: Flat Folder Structure Decision
created: 2026-02-08
status: accepted
tags: [context, decisions, architecture]
---

# Flat Folder Structure with MOCs

## Context

With 100+ notes expected, need scalable navigation strategy.

## Decision

Use flat folder structure (context/domain/ only 1-2 levels) with Maps of Content (MOCs) for navigation, instead of deep nested folders.

## Rationale

**Pros**:
- Scales to 100+ files without deep nesting
- Easy to find files (fewer places to look)
- MOCs provide flexible navigation
- Avoids "where does this go?" decisions

**Cons**:
- Requires discipline to maintain MOCs
- Single folder can feel crowded

## Alternatives Considered

1. **Deep nesting** (3+ levels)
   - Rejected: Hard to discover, rigid categories

2. **Tag-only organization**
   - Rejected: Loses clear structure

## Consequences

- Must create _index.md for each domain (MOC pattern)
- Max 2-level depth enforced
- If domain grows >10 files, split by sub-topic

## Standards Source

**Authority**: [Anthropic Best Practices - Flat Structure](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

---

*Last updated: 2026-02-08*
```
