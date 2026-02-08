---
name: context-update
description: "Extract context from conversations and update your concept-based context system"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Context Update

Extract learnings from conversations and update your concept-based context system.

**Key principle**: Works with YOUR domains (discovered dynamically), not generic categories.

**Grounded in**: [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) - "Organize by topic, not document type"

---

## Overview

This skill discovers your domains automatically by reading `context/_index.md`, then extracts context to the appropriate domain based on topic.

**Domain-agnostic**: No hardcoded folder names. Works with ANY structure from `/init-context-system`.

**When to use**:
- After completing major work sessions
- Monthly context reviews
- When you notice recurring patterns
- After making architectural decisions
- When context needs validation or cleanup

---

## Quick Start

```bash
/context-update    # Extract from current conversation
```

---

## Core Workflow

### Phase 1: Discover Context Structure (2 min)

**Goal**: Understand user's existing context organization.

**Process**:
1. Read `context/_index.md` to discover domains
2. For each domain, read `_index.md` to understand:
   - Domain purpose ("When to Use")
   - Existing files
   - External authorities
3. Store domain metadata for mapping

**See**: [Discovery Algorithm](./references/discovery-algorithm.md) for detailed logic.

**Validation**: If `context/` doesn't exist → Tell user to run `/init-context-system` first.

---

### Phase 2: Extract Context (5-10 min)

**Goal**: Identify patterns, preferences, and decisions worth capturing.

#### Step 2.1: Understand Scope

Ask user using AskUserQuestion:
```yaml
question: "What should I review to extract context?"
header: "Scope"
multiSelect: false
options:
  - label: "This conversation"
    description: "Extract from our current conversation"
  - label: "Recent work session"
    description: "Review recent commits and conversations"
  - label: "Specific topic"
    description: "Focus on a particular domain or topic"
  - label: "Full system audit"
    description: "Review entire context system for quality"
```

#### Step 2.2: Review Based on Scope

**If "This conversation"**:
- Review conversation history
- Identify patterns, preferences, decisions

**If "Recent work session"**:
```bash
git log -10 --oneline
git diff HEAD~5 context/
```
- Review changes to key files

**If "Specific topic"**:
- Ask which domain to focus on (from discovered domains)
- Review files in that domain

**If "Full system audit"**:
- Run validation checks (see Phase 4)

#### Step 2.3: Identify Extractable Context

Look for 4 pattern types → [Extraction Patterns](./references/extraction-patterns.md):

1. **Patterns** (repeated behaviors):
   - "I always prefer X..."
   - "Never do Y..."
   - "When doing Z, follow this pattern..."

2. **Decisions** (choices with rationale):
   - "We chose X because..."
   - "Decided to use Y instead of Z..."
   - "Changed approach from A to B..."

3. **Standards** (quality/security/code conventions):
   - "Follow PEP 8..."
   - "Use OWASP A02 for credentials..."
   - "Skills must be <400 lines..."

4. **Domain-Specific Knowledge**:
   - Python conventions discovered
   - Security practices applied
   - Research methods used
   - Tool preferences

#### Step 2.4: Map to Domains

For each extracted item, determine target domain using topic keywords:
- Python code → `python/`
- Security/credentials → `security/`
- Skill development → `skills/`
- Research methods → `research/`
- Communication style → `communication/`

If architectural decision → `decisions/`
If meta (about context system) → `context-system/`
If unclear → Ask user which domain

**See**: [Discovery Algorithm](./references/discovery-algorithm.md) for mapping logic.

#### Step 2.5: Present Findings

Say:
```
I identified [N] context items to extract:

[Domain 1] (e.g., python/):
  1. [Pattern 1] - Would add to python/coding-conventions.md
  2. [Pattern 2] - Would create python/error-handling.md

[Domain 2] (e.g., security/):
  1. [Security practice] - Would add to security/best-practices.md

decisions/:
  1. [Decision about X] - Would create decisions/YYYY-MM-DD-decision-name.md

Which should I extract?
```

Use AskUserQuestion for selection.

---

### Phase 3: Update Context Files (10-15 min)

**Goal**: Create or update files with extracted context.

**Process**: For each selected item:

1. **Determine action**:
   - Create new file (new topic in domain)
   - Update existing file (add to existing topic)
   - Create decision log (architectural decision)

2. **Execute file operations** → [File Operations Guide](./references/file-operations.md)

3. **Update indexes**:
   - Update domain `_index.md` (if new file)
   - Update main `context/_index.md` (if significant)
   - Update `context/context-system/loading-map.md` (if new task mapping)

**File structure standard**:
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

## Details
[Specific guidance]

## Examples
**Good**: [Example]
**Avoid**: [Counter-example]

