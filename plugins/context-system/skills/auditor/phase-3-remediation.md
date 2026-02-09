# Phase 3: Execute Remediation

Systematic process for fixing violations identified in audit.

**Use this phase when**: Audit (Phase 2) identified violations that need fixing.

**Time estimate**: Varies by violation count and complexity (typically 10-40 hours for comprehensive remediation)

---

## Step 1: Create Remediation Plan

Take the prioritized action plan from Phase 2 and organize for efficient execution.

### Group Violations by Type

**Why group**: Batch similar fixes for efficiency

**Common groupings**:
- **Size violations**: All skills needing refactoring
- **Missing sections**: All artifacts needing troubleshooting/limitations
- **Broken links**: All link fixes
- **Format violations**: All formatting issues

**Example**:
```markdown
## Remediation Groups

### Group 1: Size Refactoring (19 hours)
- recipe-scraper (400 lines) → 5 hours
- audit (390 lines) → 4 hours
- standards-sync (389 lines) → 4 hours
- compare (387 lines) → 4 hours
- Add Quick Starts × 4 → 2 hours

### Group 2: Troubleshooting Sections (8 hours)
- Add to 7 skills × 1 hour each
- Review and test × 1 hour

### Group 3: Examples (4 hours)
- Add to compare, systematic-review, audit, diagram
```

### Assign Owners

**Who can fix**:
- User (skill owner)
- Team member (delegated)
- External contributor
- AI assistant (for routine fixes)

**Document**:
```markdown
| Violation | Artifact | Owner | Status |
|-----------|----------|-------|--------|
| Size >400 lines | recipe-scraper | User | In progress |
| Missing troubleshooting | diagram | User | Not started |
```

### Set Deadlines

**Based on priority**:
- Critical: 1-2 weeks
- High: 3-4 weeks
- Medium: 4-6 weeks
- Low: Next quarter

**Be realistic**:
- Account for complexity
- Consider dependencies
- Allow buffer time
- Don't overcommit

---

## Step 2: Execute Fixes

For each violation, follow appropriate fix workflow.

### For Size Violations (Refactoring)

**Follow**: [[skills/refactoring-workflow]] (for skills) or artifact-specific refactoring process

**Steps**:
1. Read current artifact
2. Identify natural breakpoints
3. Plan reference file organization
4. Extract content to reference files
5. Update main file with summaries + links
6. Validate structure and links
7. Test (restart Claude Code for skills)

**Time per artifact**: 3-6 hours depending on size

### For Missing Sections

**Common additions**:
- Troubleshooting sections
- Known limitations
- Good/bad examples
- Quick Start navigation

**Process**:
1. Read artifact to understand context
2. Draft section content (based on actual usage/issues)
3. Add section to artifact
4. Validate placement and formatting
5. Test if applicable

**Time per section**: 30 minutes - 1 hour

### For Broken Links

**Process**:
1. Identify target file (was it moved? deleted? renamed?)
2. Fix link syntax (correct path, wikilink format)
3. If target deleted: Remove link or link to replacement
4. Validate all links in artifact

**Time**: 10-20 minutes per artifact with broken links

### For Format Violations

**Common issues**:
- Inconsistent heading levels
- Wrong frontmatter fields
- Incorrect tag formatting
- Missing separators

**Process**:
1. Read standard/template
2. Compare artifact to standard
3. Apply fixes systematically
4. Validate against standard

**Time**: 20-40 minutes per artifact

### Batch Similar Changes

**Efficiency tip**: Fix all instances of same violation type together

**Example workflow**:
```bash
# Add troubleshooting sections to all 7 skills in one session
# Benefits:
# - Single context load
# - Reuse patterns across skills
# - Catch inconsistencies
# - Faster than one-at-a-time
```

---

## Step 3: Validate Changes

After fixes, verify violations are resolved and no regressions introduced.

### Re-run Automated Audit

```bash
cd .claude/scripts
./[artifact-type]-audit.sh
```

**Check**:
- Are fixed violations now passing?
- Are compliance numbers improved?
- Were new violations introduced?

**Example**:
```
Before: 67% compliant (6/9)
After: 100% compliant (9/9)
```

### Manual Spot-Check

**Verify**:
- Links work correctly
- Formatting looks good
- Content makes sense
- No copy-paste errors
- Consistent with standards

