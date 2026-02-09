# Phase 3: Update Context

## Step 6: Create or Update Context Files

**For new context notes:**
```bash
# Read template first
Read: extras/templates/Template, Context.md

# Create note following template structure
Write: context/[category]/[descriptive-name].md
```

**For decision logs:**
```bash
# Read decision template
Read: extras/templates/Template, Decision.md

# Create decision log with date prefix
Write: context/decisions/YYYY-MM-DD-decision-name.md
```

**For private context:**
```bash
# Save to git-ignored private folder
Write: context/private/[category]/[descriptive-name].md
```

**Context note structure:**
```yaml
---
title: Context Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
keywords: [keyword1, keyword2, keyword3]
applies-to: [task-type1, task-type2]
tags: [context, category]
type: [communication|project|workflow|decision|personal]
---

# Context Title

## Summary
Brief overview (1-2 sentences)

## Details
Specific guidelines, preferences, or patterns

## Examples
Concrete examples from actual usage

## Related Context
- Other Context Note
- Related Guidance

## Notes
Additional clarifications or edge cases

---

*Last updated: YYYY-MM-DD*
```

## Step 7: Update Indexes

**Update context/_index.md:**
- Add new context files to appropriate section
- Maintain clear organization (processes, standards, retrospectives)
- Update cross-references

**Update context/private/_index.md (if applicable):**
- Add private context files
- Keep structure consistent with public index

**Update context/_loading-map.md (if applicable):**
- Add new task types if workflows create them
- Map tasks to relevant context files
- Update "When" sections to trigger appropriate loading
- Ensure new context is discoverable by Claude

## Step 8: Update CLAUDE.md (if needed)

Check if CLAUDE.md needs updates for:
- Vault-wide conventions that changed
- New major sections or folders
- Updated workflows
- Critical guidelines

**Only update CLAUDE.md for vault-level guidance**, not specific preferences.

## Step 9: Update Skills (MANDATORY when applicable)

Skills should improve based on learnings. This is critical for closing the feedback loop.

**When to update a skill:**
- **Bug discovered** in skill execution → Fix it immediately
- **Better pattern identified** → Refactor skill to use it
- **Missing capability** → Add it to prevent future manual work
- **Quality issue** → Update validation checks
- **New standard established** → Ensure skill complies
- **Reusable workflow** → Consider creating new skill

**How to identify affected skills:**
```bash
# 1. Search for skills related to session topic
Glob: .claude/skills/*/SKILL.md

# 2. Grep for skills mentioning relevant keywords
Grep: pattern="topic-keyword" path=".claude/skills"

# 3. Review retrospectives for skill-specific issues
# Look for: "skill X failed", "missing workflow", "manual workaround"
```

**What to update in skills:**
- **Workflow steps**: Add validation, error handling, new phases
- **Context references**: Point to new standards/conventions
- **Quality checks**: Implement new quality gates
- **Integration points**: Use newly created skills/tools
- **Documentation**: Update examples, edge cases, limitations

**Create new skills when:**
- Pattern is reusable across contexts (e.g., "safe-move" for file moves)
- Manual workflow could be automated (e.g., "wikilink-fixer")
- Quality issues need systematic prevention
- Multiple retrospectives mention same gap

**Example skill improvements from retrospectives:**
```markdown
Retro: "Broken wikilinks after moving files"
→ Action: Create /safe-move skill OR update file-moving skills to validate links

Retro: "Skills hardcode formats instead of reading templates"
→ Action: Update all note-creation skills to read template first

Retro: "No validation checkpoints during documentation creation"
→ Action: Add 20% preview step to documentation skills
```

**Skill update checklist:**
- [ ] Read affected skill SKILL.md files
- [ ] Identify specific improvements needed
- [ ] Update skill workflows/validation
- [ ] Add references to new context
- [ ] Test changes conceptually (does logic make sense?)
- [ ] Document what was changed and why

## Step 10: Update Templates (if applicable)

Check if templates need updates:
- Frontmatter fields changed
- Structure evolved
- New conventions added

## Step 11: Consider Archival (if applicable)

**Check for archival candidates:**
- Decisions older than 3 months that are superseded or deprecated
- Retrospectives older than 3 months (after extracting learnings)
- Context files no longer relevant

**See [[context-system/context-archival-strategy]] for complete guidelines:**
- When to archive decisions and retrospectives
- Step-by-step archival process
- Archive directory structure (decisions/archive/YYYY/, retrospectives/archive/YYYY/)
- Quality gates before archiving
- Maintenance schedule (monthly, quarterly, annual)

**Key considerations:**
- Extract learnings from retrospectives before archiving
- Update status field (superseded/deprecated) before archiving
- Move to `context/decisions/archive/YYYY/` or `context/workflows/retrospectives/archive/YYYY/`
- Update all cross-references
- Keep most recent 5-7 retrospectives active

## Step 11b: Consider File Splitting (if applicable)

**Check for splitting candidates:**
- Context files over 400-500 lines covering multiple distinct topics
- Files that would benefit from focused, single-responsibility structure

**Splitting pattern (overview + focused guides):**
1. Create focused files for each distinct topic (e.g., git-commit-conventions.md, git-workflow.md, git-safety.md)
2. Convert original file to overview that links to focused guides
3. Update context/_index.md and context/_loading-map.md
4. Update all cross-references throughout context system

**Benefits:**
- Easier to load only relevant context for specific tasks
- Single responsibility per file
- Better task-based loading via loading map
