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

## Step 7: Update Indexes & Validate Structure (COMPREHENSIVE)

**Critical Quality Gate**: This step implements Check 8 from [[context-system/context-validation-checks]].

**Standards enforced**:
- ✅ Index completeness (all files indexed)
- ✅ File count accuracy (domain + main indexes)
- ✅ Quick Links currency (top 5 most important/recent)
- ✅ Domain descriptions reflect current scope
- ✅ Wikilink format consistency

---

### 7.1 Identify All Affected Indexes

**For each new/modified context file, check**:

```bash
# 1. Which domain does this belong to?
file="context/[domain]/[filename].md"
domain=$(dirname "$file" | xargs basename)

# 2. Does domain have an index?
domain_index="context/$domain/_index.md"
[ -f "$domain_index" ] && echo "Domain index: $domain_index"

# 3. Main index always affected
echo "Main index: context/_index.md"

# 4. Loading map (if creating new task type)
[ new_task_type ] && echo "Loading map: context/context-system/loading-map.md"
```

**Affected indexes**:
- [ ] Domain index (`context/[domain]/_index.md`)
- [ ] Main index (`context/_index.md`)
- [ ] Loading map (if new task type)

---

### 7.2 Domain Index Update (Detailed Checklist)

**For**: `context/[domain]/_index.md`

#### 7.2.1 Update Description (if scope changed)

**Check if new file expands domain scope**:
```markdown
# Before
**Description**: Research gathering, analysis, and synthesis pipelines

# After (if adding methodology standards)
**Description**: Research gathering, analysis, synthesis pipelines, and research methodology standards
```

**Action**: Update description to reflect new capabilities

---

#### 7.2.2 Update Quick Links

**Policy**: Top 5-7 most important or most recent files

**Check**:
- [ ] Is new file in top 5 most important? (Add to Quick Links)
- [ ] Is new file most recent? (Add to Quick Links)
- [ ] Are Quick Links ordered logically? (Recent first OR by importance)
- [ ] Consider grouping by category if 7+ files

**Example**:
```markdown
## Quick Links

**Synthesis Pipeline**:
- [[research/synthesis-pipeline]]
- [[research/gathering-phase]]

**Research Methodology Standards** (NEW CATEGORY):
- [[research/design-science-research-standards]]
- [[research/evidence-synthesis-standards]]
```

**Action**: Add new file to Quick Links if criteria met

---

#### 7.2.3 Update All Files Table

**Format** (from [[obsidian/context-frontmatter-standard]]):
```markdown
| File | Size | Description |
|------|------|-------------|
| [[domain/file|file.md]] | 🟢/🟡/🔴 | First 60 chars of purpose |
```

**Size indicators** (from [[context-system/context-validation-checks]]):
- 🟢 Green: <150 lines (ideal)
- 🟡 Yellow: 150-400 lines (acceptable)
- 🔴 Red: >400 lines (consider splitting)

**Alphabetical ordering**: Keep table sorted by filename

**Action checklist**:
- [ ] Add new file row (alphabetically)
- [ ] Calculate line count: `wc -l context/domain/file.md`
- [ ] Set size indicator: 🟢 <150, 🟡 150-400, 🔴 >400
- [ ] Extract description (first line of purpose or H1)
- [ ] Truncate description to ~60 chars

**Example**:
```markdown
| [[research/evidence-synthesis-standards|evidence-synthesis-standards.md]] | 🔴 950 | Best practices for systematic reviews and evidence synthesis |
```

---

#### 7.2.4 Update File Count

**Location**: `## All Files (N)` header

**Calculation**:
```bash
# Count actual files (excluding index)
find context/[domain] -name "*.md" -not -name "_index.md" | wc -l

# Update header
## All Files (4) → ## All Files (5)
```

**Action**: Update N to match actual file count

---

#### 7.2.5 Update Large File Note

**Location**: `**Note**: N files >150 lines...`

**Calculation**:
```bash
# Count files over 150 lines
find context/[domain] -name "*.md" -not -name "_index.md" -exec wc -l {} \; | awk '$1 > 150' | wc -l

# Update note
**Note**: 1 files >150 lines → **Note**: 2 files >150 lines
```

**Action**: Update count of large files

---

### 7.3 Main Index Update (context/_index.md)

**For**: `context/_index.md`

#### 7.3.1 Update Total File Count

**Location**: `**Total**: N files across 17 domains`

**Calculation**:
```bash
# Count all context files (excluding indexes and archive)
find context -name "*.md" \
  -not -name "_index.md" \
  -not -path "*/archive/*" \
  -not -path "*/private/*" | wc -l

# Example: 116 + 12 new files = 128 files
```

**Action**: Update total to match actual count

---

#### 7.3.2 Update Domain File Count