**Focus on**:
- Newly extracted reference files
- Edited sections
- Batch-applied changes

### Test Functionality

**For skills**: Restart Claude Code and invoke skills to verify they load

**For templates**: Create a test note using the template

**For documentation**: Click through all links to ensure navigation works

**Time**: 30 minutes - 1 hour depending on change scope

---

## Step 4: Document Results

Record what was fixed, effort invested, and outcomes.

### Update Audit Log

Add remediation section to audit log:

```markdown
## Remediation Results

**Date**: 2026-02-15
**Effort**: 19 hours (4 hours under estimate)

### Violations Resolved

1. **recipe-scraper size violation** (400 → 278 lines):
   - Extracted 3 reference files
   - Added troubleshooting + limitations
   - Effort: 5 hours

2. **audit size violation** (390 → 220 lines):
   - Extracted 3 reference files
   - Added troubleshooting + limitations
   - Effort: 4 hours

[Continue for all fixes...]

### Compliance Change

- **Before**: 67% (6/9 artifacts)
- **After**: 100% (9/9 artifacts)
- **Improvement**: +33 percentage points

### Issues Encountered

- [Any blockers or challenges during remediation]
- [Lessons learned]

### Next Steps

- Monitor for size creep over next quarter
- Schedule next audit: 2026-05-07
```

### Commit Changes

**Use clear commit messages**:

```bash
git add .claude/skills/recipe-scraper/
git commit -m "refactor(skills): apply progressive disclosure to recipe-scraper

- Split 400-line SKILL.md into 278-line overview + 3 reference files
- Add troubleshooting section (4 common issues)
- Add known limitations section with workarounds
- Extract metadata-guide.md, quality-and-edge-cases.md, examples.md
- Compliance: Resolved critical violation

Ref: .claude/auditors/auditor-log-2026-02-08.md"
```

### Update Tracking

**Mark items complete** in action plan:

```markdown
| Violation | Artifact | Owner | Status | Completed |
|-----------|----------|-------|--------|-----------|
| Size >400 | recipe-scraper | User | ✅ Done | 2026-02-15 |
| Size >400 | audit | User | ✅ Done | 2026-02-15 |
| Size >400 | standards-sync | User | ⏳ In Progress | - |
```

---

## Remediation Patterns

### Pattern 1: Phased Remediation

**When**: Many violations, limited time

**Approach**:
1. **Phase 1** (Week 1-2): Critical violations only
2. **Phase 2** (Week 3-4): High priority violations
3. **Phase 3** (Week 5-6): Medium priority violations
4. **Phase 4** (Next quarter): Low priority / nice-to-haves

**Benefits**: Progress visible quickly, prevents overwhelm

### Pattern 2: Systematic Batch Fixing

**When**: Many artifacts with same violation

**Approach**:
1. Fix all instances of Violation Type A
2. Fix all instances of Violation Type B
3. Validate all at once

**Benefits**: Efficient, consistent, pattern reuse

### Pattern 3: Opportunistic Fixing

**When**: Low priority violations, limited dedicated time

**Approach**:
- Fix violations when touching file for other reasons
- "Leave it better than you found it" principle
- Track as bonus compliance improvements

**Benefits**: No dedicated time needed, gradual improvement

---

## Time-Saving Tips

### Reuse Patterns

**First fix establishes template**:
- First troubleshooting section → template for others
- First refactoring → structure for similar artifacts
- First example → format for additional examples

### Automate Where Possible

**Consider automation for**:
- Link validation (scripted)
- Format checks (linters)
- Batch find-replace (sed/awk)
- Template scaffolding

### Delegate Appropriately

**User focus on**:
- Content quality decisions
- Architecture choices
- Standard interpretations

**AI assistant good for**:
- Structural refactoring
- Format fixes
- Link updates
- Template application

---

## Success Criteria

Remediation is complete when:

- [ ] All critical violations resolved
- [ ] All high priority violations resolved (or explicitly deferred)
- [ ] Re-audit shows compliance improvement
- [ ] No new violations introduced
- [ ] Changes tested and validated
- [ ] Audit log updated with results
- [ ] Commits created with clear messages
- [ ] Tracking updated (action items marked complete)
- [ ] Lessons learned documented

**Result**: Improved artifact quality, compliance targets met, systematic improvements applied
