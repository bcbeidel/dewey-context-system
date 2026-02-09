# Phase 2: Execute Audit (Quarterly/Recurring)

Detailed workflow for running an audit cycle on established artifact types.

**Use this phase when**: You've already set up audit infrastructure (Phase 1) and need to run a regular audit cycle.

**Time estimate**: 3-5 hours for comprehensive quarterly audit

---

## Step 1: Ask User Which Artifact Type

If not specified, ask what to audit:
- **Skills** (implemented - has automation)
- **Context** (planned)
- **Documentation** (planned)
- **Templates** (planned)
- **Custom** (user-defined)

**If artifact type has no automation yet**: User needs Phase 1 (Setup) first.

---

## Step 2: Run Automated Checks

### Execute Audit Script

```bash
cd .claude/scripts
./[artifact-type]-audit.sh --verbose
```

**Example**:
```bash
cd .claude/scripts
./skill-audit.sh --verbose
```

### Review Output

**Terminal report shows**:
- Immediate feedback on violations
- Pass/fail status per artifact
- Summary statistics

**Audit log created at**:
```
.claude/auditors/auditor-log-YYYY-MM-DD.md
```

**Log contains**:
- Violations by priority (Critical, High, Medium, Low)
- Compliance percentage
- Per-artifact breakdown
- Detailed violation descriptions

**Time**: 5-15 minutes

---

## Step 3: Manual Assessment

Automated checks catch quantitative issues (size, structure), but qualitative assessment requires human judgment.

### Load Checklist

```bash
Read: context/workflows/standards/[artifact-type]-audit-checklist.md
```

**Example**:
```bash
Read: context/skills/auditoror-checklist.md
```

### For Each Flagged Artifact

1. **Apply manual checklist**:
   - Review content quality
   - Check usability/clarity
   - Assess maintainability
   - Verify completeness

2. **Document findings**:
   - Rate quality dimensions (1-5 scale)
   - List specific issues with severity
   - Note positive aspects
   - Compare to best practices

3. **Recommend actions**:
   - Refactor (if size violation)
   - Clarify (if unclear content)
   - Enhance (if missing features)
   - Archive (if obsolete)
   - Estimate effort (hours)

### Identify Patterns

**Look for**:
- **Same issue across multiple artifacts**: Indicates systemic problem
- **Recurring violations**: Suggests standard unclear or unrealistic
- **New patterns**: May need new quality criteria
- **Root causes**: Why are violations happening?

**Examples**:
- "5 of 9 skills missing troubleshooting sections" → Systemic gap
- "3 skills approaching size limit" → Standard may be too tight
- "All new skills compliant, old ones not" → Onboarding works, maintenance doesn't

**Time**: 15-30 minutes per artifact

---

## Step 4: Document Comprehensive Findings

Update audit log with manual assessment findings.

### Format for Manual Assessment

```markdown
## Manual Assessment

### Artifact: [name]

**Automated Results**:
- Size: [PASS/FAIL] ([line count])
- Structure: [PASS/FAIL] ([violations])
- Links: [PASS/FAIL] ([broken links])
- Fields: [PASS/FAIL] ([missing fields])

**Manual Assessment** (1-5 scale):
- Content quality: [rating] - [notes]
- Usability: [rating] - [notes]
- Maintainability: [rating] - [notes]
- Completeness: [rating] - [notes]

**Issues Identified**:
1. [CRITICAL] [Description] - [Impact]
2. [HIGH] [Description] - [Impact]
3. [MEDIUM] [Description] - [Impact]

**Strengths**:
- [Positive aspect 1]
- [Positive aspect 2]

**Recommendation**:
- [Primary action] ([effort estimate])
- [Secondary action] ([effort estimate])
```

### Identify Systemic Issues

**Analyze across all artifacts**:
- Patterns observed (frequency = importance)
- Common violations (same problem repeatedly)
- Standards gaps (missing quality criteria)
- Process failures (why violations occurred)

**Document systemic findings**:
```markdown
## Systemic Issues

1. **Missing troubleshooting sections** (7/9 artifacts):
   - Impact: Users can't self-help when things fail
   - Root cause: Standard added recently, not applied retroactively
   - Recommendation: Add to all artifacts (8 hours effort)

2. **Approaching size limits** (4/9 artifacts):
   - Impact: Risk of future violations
   - Root cause: Content accumulation over time
   - Recommendation: Proactive refactoring (16 hours effort)
```

**Time**: 30 minutes

---

## Step 5: Prioritize Findings

Use priority matrix to decide what to fix when.

### Priority Matrix

| Severity | Quick Fix (<1hr) | Small (1-4hrs) | Medium (4-8hrs) | Large (>8hrs) |
|----------|------------------|----------------|-----------------|---------------|
| **Critical** | DO NOW | DO NOW | DO NOW | DO NOW |
| **High** | This cycle | This cycle | This cycle | Plan |
| **Medium** | Nice win | Next cycle | Next cycle | Backlog |
| **Low** | Opportunistic | Backlog | Backlog | Don't do |

