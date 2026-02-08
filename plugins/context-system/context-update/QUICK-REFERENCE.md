# Context Update - Quick Reference

## When to Use

Use `/context-update` to periodically extract and update context from:
- Recent conversations
- Git changes
- Specific topics or areas
- Full context audits

## What It Does

1. **Reviews** conversations or changes
2. **Extracts** preferences, patterns, and decisions
3. **Categorizes** into appropriate context types
4. **Updates** context files, indexes, and related guidance
5. **Validates** consistency across all guidance locations
6. **Commits** changes with proper documentation

## Invocation

```bash
/context-update
```

The skill will ask you what to review:
- Recent conversation(s)
- Recent git changes
- Specific topic
- Full audit

## What Gets Updated

### Context Files (`context/`)
- Communication preferences
- Project knowledge and conventions
- Workflow patterns
- Decision logs
- Private context (git-ignored)

### Guidance Locations
- `CLAUDE.md` - Vault-wide instructions (if needed)
- `.claude/skills/` - Skill workflows (if affected)
- `extras/templates/` - Note templates (if changed)
- `context/_index.md` - Context index

## Output

You'll receive a summary of:
- New context files created
- Existing files updated
- Key insights extracted
- Cross-reference validation status

You can review before committing.

## Example Usage

### After Major Work
```
User: /context-update
Claude: What would you like me to review?
User: Our recent conversation about recipe organization
Claude: [Extracts decisions, patterns, preferences]
Claude: [Creates/updates context files]
Claude: [Shows summary for review]
```

### Weekly Review
```
User: /context-update
Claude: What would you like me to review?
User: Last week's git changes
Claude: [Reviews commits]
Claude: [Extracts patterns and conventions]
Claude: [Updates documentation]
```

### Full Audit
```
User: /context-update
Claude: What would you like me to review?
User: Full context audit
Claude: [Reviews all guidance locations]
Claude: [Identifies gaps and conflicts]
Claude: [Proposes updates]
```

## Categories

**Communication** - How Claude should communicate
- Style preferences
- Response formatting
- Terminology

**Project** - Project-specific knowledge
- Vault conventions
- Standards and patterns
- Architectural decisions

**Workflows** - How tasks are done
- Common processes
- Quality checks
- Decision patterns

**Decisions** - What was decided and why
- Problem/question
- Decision made
- Rationale and alternatives
- Implications

**Private** - Sensitive information (git-ignored)
- Work context
- Personal preferences
- Goals and plans

## Consistency Check

The skill ensures consistency across:
- ✅ CLAUDE.md (vault-wide)
- ✅ context/ (persistent context)
- ✅ .claude/skills/ (task workflows)
- ✅ extras/templates/ (note formats)

## Tips

- **Run after major work**: Capture decisions while fresh
- **Weekly light reviews**: Maintain current context
- **Monthly deep dives**: Comprehensive audits
- **Before big changes**: Baseline current state

## See Also

- [[context/_index]] - Context system overview
- [[context/project/context-governance]] - How to maintain context
- [[context/TEMPLATE]] - Context note template
- [[context/decisions/TEMPLATE-decision]] - Decision log template
