# Phase 4: Validate & Commit

## Step 12: Cross-Reference Check & Quality Validation (COMPREHENSIVE)

**Critical Quality Gate**: Implements multiple checks from [[context-system/context-validation-checks]] and [[skills/execution-standards]].

---

### 12.1 Standard Validation Checklist

**Basic checks**:
- [ ] CLAUDE.md reflects vault-wide conventions
- [ ] Context files properly categorized
- [ ] Skills reference relevant context
- [ ] Templates match current standards
- [ ] No conflicting guidance exists
- [ ] Private context is git-ignored

---

### 12.2 Index Completeness Audit (AUTOMATED)

**Re-run all validation checks from Step 7.4**:

```bash
# Run complete index audit
.claude/scripts/context-curator-validate-indexes.sh

# Expected: All ✅, no ❌
```

**Checks performed**:
1. Domain indexes complete (all files indexed)
2. Main index total accurate (matches actual count)
3. Domain counts consistent (domain index ↔ main index)

**Action if failures**: Return to Step 7 and complete updates

---

### 12.3 File Size Compliance Check

**Implements**: Check 1 from [[context-system/context-validation-checks]]

```bash
# Check for files exceeding thresholds
echo "=== File Size Audit ==="
echo "Critical (>500 lines):"
find context -name "*.md" -not -path "*/archive/*" -exec wc -l {} \; | \
  awk '$1 > 500 {print "  ❌", $2, "(" $1, "lines)"}'

echo ""
echo "High (400-500 lines):"
find context -name "*.md" -not -path "*/archive/*" -exec wc -l {} \; | \
  awk '$1 >= 400 && $1 <= 500 {print "  ⚠️ ", $2, "(" $1, "lines)"}'

echo ""
echo "Watch (300-400 lines):"
find context -name "*.md" -not -path "*/archive/*" -exec wc -l {} \; | \
  awk '$1 >= 300 && $1 < 400 {print "  📊", $2, "(" $1, "lines)"}'
```

**Standards** (from [[context-system/context-boundary-identification-guide]]):
- ❌ **Critical**: >500 lines (split required)
- ⚠️ **High**: 400-500 lines (strong candidate for split)
- 📊 **Watch**: 300-400 lines (evaluate using mental model boundaries)

**Exceptions**: Retrospectives may exceed (comprehensive learnings)

**Action if critical files found**: Plan splitting using [[context-system/context-boundary-identification-guide]]

---

### 12.4 Frontmatter Validation

**Implements**: Checks 2-3 from [[context-system/context-validation-checks]]

```bash
# Check required fields
echo "=== Frontmatter Validation ==="
echo "Missing 'title':"
grep -L "^title:" context/**/*.md 2>/dev/null | sed 's/^/  ❌ /'

echo ""
echo "Missing 'created':"
grep -L "^created:" context/**/*.md 2>/dev/null | sed 's/^/  ❌ /'

echo ""
echo "Missing 'tags':"
grep -L "^tags:" context/**/*.md 2>/dev/null | sed 's/^/  ❌ /'

echo ""
echo "Inconsistent date formats:"
grep -r "created:" context/ 2>/dev/null | \
  grep -v "[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}" | sed 's/^/  ❌ /'
```

**Standards**: All context files must have:
- ✅ `title:` (descriptive)
- ✅ `created: YYYY-MM-DD` (consistent format)
- ✅ `tags:` (minimum `[context]` + category)

**Action if failures**: Add missing frontmatter per [[obsidian/context-frontmatter-standard]]

---

### 12.5 Cross-Reference Integrity

**Implements**: Check 5 from [[context-system/context-validation-checks]]

```bash
# Basic wikilink validation
echo "=== Cross-Reference Check ==="
echo "Checking for broken wikilinks..."

# Extract all wikilinks
grep -roh "\[\[[^]]*\]\]" context/ | sort | uniq > /tmp/wikilinks-used.txt

# Check each (simplified - manual review recommended)
echo "Manual check recommended: Review wikilinks in Obsidian"
echo "Files with most links:"
grep -rc "\[\[" context/**/*.md 2>/dev/null | sort -t: -k2 -rn | head -10
```

**Manual validation in Obsidian**:
- [ ] No broken link indicators
- [ ] Related Context sections resolve
- [ ] Cross-domain references work

