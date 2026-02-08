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

