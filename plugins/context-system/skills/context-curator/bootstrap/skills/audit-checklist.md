---
title: Skill Audit Checklist
category: workflow
type: standard
tags:
- audit
- compliance
- context
- maintenance
- quality
- skills
created: 2026-02-07
updated: 2026-02-07
status: active
---
# Skill Audit Checklist

**Purpose**: Comprehensive quality checklist for auditing Claude Code skills systematically.

**When to use**: Quarterly skill audits, before/after refactoring, when onboarding new skills.

**Complements**: Automated audit script (`.claude/scripts/skill-audit.sh`) handles what can be automated; this checklist covers manual quality assessment.

---

## Audit Cadence

**Quarterly** (every 3 months):
- Full comprehensive audit using this checklist
- Run automated script for quantitative metrics
- Document findings in audit log
- Schedule refactoring for violations

**Monthly** (light check):
- Run automated script only
- Review new/changed skills
- Check compliance trends

**After major changes**:
- New skill added → Run full checklist
- Skill refactored → Validate compliance
- Standards updated → Check affected skills

---

## Quick Reference

**Run automated audit first**:
```bash
cd .claude/scripts
./skill-audit.sh --verbose
```

Then use this checklist for manual quality assessment.

---

## Section 1: Structure & Format Compliance

### 1.1 Size Compliance

**Check**:
- [ ] SKILL.md <500 lines (violation threshold)
- [ ] SKILL.md <400 lines (proactive threshold - schedule refactoring)
- [ ] SKILL.md ideally 200-300 lines (sweet spot)
- [ ] Each reference file <500 lines (ideally 100-300)
- [ ] No single section >100 lines without progressive disclosure

**Thresholds** (from [[skills/structure-standard]]):
- **Ideal**: 200-300 lines (sweet spot for readability)
- **Watch**: >300 lines (monitor for growth)
- **Proactive action**: >400 lines (schedule progressive disclosure refactoring)
- **Violation**: >500 lines (immediate refactoring required)

**Automated**: ✅ (script checks this)

**Manual review**:
- Does length feel appropriate for skill complexity?
- Are any sections too dense or overwhelming?
- Should this trigger proactive refactoring (>400 lines)?

**Priority**: Critical (>500 = violation), High (>400 = proactive action needed)

---

### 1.2 Frontmatter Validation

**Check**:
- [ ] `name:` matches directory name (kebab-case)
- [ ] `description:` clear, concise (1-2 sentences)
- [ ] `allowed-tools:` comprehensive but not overly restrictive

**Automated**: ✅ (script checks presence)

**Manual review**:
- Is description accurate for auto-discovery?
- Are tools listed appropriate for skill tasks?

**Example good frontmatter**:
```yaml
---
name: context-update
description: "Review conversations and changes to extract and update context that improves Claude alignment with project preferences"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---
```

**Priority**: High

---

### 1.3 Required Sections Present

**Check**:
- [ ] Title (H1) matches frontmatter name (friendly version)
- [ ] Brief overview (2-3 paragraphs)
- [ ] Quick Start (if multi-phase or multi-scenario)
- [ ] Main content (workflow overview or phase summaries)
- [ ] Related Documentation section

**Automated**: ⚠️ (script checks Quick Start only)

**Manual review**:
- Is overview actually brief (not multi-page)?
- Does Quick Start provide clear entry points?
- Is main content well-organized?

**Reference**: [[skills/structure-standard]]

**Priority**: High

---

## Section 2: Progressive Disclosure Compliance

### 2.1 Reference File Organization