**Source**: [[patterns/auditor-pattern#component-6-prioritization-framework]]

### Create Action Plan

**Format**:
```markdown
## Action Plan

### Critical (Complete within 1-2 weeks)
1. [Issue] - [Artifact] - [Effort] - [Owner] - [Due date]
2. [Issue] - [Artifact] - [Effort] - [Owner] - [Due date]

### High Priority (Complete within 3-4 weeks)
3. [Issue] - [Artifact] - [Effort] - [Owner] - [Due date]
4. [Issue] - [Artifact] - [Effort] - [Owner] - [Due date]

### Medium Priority (Complete within 4-6 weeks)
5. [Issue] - [Artifact] - [Effort] - [Owner] - [Due date]

### Backlog (Revisit next quarter)
6. [Issue] - [Artifact] - [Effort] - [Notes]
```

**Assign owners**: Can be user, team member, or "TBD"

**Set target dates**: Based on priority and effort

**Track completion**: Check off items as resolved

**Time**: 30 minutes

---

## Step 6: Track Trends

Compare current audit to previous audits to identify trends.

### Comparison Table

| Date | Total | Compliant | % | Critical | High | Medium | Low | Notes |
|------|-------|-----------|---|----------|------|--------|-----|-------|
| 2025-11-07 | 9 | 4 | 44% | 2 | 3 | 2 | 1 | Baseline |
| 2026-02-08 | 9 | 6 | 67% | 0 | 4 | 3 | 0 | Improvement |
| 2026-05-07 | 9 | ? | ?% | ? | ? | ? | ? | Target: 89% |

### Trend Analysis Questions

**Compliance trending**:
- Is compliance improving or declining?
- Are we on track to hit targets?
- What's the rate of improvement?

**Issue patterns**:
- Same issues recurring across audits?
- New types of issues emerging?
- Old issues being resolved?

**Standards effectiveness**:
- Are standards clear and achievable?
- Do thresholds need adjustment?
- Are checks catching real problems?

**Process health**:
- Is audit cadence appropriate?
- Are fixes being completed?
- Is effort tracking accurate?

### Document Trends

```markdown
## Trend Analysis

**Overall**: Compliance improved from 44% → 67% (+23 points)

**Positive trends**:
- No critical violations (down from 2)
- Progressive disclosure adoption up 33%

**Concerning trends**:
- High priority violations increased (3 → 4)
- Same skills flagged in both audits (systematic issues)

**Root causes**:
- Refactoring effort focused on critical only
- High priority items deprioritized
- Standards updated but not applied retroactively
```

**Time**: 15 minutes

---

## Step 7: Feed Learnings Back to Standards

Audits reveal whether standards are working. Use findings to refine standards.

### When to Update Standards

#### Many Artifacts Fail Same Check

**Signal**: 50%+ fail same criterion

**Analysis**:
- Is standard unclear?
- Is threshold unrealistic?
- Do examples exist?

**Action**:
- Refine wording for clarity
- Add examples to standard
- Adjust threshold if appropriate
- Document rationale

#### New Issue Pattern Emerges

**Signal**: Same problem across multiple artifacts, but no standard exists

**Analysis**:
- Is this a real quality issue?
- Should it be a standard?
- Can it be automated?

**Action**:
- Add criterion to checklist
- Update automation if possible
- Document in standard

#### Compliance Declining

**Signal**: Compliance drops between audits

**Analysis**:
- Are standards not followed?
- Is process unclear?
- Are tools missing?
- Is governance weak?

**Action**:
- Review process documentation
- Improve tooling/automation
- Increase visibility/accountability
- Revisit governance model

### Document Standards Updates

**In audit log**:
```markdown
## Standards Updates

1. **Updated size threshold**: Reduced from 500 → 400 lines
   - Rationale: 85% of skills under 400, larger skills harder to maintain
   - Effective: 2026-02-08
   - Reference: [[skills/progressive-disclosure-standard]]

2. **Added troubleshooting requirement**: All skills must have troubleshooting section
   - Rationale: 7/9 skills lacked debug guidance, user friction
   - Effective: 2026-02-08
   - Reference: [[skills/structure-standard]]
```

**In standard files**: Update the actual standard documents

**Time**: 1 hour (if standards need updating)

---

## Step 8: Present Summary to User

Deliver concise, actionable audit summary.

### Report Format

```markdown
# [Artifact Type] Audit - [Date]

## Executive Summary

**Compliance**: [X%] ([Y] of [Z] artifacts compliant)
**Status**: [Improving/Declining/Stable] (previous: [X%])
**Critical Issues**: [N] artifacts need immediate attention

## Key Findings

1. **[Most important finding]** - [Impact] - [Recommendation]
2. **[Second finding]** - [Impact] - [Recommendation]
3. **[Third finding]** - [Impact] - [Recommendation]

## Trends (vs Previous Audit)

- Compliance: [X%] → [Y%] ([+/-N] points)
- Critical violations: [N] → [M]
- Pattern: [Key trend identified]

## Systemic Issues

1. **[Cross-artifact problem]**:
   - Affects [N] artifacts
   - Root cause: [Why it's happening]
   - Recommendation: [Systemic fix]

## Action Plan

### Critical (1-2 weeks)
- [Action 1] ([effort])
- [Action 2] ([effort])

### High Priority (3-4 weeks)
- [Action 3] ([effort])
- [Action 4] ([effort])

## Standards Updates

[If standards were updated, summarize changes]

## Next Audit

**Scheduled**: [Date]
**Focus**: [Any special focus areas for next time]
**Target**: [Compliance goal]
```

### Key Messaging

**Be clear**:
- Specific numbers and trends
- Actionable recommendations
- Effort estimates

**Be balanced**:
- Acknowledge improvements
- Highlight concerns
- Celebrate progress

**Be forward-looking**:
- Next steps clear
- Timeline realistic
- Target measurable

**Time**: 15 minutes

---

## Summary Checklist

After completing Phase 2, you should have:

- [ ] Automated checks executed
- [ ] Audit log created (`.claude/auditors/auditor-log-YYYY-MM-DD.md`)
- [ ] Manual assessment completed for flagged artifacts
- [ ] Systemic issues identified
- [ ] Findings prioritized using matrix
- [ ] Action plan created with owners and dates
- [ ] Trends analyzed vs previous audit
- [ ] Standards updated if needed
- [ ] Summary presented to user
- [ ] Next audit date scheduled

**Next**: If violations need fixing, proceed to Phase 3 (Remediation)
