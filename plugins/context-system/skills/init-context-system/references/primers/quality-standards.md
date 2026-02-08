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

**Fix**: Run `/context-update` validation monthly, archive old content

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