**Action if broken links**: Fix references or remove obsolete links

---

### 12.6 Skill Quality Gate (if skills updated)

**If Step 9 updated any skills**, run skill-specific validation:

#### 12.6.1 Skill Structure Validation

```bash
# Check SKILL.md size compliance
for skill in .claude/skills/*/SKILL.md; do
  lines=$(wc -l < "$skill")
  skill_name=$(dirname "$skill" | xargs basename)

  if [ "$lines" -gt 500 ]; then
    echo "❌ $skill_name: $lines lines (>500 VIOLATION)"
  elif [ "$lines" -gt 400 ]; then
    echo "⚠️  $skill_name: $lines lines (>400 action needed)"
  elif [ "$lines" -lt 200 ]; then
    echo "📊 $skill_name: $lines lines (may need more detail)"
  else
    echo "✅ $skill_name: $lines lines (optimal)"
  fi
done
```

**Standards** (from [[skills/structure-standard]]):
- ❌ **Violation**: >500 lines (immediate refactoring)
- ⚠️ **Action needed**: >400 lines (schedule refactoring)
- ✅ **Optimal**: 200-400 lines
- 📊 **May need more**: <200 lines (check if adequate)

---

#### 12.6.2 Progressive Disclosure Check

**For skills with reference files**:
```bash
# Check reference file organization
for skill_dir in .claude/skills/*/; do
  skill_name=$(basename "$skill_dir")
  ref_count=$(find "$skill_dir" -name "*.md" -not -name "SKILL.md" | wc -l)

  if [ "$ref_count" -gt 0 ]; then
    echo "$skill_name: $ref_count reference files"

    # Check for flat structure (no subdirectories or references/ pattern)
    if [ -d "$skill_dir/references" ]; then
      echo "  ✅ Uses references/ subdirectory (7+ files)"
    fi
  fi
done
```

**Standards** (from [[skills/reference-organization]]):
- ✅ 3-6 reference files (sweet spot)
- ⚠️ 7+ files without references/ subdirectory (reorganize)
- ⚠️ <3 files with skill >300 lines (consider splitting)

---

#### 12.6.3 Quality Markers Present

**Manual check** (from [[skills/audit-checklist]]):
- [ ] Quick Start section present (if multi-phase)
- [ ] Troubleshooting section exists
- [ ] Known Limitations documented
- [ ] Examples provided (concrete, not generic)
- [ ] Integration patterns documented (if applicable)

---

### 12.7 Self-Critique Quality Gate

**Implements**: Phase 3 from [[skills/execution-standards]]

**Before presenting to user, answer**:
- [ ] Have I run all automated validation checks?
- [ ] Did all checks pass (all ✅, no ❌)?
- [ ] Have I fixed identified issues?
- [ ] Are indexes complete and accurate?
- [ ] Is frontmatter consistent across files?
- [ ] Are file sizes within standards?
- [ ] Are wikilinks validated?
- [ ] If skills updated, do they meet quality standards?

**If "no" to any**: Return to relevant step and complete validation

---

### 12.8 Validation Summary Report

**Generate summary for user**:

```markdown
## Context Curation Validation Report

### Index Completeness
- ✅/❌ All domain indexes updated
- ✅/❌ Main index total accurate
- ✅/❌ Domain counts consistent
- ✅/❌ Quick Links current

### File Quality
- ✅/❌ All files <500 lines (or split planned)
- ✅/❌ Frontmatter complete and consistent
- ✅/❌ Cross-references valid

### Skill Quality (if applicable)
- ✅/❌ SKILL.md size compliant
- ✅/❌ Progressive disclosure applied
- ✅/❌ Quality markers present

### Issues Identified
[List any ⚠️ or ❌ items that need attention]

### Deferred Actions
[List any items planned for future (e.g., splitting large files)]

**Overall Status**: ✅ Ready for commit | ⚠️ Issues to address
```

---

### 12.9 Validation Checkpoint

**DO NOT PROCEED to Step 13 (User Review) until**:
- [ ] All automated checks run
- [ ] All critical issues (❌) resolved
- [ ] High-priority warnings (⚠️) addressed or documented
- [ ] Validation summary report prepared

**Quality standard**: This implements comprehensive validation from [[context-system/context-validation-checks]] and [[skills/execution-standards]]

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