**Location**: "All Domains" section

**Format**:
```markdown
- **[[domain/_index|Domain Name]]** (N files)
  Description of domain scope
```

**Calculation**: Use domain's `## All Files (N)` count

**Example**:
```markdown
# Before
- **[[research/_index|Research & Synthesis]]** (4 files)
  Research gathering, analysis, synthesis pipelines

# After
- **[[research/_index|Research & Synthesis]]** (13 files)
  Research gathering, analysis, synthesis pipelines, and 7 research methodology standards
```

**Action checklist**:
- [ ] Update file count to match domain index
- [ ] Update description if domain scope changed
- [ ] Fix any broken wikilinks (context-system/_index → domain/_index)

---

#### 7.3.3 Fix Wikilink Paths

**Common issue**: Main index may reference `[[context-system/_index|...]]` when it should reference `[[domain/_index|...]]`

**Check**:
```bash
# Find mismatched wikilinks
grep -n "context-system/_index" context/_index.md
```

**Fix**:
```markdown
# Before
- **[[context-system/_index|Skills]]** (11 files)

# After
- **[[skills/_index|Skills]]** (12 files)
```

**Action**: Correct all wikilink paths to match actual domain names

---

### 7.4 Automated Index Validation (Quality Gate)

**Run these checks BEFORE proceeding to Step 12**:

#### 7.4.1 Domain Index Completeness Check

```bash
#!/bin/bash
echo "=== Domain Index Audit ==="
echo

for domain in context/*/; do
  domain_name=$(basename "$domain")

  # Skip special directories
  if [[ "$domain_name" == "private" || "$domain_name" == "archive" ]]; then
    continue
  fi

  domain_index="$domain/_index.md"

  if [ -f "$domain_index" ]; then
    # Count actual files (excluding index)
    actual=$(find "$domain" -name "*.md" -not -name "_index.md" | wc -l | tr -d ' ')

    # Count indexed files (lines starting with | [[)
    indexed=$(grep -c "^| \[\[$domain_name" "$domain_index" 2>/dev/null || echo "0")

    if [ "$actual" -eq "$indexed" ]; then
      echo "✅ $domain_name: $actual files (all indexed)"
    else
      echo "❌ $domain_name: $actual files but only $indexed indexed (MISMATCH)"
    fi
  else
    file_count=$(find "$domain" -name "*.md" | wc -l | tr -d ' ')
    if [ "$file_count" -gt 0 ]; then
      echo "⚠️  $domain_name: $file_count files but missing _index.md"
    fi
  fi
done
```

**Expected output**: All domains show ✅ (all indexed)

**If ❌ or ⚠️ appears**: Return to Step 7.2 and complete domain index updates

---

#### 7.4.2 Main Index Total Validation

```bash
echo ""
echo "=== Main Index Total Validation ==="
echo

# Count total files
total_files=$(find context -name "*.md" \
  -not -name "_index.md" \
  -not -path "*/archive/*" \
  -not -path "*/private/*" | wc -l | tr -d ' ')

# Extract main index total
main_index_total=$(grep "^\*\*Total\*\*:" context/_index.md | \
  grep -o '[0-9]\+' | head -1)

echo "Actual context files: $total_files"
echo "Main index claims: $main_index_total"

if [ "$total_files" -eq "$main_index_total" ]; then
  echo "✅ Main index total is accurate"
else
  echo "❌ Main index needs update ($total_files actual vs $main_index_total claimed)"
fi
```

**Expected output**: ✅ Main index total is accurate

**If ❌ appears**: Return to Step 7.3.1 and update main index total

---

#### 7.4.3 Domain Count Validation

```bash
echo ""
echo "=== Domain Count Validation ==="
echo

for domain in context/*/; do
  domain_name=$(basename "$domain")

  # Skip special directories
  if [[ "$domain_name" == "private" || "$domain_name" == "archive" ]]; then
    continue
  fi

  domain_index="$domain/_index.md"

  if [ -f "$domain_index" ]; then
    # Get domain's claimed count
    domain_count=$(grep "^## All Files (" "$domain_index" | \
      grep -o '([0-9]\+)' | grep -o '[0-9]\+')

    # Get main index's claimed count for this domain
    main_count=$(grep "\[\[$domain_name/_index" context/_index.md | \
      grep -o '([0-9]\+ files)' | grep -o '[0-9]\+' | head -1)

    if [ "$domain_count" -eq "$main_count" ]; then
      echo "✅ $domain_name: Counts match ($domain_count files)"
    else
      echo "❌ $domain_name: Domain says $domain_count, main index says $main_count"
    fi
  fi
done
```

**Expected output**: All domains show ✅ (counts match)

**If ❌ appears**: Sync domain index count with main index

---

### 7.5 Validation Checkpoint