**Check**:
- [ ] 3-6 reference files (if skill >200 lines)
- [ ] Descriptive file names (`phase-1-discovery.md` not `part1.md`)
- [ ] Consistent naming pattern (phase/topic/purpose-based)
- [ ] Flat structure (reference files don't reference each other)

**Automated**: ⚠️ (script counts files, manual checks quality)

**Manual review**:
- Is organization strategy clear (phase/topic/purpose)?
- Are file names self-documenting?
- Could any files be merged or split?

**Reference**: [[skills/reference-organization]]

**Priority**: Medium

---

### 2.2 Summary vs Detail Balance

**Check SKILL.md**:
- [ ] Each phase/section has brief summary (5-10 lines)
- [ ] Key steps listed (bulleted, 3-7 items)
- [ ] Link to reference file for details
- [ ] No walls of text >30 lines

**Check reference files**:
- [ ] Each file self-contained (understandable independently)
- [ ] Appropriate depth (detailed instructions, examples, edge cases)
- [ ] Not duplicating SKILL.md content

**Manual review only**

**Priority**: Medium

---

## Section 3: Content Quality

### 3.1 Workflow Clarity

**Check**:
- [ ] Workflow steps clearly numbered/ordered
- [ ] Each step has actionable instruction
- [ ] Decision points clearly marked
- [ ] Expected outcomes stated
- [ ] Error handling guidance provided

**Manual review only**

**Test**: Could another agent follow this skill without prior knowledge?

**Priority**: High

---

### 3.2 Examples & Concrete Guidance

**Check**:
- [ ] Concrete examples provided (not just abstract guidance)
- [ ] "Good vs Bad" examples where applicable
- [ ] Real-world scenarios included
- [ ] Edge cases documented
- [ ] Common pitfalls listed

**Manual review only**

**Anti-pattern**: "Follow best practices" (too vague)
**Good pattern**: "Use `phase-1-discovery.md` not `part1.md` for clarity"

**Priority**: Medium

---

### 3.3 Context Integration

**Check**:
- [ ] References current context files (not outdated paths)
- [ ] Uses wikilinks for context: `[[context/path/file]]`
- [ ] Uses relative links for skill references: `[file.md](file.md)`
- [ ] Links to relevant standards and conventions
- [ ] "Related Documentation" section complete

**Automated**: ⚠️ (script checks for deprecated paths)

**Manual review**:
- Are context references still accurate?
- Should additional context be referenced?

**Priority**: Medium

---

## Section 4: Technical Validation

### 4.1 Link Validation

**Check**:
- [ ] All internal links work (no 404s)
- [ ] Wikilinks formatted correctly
- [ ] Relative links use correct paths
- [ ] External links accessible (if any)

**Automated**: ✅ (script checks internal links)

**Manual review**:
- Test a few links manually
- Check for orphaned reference files (not linked from SKILL.md)

**Priority**: High

---

### 4.2 Tool Usage Consistency

**Check**:
- [ ] Tools used match `allowed-tools` list
- [ ] Tool usage follows current best practices
- [ ] No hardcoded file operations (uses Read/Write/Edit, not bash cat/sed)
- [ ] Bash reserved for system commands only

**Manual review only**

**Reference**: [[skills/execution-standards]]

**Priority**: Medium

---

### 4.3 Testing Status

**Check**:
- [ ] Skill has been tested after last refactoring
- [ ] Test date documented (comment in SKILL.md or audit log)
- [ ] Known issues documented
- [ ] Workarounds provided for limitations

**Manual review only**

**Note**: Skills require Claude Code restart to load changes.

**Test procedure**:
1. Exit Claude Code
2. Restart: `claude-code`
3. Invoke: `/skill-name`
4. Verify reference files load on-demand
5. Confirm workflow executes correctly

**Priority**: High (before marking skill as production-ready)

---

## Section 5: Standards Alignment

### 5.1 Skill Structure Standard Compliance

**Check against**: [[skills/structure-standard]]

**Validates**:
- [ ] Follows standard template
- [ ] Section ordering correct
- [ ] Writing style consistent (clear, direct, action-oriented)
- [ ] Tone appropriate
- [ ] Size guidelines met

**Manual review only**

**Priority**: Medium

---

### 5.2 Reference Organization Pattern Compliance

**Check against**: [[skills/reference-organization]]

**Validates**:
- [ ] Organization pattern matches skill type (phase/topic/purpose/hybrid)
- [ ] Naming convention followed
- [ ] File count in sweet spot (3-6)
- [ ] Flat structure maintained

**Manual review only**

**Priority**: Medium

---

### 5.3 Current Best Practices

**Check against external sources**:
- [ ] Anthropic skill authoring best practices (latest version)
- [ ] Progressive disclosure guidelines
- [ ] Claude Code conventions (if documented)

**Manual review**: Check Anthropic docs quarterly for updates
- [Anthropic Skill Authoring Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

**Document**: If external best practices change, update internal standards and note in audit log.

**Priority**: Low (quarterly check sufficient)

---

## Section 6: Usability Assessment

### 6.1 Discoverability

**Check**:
- [ ] Skill description makes purpose clear
- [ ] Quick Start helps user find entry point
- [ ] File names indicate content
- [ ] Clear navigation throughout

**Manual review**: Put yourself in shoes of first-time user

**Questions**:
- Would I know when to use this skill?
- Can I find what I need quickly?
- Is organization intuitive?

**Priority**: Medium

---

### 6.2 Cognitive Load

**Check**:
- [ ] Progressive disclosure reduces overwhelm
- [ ] Summaries before details
- [ ] Not too many choices at once
- [ ] Clear decision trees at branches

**Manual review**: Read SKILL.md start to finish

**Red flags**:
- Feeling overwhelmed by information
- Unclear what to do next
- Too many options without guidance

**Priority**: Medium

---

### 6.3 Maintenance Burden

**Check**:
- [ ] Not overly complex (can be maintained)
- [ ] Clear ownership/responsibility
- [ ] Dependencies documented
- [ ] No brittle assumptions (e.g., hardcoded paths)

**Manual review**: Consider long-term maintenance

**Questions**:
- Will this skill break easily?
- Is it easy to update when standards change?
- Could someone else maintain this?

**Priority**: Low

---

## Audit Output

### Findings Documentation

**For each skill audited, document**:

```markdown
## Skill: [name]

**Audit date**: YYYY-MM-DD
**Audited by**: [name/role]

### Compliance Status
- Size: [PASS/FAIL] ([line count] lines)
- Structure: [PASS/FAIL with notes]
- Content: [PASS/FAIL with notes]
- Links: [PASS/FAIL] ([broken count] broken)
- Testing: [TESTED/UNTESTED] ([date])

### Issues Found
1. [Priority] [Description]
2. [Priority] [Description]

### Recommended Actions
- [ ] [Action item 1]
- [ ] [Action item 2]

### Notes
[Any additional observations]
```

**Save to**: `.claude/audits/audit-log-YYYY-MM-DD.md`

---

### Summary Report

**After auditing all skills**:

```markdown
# Quarterly Skill Audit - [Quarter] [Year]

## Executive Summary
- Total skills: [count]
- Compliant: [count] ([percentage]%)
- Violations: [count]
- Trends: [improving/stable/declining]

## Key Findings
[Top 3-5 issues across all skills]

## Recommendations
[Prioritized action items]

## Next Steps
[Concrete plan with owners and deadlines]

## Standards Updates
[Any standards that should be revised based on findings]
```

---

## Integration with Audit Script

**Workflow**:

1. **Run automated script**:
   ```bash
   ./skill-audit.sh --verbose > audit-output.txt
   ```

2. **Review script output**: Identifies violations automatically

3. **Use this checklist**: Manual quality assessment for flagged skills

4. **Document findings**: Add to audit log (script generates template)

5. **Create action items**: Schedule refactoring or updates

6. **Track trends**: Compare to previous audits

---

## Continuous Improvement

### After Each Audit

**Update standards if**:
- Multiple skills fail same check → Standard may be unclear
- Common pattern emerges → Document as best practice
- External best practices change → Sync internal standards
- New quality dimension discovered → Add to checklist

**Update this checklist if**:
- New automated check added → Remove from manual list
- Check proves ineffective → Remove or revise
- Missing quality dimension → Add new section
- Checklist too long → Consolidate or prioritize

---

## Related Documentation

- [[skills/refactoring-workflow]] - How to refactor non-compliant skills
- [[skills/structure-standard]] - Template for compliant skills
- [[skills/reference-organization]] - Reference file patterns
- [[skills/execution-standards]] - Skill quality standards
- [[context-system/context-maintenance-guide]] - Quarterly maintenance cadence
- `.claude/scripts/skill-audit.sh` - Automated audit script

---

## Version History

**v1.0 (2026-02-07)**: Initial checklist
- Extracted from skills refactoring retrospective
- 6 main sections, 20+ quality checks
- Designed to complement automated script

**Next review**: 2026-05-07 (after first quarterly use)
