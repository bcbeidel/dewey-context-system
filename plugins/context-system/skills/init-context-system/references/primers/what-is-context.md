
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