**DO NOT PROCEED to Step 8 until**:
- [ ] All automated checks pass (all ✅, no ❌)
- [ ] Domain indexes updated (description, Quick Links, All Files table, counts)
- [ ] Main index updated (total, domain counts, descriptions)
- [ ] All wikilinks correct (domain/_index not context-system/_index)

**If any checks fail**: Return to relevant substep and fix before proceeding

**Quality standard**: This implements Check 8 from [[context-system/context-validation-checks]]

**Prefer automated script**: See [[index-update-template]] for quick fixes

**Script location**: `.claude/scripts/context-curator-validate-indexes.sh`

---

## Step 7b: Update Loading Map (if applicable)

**When to update** `context/context-system/loading-map.md`:
- Creating new task type or domain
- Adding new workflow that needs task-based loading
- Splitting files requiring subtask-specific loading

**Check**:
- [ ] Does new context create new task type?
- [ ] Should this be in Quick Start table in context/_index.md?
- [ ] Do split files need subtask-specific loading rules?

**If yes to any**: Update loading map per [[context-system/context-validation-checks]] Check 9

## Step 8: Update CLAUDE.md and README.md (if needed)

### 8.1: When to Update Documentation

**Update both CLAUDE.md and README.md when**:
- ✅ Skills added or removed
- ✅ Context system file count changes significantly (±10 files or more)
- ✅ New domain added to context/
- ✅ Major architectural changes (folder restructuring, new patterns)
- ✅ Skill capabilities significantly enhanced (e.g., quality gates added)

**Update only CLAUDE.md when**:
- Vault-wide conventions change
- New workflows established
- Critical guidelines added
- Template structure changes

**Update only README.md when**:
- Production-validated patterns evolve
- Project status changes
- External references updated

**Update neither when**:
- Minor context file additions (1-5 files)
- Specific preferences documented
- Small clarifications or corrections

---

### 8.2: What to Update in CLAUDE.md

**Purpose**: Vault-level instructions for Claude (LLM audience)

**Check these sections**:
- [ ] **Custom Skills** list (lines ~138-164)
  - Add/remove skills with brief descriptions
  - Organize by category (Research, Planning, Content, Meta-Skills)
  - Mark deprecated skills before removal
- [ ] **Context System** overview (lines ~52-69)
  - Update file counts if changed significantly
  - Update domain list if new domains added
- [ ] **Template Files** (lines ~104-117)
  - Add new templates
  - Update template purposes
- [ ] **Workflows** section (lines ~254-271)
  - Update if new workflow patterns established

**Example updates**:
```markdown
# Before
- `/context-curator` - Extract context from conversations

# After (capability enhancement)
- `/context-curator` - Extract and curate context with automated quality gates
```

---

### 8.3: What to Update in README.md

**Purpose**: Repository overview for humans (developers, researchers)

**Check these sections**:
- [ ] **High-Level Architecture → Custom Skills** (lines ~69-95)
  - Same updates as CLAUDE.md but with more detail
  - Include skill counts and category organization
- [ ] **High-Level Architecture → Structured Context** (line ~40)
  - Update file count: `(140 files)` format
- [ ] **Core System** (lines ~126-133)
  - Update context file count
  - Update skill count
- [ ] **Example Implementations** (lines ~193-199)
  - Add notable new skills
  - Update descriptions for enhanced skills
- [ ] **Project Status** (lines ~245-253)
  - Update production validation notes
  - Document significant pattern evolutions

**Example updates**:
```markdown
# Before
**17 concept-based domains** (109 files)

# After
**17 concept-based domains** (140 files)
```

---

### 8.4: Validation Checklist

After updating, verify:
- [ ] Skill counts match actual count (`find .claude/skills -mindepth 1 -maxdepth 1 -type d | wc -l`)
- [ ] Context file counts match (`find context -name "*.md" -not -name "_index.md" -not -path "*/archive/*" -not -path "*/private/*" | wc -l`)
- [ ] Skill descriptions match SKILL.md frontmatter descriptions
- [ ] No references to deleted skills (unless marked DEPRECATED)
- [ ] Categories accurately reflect skill purposes
- [ ] Both files updated consistently (if both needed updates)

---

### 8.5: Common Mistakes to Avoid

**Don't**:
- ❌ Update for every minor context file addition
- ❌ Add skills to documentation before they're fully implemented
- ❌ Leave DEPRECATED markers indefinitely (remove after 1-2 releases)
- ❌ Update one file without checking if the other needs it too
- ❌ Hardcode file counts without validation

**Do**:
- ✅ Update both files together when skills change
- ✅ Validate counts with bash commands
- ✅ Group related updates in single commit
- ✅ Use consistent descriptions across both files
- ✅ Mark skills as DEPRECATED before deleting directories

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
