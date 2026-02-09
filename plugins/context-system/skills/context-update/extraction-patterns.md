# Context Extraction Patterns

## From Conversations

**Look for:**
- Explicit preferences ("I prefer...", "Always...")
- Corrections ("Actually, it should be...", "Don't do...")
- Repeated patterns (same request multiple times)
- Decisions with rationale ("We chose X because...")
- Clarifications ("To be clear...", "What I mean is...")

**Examples:**
```
User: "I prefer you don't use emojis in commit messages"
→ Communication preference

User: "Always read the template first before creating notes"
→ Workflow pattern

User: "We decided to use lowercase tags for consistency"
→ Decision with rationale
```

## From Git Changes

**Look for:**
- New conventions in committed files
- Structural changes (folders, organization)
- Template updates
- Documentation additions
- Repeated patterns across commits

**Check:**
```bash
# Recent commits
git log -10 --oneline

# Changes in key areas
git diff HEAD~5 CLAUDE.md
git diff HEAD~5 context/
git diff HEAD~5 .claude/skills/
git diff HEAD~5 extras/templates/
```

## From Patterns

**Identify:**
- How tasks are broken down
- How decisions are made
- How quality is verified
- How documentation is structured
- How errors are handled
