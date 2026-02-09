# Context Update Examples

## Example 1: Extract Communication Preference

**Conversation snippet:**
```
User: "Can you avoid using emojis in your responses unless I explicitly request them?"
Claude: "I'll avoid using emojis in my responses unless you explicitly request them."
```

**Extraction:**
```yaml
---
title: Emoji Usage
created: 2026-01-25
updated: 2026-01-25
tags: [context, communication]
type: communication
---

# Emoji Usage

## Summary
Avoid using emojis in responses unless explicitly requested by user.

## Details
Do not include emojis in:
- Regular responses
- Code comments
- Commit messages
- File content
- Documentation

Only use emojis when:
- User explicitly requests: "use emojis" or "add emoji"
- Context clearly calls for it (e.g., user is using them)

## Examples

**Avoid** ✗:
```
✅ Updated the recipe! 🎉
```

**Preferred** ✓:
```
Updated the recipe successfully.
```

## Related Context
- [[communication/style-preferences]]
- [[communication/response-format]]

---

*Last updated: 2026-01-25*
```

## Example 2: Extract Decision

**Conversation snippet:**
```
User: "Let's use lowercase tags for all recipes to keep them consistent"
Claude: "I'll update all recipe tags to lowercase for consistency"
```

**Extraction:**
```yaml
---
title: Lowercase Tag Standardization
date: 2026-01-25
tags: [context, decision, recipes]
status: active
---

# Decision: Lowercase Tag Standardization

## Context
Recipe collection had mixed case tags (Dinner, dinner, DINNER) making filtering and organization difficult.

## Decision
All tags in recipe frontmatter must be lowercase.

## Rationale
1. **Consistency**: Easier to search and filter
2. **Simplicity**: One clear rule to follow
3. **Obsidian compatibility**: Tag queries are case-sensitive
4. **Scalability**: Works with hundreds of recipes

### Alternatives Considered
- **Title Case**: More readable but inconsistent in Obsidian
- **Mixed case**: User preference, but creates chaos
- **ALL CAPS**: Too aggressive, poor UX

## Implications
- All existing recipes need tag updates
- Recipe template must reflect this
- Recipe scraper skill must enforce this
- Documentation must be clear about this rule

## Related
- [[obsidian/recipe-conventions]]
- [[recipes/_index/Recipe System Documentation]]

---

*Status: Active as of 2026-01-25*
```

## Example 3: Update Multiple Locations

**Scenario**: New convention that skills must read templates first

**Updates required:**

1. **context/project/vault-conventions.md** (update):
```markdown
# Template-First Architecture

All skills that create notes must read the relevant template first...
```

2. **context/_index.md** (update):
```markdown
- [[obsidian/vault-conventions]] - Template-first architecture
```

3. **CLAUDE.md** (update):
```markdown
**How Skills Use Templates**:
1. The skill MUST read the template file first using the Read tool
```

4. **.claude/skills/recipe-scraper/SKILL.md** (verify):
```markdown
### Step 1: Read Template (REQUIRED)
```

5. **context/decisions/2026-01-25-template-first-skill-architecture.md** (new):
```markdown
# Decision: Template-First Skill Architecture

Document the decision and rationale...
```

## Example 4: Split Large Context File

**Scenario**: git-practices.md (467 lines) covers 3 distinct topics

**Splitting approach:**

1. **Create focused files:**
   - context/workflows/processes/git-commit-conventions.md (155 lines)
   - context/workflows/processes/git-workflow.md (124 lines)
   - context/workflows/processes/git-safety.md (133 lines)

2. **Convert to overview (82 lines):**
   - git-practices.md becomes navigation hub linking to focused guides

3. **Update indexes:**
   - context/_index.md: Add all 4 files (overview + 3 focused)
   - context/_loading-map.md: Map subtasks (creating commits → git-commit-conventions)

4. **Update cross-references:**
   - Search for references to git-practices throughout context/
   - Update to reference specific focused guide where appropriate

**Benefits:**
- Creating commits → load only git-commit-conventions + git-safety
- Creating PRs → load only git-workflow
- General git work → load git-practices overview

## Example 5: Retrospective → Context + Skill Improvement (Full Feedback Loop)

**Scenario**: Learning system retrospective identifies "Broken Wikilinks After Move" issue

**Full update cycle:**

1. **Extract from retrospective** (context/workflows/retrospectives/2026-01-27-learning-system-implementation-retro.md):
```markdown
### Issue 1: Broken Wikilinks After Move
**Discovery**: Moving files between directories breaks relative wikilinks
**Current mitigation**: Manual fix or agent cleanup
**Potential improvement**: Could create "safe move" workflow
```

2. **Create context document** (context/workflows/processes/safe-file-move.md):
```markdown
# Safe File Move Workflow

## Problem
Moving files in Obsidian breaks wikilinks if not updated.

## Solution
1. Find all references to file being moved
2. Update wikilinks with new path
3. Move file
4. Validate links resolve

## Related
- Used by: mental-model, book-notes, safe-move skills
```

3. **Create new skill** (.claude/skills/safe-move/SKILL.md):
```markdown
# Safe Move Skill

Safely move files while preserving wikilinks.

## Workflow
1. Grep for references to file
2. Update all wikilinks
3. Move file
4. Validate no broken links
```

4. **Update existing skills** that move/create files:
```bash
# Find skills that might move files
Grep: pattern="Write.*\.md|move|rename" path=".claude/skills" output_mode="files_with_matches"

# Update mental-model/SKILL.md
# Update book-notes/SKILL.md
# Update podcast/SKILL.md

# Add step: "Use safe-move pattern" or "Validate wikilinks after creation"
```

5. **Update context index** (context/_index.md):
```markdown
### Processes
- safe file move - Prevent broken wikilinks when moving files
```

6. **Update CLAUDE.md** (if broadly applicable):
```markdown
## File Operations
- Use safe file move pattern for file moves
- Available as `/safe-move` skill
```

**Result**: Problem identified → Pattern documented → Skill created → Existing skills improved → Future moves are safe

**Key insight**: Don't just document problems in retrospectives. Close the loop by:
- Creating reusable patterns (context)
- Building automation (new skills)
- Improving existing tools (skill updates)
