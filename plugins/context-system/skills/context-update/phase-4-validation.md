# Phase 4: Validate & Commit

## Step 12: Cross-Reference Check

Verify consistency across all guidance locations:

**Checklist**:
- [ ] CLAUDE.md reflects vault-wide conventions
- [ ] Context files are properly categorized
- [ ] Indexes link to all context files
- [ ] Skills reference relevant context
- [ ] Templates match current standards
- [ ] No conflicting guidance exists
- [ ] Private context is git-ignored

## Step 13: Review with User

Present summary:
```
## Context Updates Summary

### New Context Files
- [context/communication/style-preferences.md] - Communication style guidelines
- [context/decisions/2026-01-25-decision.md] - Decision about X

### Updated Files
- [context/_index.md] - Added new entries
- [CLAUDE.md] - Updated vault structure
- [.claude/skills/recipe-scraper/SKILL.md] - Added context reference

### Key Changes
- Extracted preference: [description]
- Documented decision: [description]
- Updated convention: [description]

### Cross-Reference Validation
✅ All guidance locations consistent
✅ Indexes updated
✅ No conflicts detected
```

Ask user to review before committing.

## Step 14: Commit Changes

Create commit following git conventions:
```bash
git add context/ CLAUDE.md .claude/skills/ extras/templates/
git commit -m "docs(context): extract context from [source]

- Add [new context files]
- Update [modified files]
- Document [key insights]

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```