## Related Context
- [[wikilinks to related files]]
```

**See**: [File Operations](./references/file-operations.md) for detailed templates and examples.

---

### Phase 4: Validate Quality (3-5 min)

**Goal**: Ensure extracted context meets quality standards.

#### Step 4.1: Run Validation Checks

**Structure validation**:
```bash
# Check all domains have _index.md
for domain in context/*/; do
  if [ ! -f "$domain/_index.md" ]; then
    echo "⚠️ Missing: $domain/_index.md"
  fi
done
```

**File validation**:
```bash
# Find files missing frontmatter
Grep: "^---" context/**/*.md
# Files without frontmatter = validation error
```

**Quality checklist** → [Quality Standards](./references/quality-standards.md):
- [ ] All context files have frontmatter
- [ ] All frontmatter has required fields (title, created, keywords, applies-to, tags)
- [ ] Files have summary section
- [ ] Standards grounding included (where applicable)
- ⚠️ Warn if file >400 lines (suggest splitting)

**Link validation**:
```bash
# Check wikilinks resolve
Glob: context/**/*.md
# For each file, extract [[wikilinks]] and verify target exists
```

**Checks**:
- [ ] All wikilinks in context files resolve
- [ ] Loading map references valid files
- [ ] Domain indexes list all files
- ⚠️ Warn about orphaned files (not referenced anywhere)

#### Step 4.2: Report Results

```
Context Update Summary
======================

✅ ADDED (N items)
- context/python/error-handling.md - Python error handling patterns
- context/security/best-practices.md - Updated with keychain storage
- context/decisions/2026-02-08-flat-structure.md - Decision log

✅ UPDATED (N files)
- context/communication/style-preferences.md - Added review-first preference
- context/_index.md - Added new files
- context/context-system/loading-map.md - Updated task mappings

✅ VALIDATION PASSED
- 12/12 files have frontmatter
- 0 broken wikilinks
- All domain indexes up to date

⚠️ WARNINGS (if any)
- context/python/conventions.md is 427 lines (consider splitting)

---

Next: Run `/context-update` after your next major work session
```

---

### Phase 5: Optional Maintenance Tasks (5 min)

**Goal**: Suggest proactive maintenance.

#### Check for Standards Sync Needs

If user has domains with external authorities (python, security, skills):
```
I notice you have domains with external authorities:
- python/ → PEP 8
- security/ → OWASP Top 10
- skills/ → Anthropic Best Practices

Would you like to sync with external standards?
Run `/standards-sync` to check for updates.
```

#### Check for Splitting Candidates

If files >400 lines:
```
The following files exceed the 400-line threshold:
- context/python/conventions.md (427 lines)

Would you like to apply progressive disclosure?
I can split into overview + focused files.
```

If user agrees:
1. Create overview file (summary + links)
2. Extract focused topic files
3. Update cross-references
4. Update loading map

---

## Reference Documentation

### Core Guides
- [Discovery Algorithm](./references/discovery-algorithm.md) - How to discover user's domains dynamically
- [Extraction Patterns](./references/extraction-patterns.md) - 4 types: Patterns, Decisions, Standards, Domain Knowledge
- [File Operations](./references/file-operations.md) - Creating/updating files with templates
- [Quality Standards](./references/quality-standards.md) - What makes good context extraction

### Edge Cases
- [Edge Cases Guide](./references/edge-cases.md) - Handling:
  - Unclear which domain
  - Domain doesn't exist yet
  - Conflicting context
  - Too much context

---

## Good Context Extraction

✅ **Specific and actionable**
```
Good: "Use snake_case for Python functions (PEP 8)"
Bad: "Follow Python conventions"
```

✅ **Includes examples**
```
Good:
  **Good**: `def calculate_total():`
  **Avoid**: `def calculateTotal():`
Bad: [no examples]
```

✅ **Grounds in external authority** (where applicable)
```
Good: "Authority: PEP 8 (https://peps.python.org/pep-0008/)"
Bad: [no source cited]
```

✅ **Cross-references related context**
```
Good: "Related: [[context/python/_index]], [[context/security/best-practices]]"
Bad: [no cross-references]
```

### Avoid

❌ **Vague guidance**: "Write good code"
❌ **Obvious information**: "Use proper grammar"
❌ **One-off situations**: "Fix bug in line 42" (not a pattern)
❌ **Hypothetical context**: "Might need this later"

**See**: [Quality Standards](./references/quality-standards.md) for complete criteria.

---

## Integration with Other Skills

### With /init-context-system
- Discovers structure created by init-context-system
- Works with whatever domains user chose
- Maintains same standards grounding

### With /standards-sync
- Identifies domains needing external sync
- Reminds user to run standards-sync quarterly
- Updates registry after sync

### With /audit
- Can trigger audit validation checks
- Uses same quality standards
- Identifies issues for audit to track

---

## Best Practices

### DO:
- ✅ Discover domains dynamically (read _index.md)
- ✅ Map context to appropriate domain based on topic
- ✅ Ground in external authorities where applicable
- ✅ Include examples in extracted context
- ✅ Update all relevant indexes and loading map
- ✅ Validate after extraction

### DON'T:
- ❌ Hardcode domain names (python, security, etc.)
- ❌ Assume type-based structure
- ❌ Extract vague or obvious patterns
- ❌ Skip validation checks
- ❌ Create context without user confirmation

---

## Remember

**This skill is domain-agnostic**: It works with YOUR domains (python, security, research, recipes, etc.), not generic categories.

**Grounded in standards**: Links to [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) and [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md).

**Progressive**: Extract context based on real use, not hypothetical needs.

---

**After extraction**: Run `/audit` quarterly to validate context quality systematically.

**Authority**: [Anthropic Best Practices - Concept-Based Organization](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

*Last updated: February 2026*
