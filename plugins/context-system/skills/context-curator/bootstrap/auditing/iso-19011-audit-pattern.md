---
title: Audit Pattern
category: workflow
type: pattern
tags:
- audit
- compliance
- context
- continuous-improvement
- iso-19011
- meta-pattern
- performance
- quality
- security
created: 2026-02-07
updated: 2026-02-08
status: active
---
# Audit Pattern

**Meta-Pattern**: Systematically assess artifacts across multiple dimensions (quality, compliance, security, performance), identify improvements, track trends over time, and feed learnings back into standards.

**Based on**: ISO 19011:2018 (Guidelines for Auditing Management Systems), ISO 25010 (Software Quality), OWASP (Security)

**Applies to**: Any artifact that accumulates or evolves (skills, context files, documentation, code, templates, processes, etc.).

---

## Pattern Overview

```
┌─────────────────────────────────────────────────┐
│  1. Automated Checks                            │
│     - Run quantitative validation               │
│     - Generate baseline metrics                 │
│     - Flag violations automatically             │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  2. Manual Assessment                           │
│     - Deep quality review (checklist)           │
│     - Evaluate flagged items                    │
│     - Identify patterns and root causes         │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  3. Document Findings                           │
│     - Record violations and issues              │
│     - Prioritize by severity/impact             │
│     - Generate audit report                     │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  4. Prioritize & Plan                           │
│     - Categorize: Critical/High/Medium/Low      │
│     - Schedule remediation                      │
│     - Assign ownership                          │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  5. Execute Improvements                        │
│     - Fix violations                            │
│     - Refactor artifacts                        │
│     - Validate changes                          │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  6. Measure & Track Trends                      │
│     - Compare to previous audits                │
│     - Track compliance percentage               │
│     - Identify systemic issues                  │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│  7. Refine Standards                            │
│     - Feed learnings back to standards          │
│     - Update quality criteria                   │
│     - Improve automation                        │
└────────────────┬────────────────────────────────┘
                 │
                 └──────► Next Audit Cycle (Periodic)
```

---

## ISO 19011 Audit Principles

This pattern follows **seven core audit principles** from ISO 19011:2018 (Guidelines for Auditing Management Systems):

### 1. **Integrity** - Foundation of Professionalism

**Principle**: Auditors are ethical, truthful, and accountable.

**Application to artifact auditing**:
- Be honest about findings (don't downplay issues)
- Document actual state, not desired state
- Don't skip violations to inflate compliance metrics
- Admit uncertainty when assessment is subjective

**Example**: If skill exceeds 500 lines, report it as violation even if "it's almost done being refactored."

### 2. **Fair Presentation** - Report Truthfully and Accurately

**Principle**: Audit findings reflect the true condition, with evidence to support claims.

**Application**:
- Provide evidence for violations (line counts, examples, links)
- Distinguish facts from opinions/recommendations
- Balance negative findings with positive observations
- Avoid exaggeration or minimization

**Example**: Don't say "skill is completely unmaintainable" - say "skill has 892 lines (violation: >500 threshold), making navigation difficult."

### 3. **Due Professional Care** - Diligence and Judgment

**Principle**: Apply diligence and judgment in auditing, considering importance and auditor competence limits.

**Application**:
- Allocate time proportional to artifact importance/risk
- Recognize limits (don't audit technical accuracy if lacking expertise)
- Use appropriate depth (comprehensive for critical, light for low-risk)
- Escalate when unsure

**Example**: Critical security-related skills warrant deep manual assessment; low-use archived skills warrant automated-only checks.

### 4. **Confidentiality** - Security of Information

**Principle**: Exercise discretion in use and protection of information acquired during audits.

**Application**:
- Don't publicly share audit findings without authorization
- Store audit reports securely (`.claude/audits/` not public-facing)
- Be careful with examples that might reveal sensitive patterns
- Respect private context (don't audit `context/private/`)

**Example**: If audit reveals security vulnerability, report privately before broad disclosure.

### 5. **Independence** - Basis for Impartiality

**Principle**: Auditors are independent of the activity being audited and free from bias.

**Application**:
- Don't audit your own recent work (wait for perspective)
- Separate roles: don't both create standard AND audit compliance immediately
- Consider peer audits for objectivity
- Acknowledge conflicts of interest

**Example**: If you just refactored a skill, have someone else (or wait 1+ weeks) audit it for objectivity.

### 6. **Evidence-Based Approach** - Rational Method for Reliable Conclusions

**Principle**: Audit conclusions are based on verifiable evidence, not assumptions or feelings.

**Application**:
- **Quantitative evidence**: Line counts, link checks, field presence
- **Qualitative evidence**: Examples of unclear guidance, usability issues documented
- **Trace findings to evidence**: Each violation links to specific check/example
- **Sample appropriately**: Manual reviews sample flagged items + random compliant items

**Example**: Instead of "skill feels bloated," provide "skill is 892 lines (target <500), contains 6 redundant examples (lines 234-456 duplicate 123-345)."

### 7. **Risk-Based Approach** - Consider Risks and Opportunities

**Principle**: Audit process considers risks to achieve audit objectives and minimize disruption.

**Application**:
- **Prioritize high-risk artifacts**: Recently changed, critical functionality, past violations
- **Adjust audit depth**: Deep audit for high-risk, light audit for low-risk
- **Schedule strategically**: Audit before releases, after major changes
- **Resource allocation**: Invest time where problems most likely

**See**: [[#Risk-Based Audit Prioritization]] for detailed framework.

---

## Risk-Based Audit Prioritization

**From ISO 19011**: Build risk-based audit schedules using risk level, performance data, recent changes, and past nonconformities.

### Risk Assessment Framework

**Before each audit cycle**, assess risk for each artifact to prioritize audit effort:

#### Risk Scoring Formula

```
Risk Score = (Impact × Likelihood) + (Change Frequency × Past Issues)

Where:
- Impact: 1-5 (How critical is this artifact?)
- Likelihood: 1-5 (How likely are problems?)
- Change Frequency: 1-5 (How often does it change?)
- Past Issues: 0-5 (How many violations last audit?)
```

#### Impact Rating (1-5)

| Rating | Description | Examples |
|--------|-------------|----------|
| **5** | Critical | Security-related skills, core infrastructure, public-facing docs |
| **4** | High | Frequently-used skills, important context, user-facing docs |
| **3** | Medium | Occasionally-used skills, internal docs, supporting context |
| **2** | Low | Rarely-used skills, archived context, draft docs |
| **1** | Minimal | Deprecated artifacts, personal notes, experimental |

#### Likelihood Rating (1-5)

| Rating | Description | Indicators |
|--------|-------------|------------|
| **5** | Very High | Complex artifact, no automation, past violations, organic growth |
| **4** | High | Medium complexity, partial automation, some past issues |
| **3** | Medium | Moderate complexity, mostly automated checks, occasional issues |
| **2** | Low | Simple artifact, automated, well-maintained |
| **1** | Very Low | Template-generated, fully automated, no history of issues |

#### Change Frequency Rating (1-5)

| Rating | Description | Time Since Last Change |
|--------|-------------|------------------------|
| **5** | Daily | Changes daily/weekly |
| **4** | Weekly | Changes multiple times per month |
| **3** | Monthly | Changes monthly or several times per quarter |
| **2** | Quarterly | Changes once per quarter |
| **1** | Annual | Changes annually or less |

#### Past Issues Rating (0-5)

- **5**: 5+ violations in last audit
- **4**: 3-4 violations
- **3**: 2 violations
- **2**: 1 violation
- **1**: No violations but flagged for watch
- **0**: No issues (clean)

### Risk Categories

**After scoring**, categorize artifacts:

| Risk Score | Category | Audit Depth | Frequency |
|------------|----------|-------------|-----------|
| **25-40** | Critical Risk | Comprehensive (automated + deep manual) | Monthly |
| **15-24** | High Risk | Standard (automated + manual sample) | Quarterly |
| **8-14** | Medium Risk | Light (automated + spot checks) | Semi-annually |
| **4-7** | Low Risk | Automated only | Annually |
| **0-3** | Minimal Risk | Optional (spot audit) | As needed |

### Risk-Based Audit Plan Example

**Skills Audit Q1 2026**:

| Skill | Impact | Likelihood | Change Freq | Past Issues | Risk Score | Category | Audit Depth |
|-------|--------|------------|-------------|-------------|------------|----------|-------------|
| context-update | 5 | 4 | 5 | 3 | 32 | Critical | Comprehensive |
| standards-sync | 5 | 3 | 4 | 0 | 27 | Critical | Comprehensive |
| audit | 4 | 3 | 5 | 0 | 22 | High | Standard |
| systematic-review | 3 | 3 | 4 | 0 | 16 | High | Standard |
| compare | 3 | 2 | 3 | 0 | 11 | Medium | Light |
| diagram | 3 | 2 | 2 | 0 | 9 | Medium | Light |
| recipe-scraper | 2 | 1 | 1 | 0 | 4 | Low | Automated |

**Interpretation**:
- **context-update** (score 32): Comprehensive audit - critical skill, changes frequently, had 3 violations
- **recipe-scraper** (score 4): Automated only - low impact, stable, no past issues

### Applying Risk-Based Prioritization

**Step 1: Score all artifacts** (before quarterly audit)

**Step 2: Prioritize audit effort**:
- Allocate 60% of time to Critical/High risk
- Allocate 30% of time to Medium risk
- Allocate 10% of time to Low risk (or skip)

**Step 3: Adjust audit depth** per category (see table above)

**Step 4: Document risk scores** in audit log for trend tracking

**Step 5: Review risk scores quarterly** - risks change as artifacts evolve

---

## Pattern Components

### Component 1: Artifact Definition

**Define what you're auditing**:

- **Artifact type**: Skills, context files, docs, code, templates
- **Scope**: All instances or subset?
- **Location**: File paths, glob patterns
- **Exclusions**: What to skip (archived, deprecated, etc.)

**Example (Skills)**:
```yaml
artifact:
  type: "Claude Code Skills"
  scope: "All active skills"
  location: ".claude/skills/*/SKILL.md"
  exclusions:
    - ".claude/skills/deprecated/*"
    - ".claude/skills/*/archive/*"
  count: 9
```

**Example (Context)**:
```yaml
artifact:
  type: "Context Files"
  scope: "Active context (not archived)"
  location: "context/**/*.md"
  exclusions:
    - "context/**/archive/**"
    - "context/_*.md" (indexes)
  count: ~85
```

---

### Component 2: Quality Criteria

**Define what "quality" means for your artifact**:

#### Quantitative Criteria (Automatable)

**Structural**:
- Size limits (line count, file size)
- Required sections/fields present
- Format compliance (frontmatter, structure)
- Link integrity (no broken references)

**Metadata**:
- Required fields populated
- Dates valid and current
- Tags follow conventions
- Version information present

**Dependencies**:
- References valid (files exist)
- No circular dependencies
- Deprecated dependencies flagged

**Example (Skills)**:
```yaml
quantitative_criteria:
  size:
    - SKILL.md < 500 lines (violation)
    - SKILL.md < 400 lines (proactive threshold)
    - SKILL.md 200-300 lines (ideal)

  structure:
    - Frontmatter present (name, description, tools)
    - Quick Start section (if >200 lines)
    - Related Documentation section

  links:
    - All internal links resolve
    - No references to deprecated skills
```

#### Qualitative Criteria (Manual Review)

**Content Quality**:
- Clear and actionable guidance
- Concrete examples provided
- Appropriate level of detail
- Up-to-date and accurate

**Usability**:
- Easy to discover and navigate
- Clear entry points
- Appropriate cognitive load
- Self-explanatory

**Maintainability**:
- Not overly complex
- Clear ownership
- Dependencies documented
- Easy to update

**Standards Alignment**:
- Follows current standards
- Consistent with related artifacts
- Reflects best practices

---

### Component 3: Automation Strategy

**What can be automated**:

✅ **Easily automated**:
- Line counts, file sizes
- Required fields present/absent
- Link validation (internal)
- Pattern matching (regex)
- File structure validation

⚠️ **Partially automated**:
- Content quality (heuristics only)
- Duplication detection
- Naming convention compliance
- Reference currency (detect old patterns)

❌ **Requires human judgment**:
- Appropriateness of content
- Clarity and actionability
- Examples quality
- Usability assessment
- Strategic alignment

**Automation approach**:

1. **Identify automatable checks** (from quality criteria)
2. **Choose implementation**:
   - Script (bash, python)
   - Git hooks (pre-commit)
   - CI/CD (GitHub Actions)
   - Manual commands
3. **Generate reports**:
   - Terminal output (immediate feedback)
   - Markdown log (persisted)
   - Metrics dashboard (trends)
4. **Set thresholds**:
   - Critical (must fix)
   - High (schedule soon)
   - Medium (next cycle)
   - Low (monitor)

**Example**:
```bash
#!/bin/bash
# skill-audit.sh

# Check 1: Size compliance
find .claude/skills -name "SKILL.md" -exec wc -l {} + | sort -n

# Check 2: Frontmatter validation
grep -L "^name:" .claude/skills/*/SKILL.md

# Check 3: Broken links
# ... (validation logic)

# Output: audit-log-YYYY-MM-DD.md
```

---

### Component 4: Manual Review Process

**Checklist-driven assessment**:

1. **Create comprehensive checklist**:
   - Organized by category (structure, content, technical, usability)
   - Clear pass/fail criteria
   - Examples of good/bad
   - Effort estimate per check

2. **Review workflow**:
   - Start with automated results (what's flagged?)
   - Use checklist for deep assessment
   - Document findings per artifact
   - Note patterns across artifacts

3. **Efficiency strategies**:
   - Review flagged items first (automated triage)
   - Sample compliant items (validate automation)
   - Focus on recent changes (delta audits)
   - Time-box reviews (avoid perfectionism)

**Example checklist structure**:
```markdown
## Artifact: [name]

### Automated Checks
- [ ] Size: [PASS/FAIL] ([count] lines)
- [ ] Frontmatter: [PASS/FAIL]
- [ ] Links: [PASS/FAIL] ([broken] broken)

### Manual Assessment
- [ ] Content quality: [1-5 rating]
- [ ] Usability: [1-5 rating]
- [ ] Maintainability: [1-5 rating]

### Issues Found
1. [Priority] [Description]

### Recommendation
- [Action] [Estimated effort]
```

---

### Component 5: Reporting & Tracking

**Audit report structure**:

```markdown
# [Artifact Type] Audit - [Date]

## Executive Summary
- Total artifacts: [count]
- Compliant: [count] ([percent]%)
- Violations: [breakdown by severity]
- Trend: [improving/stable/declining]

## Detailed Findings

### Critical Issues (Fix Immediately)
[List with priority, impact, effort]

### High Priority (Schedule This Cycle)
[List]

### Medium Priority (Next Cycle)
[List]

### Watch List
[Items approaching threshold]

## Systemic Issues
[Patterns observed across multiple artifacts]

## Recommendations
[Prioritized action items]

## Trend Analysis
[Comparison to previous audits]

## Next Audit
[Date, focus areas]
```

**Tracking over time**:

| Audit Date | Total | Compliant | % | Critical | High | Medium | Notes |
|------------|-------|-----------|---|----------|------|--------|-------|
| 2026-02-07 | 9 | 6 | 67% | 0 | 3 | 0 | Baseline after refactoring |
| 2026-05-07 | TBD | TBD | TBD | TBD | TBD | TBD | Q2 audit |

**Success metrics**:
- Compliance percentage (target: >80%)
- Trend direction (improving over time)
- Time to remediation (how fast issues fixed)
- Issue recurrence rate (same problems returning?)

---

### Component 6: Prioritization Framework

**Severity classification**:

**Critical** (Fix immediately):
- Breaks functionality
- Security vulnerability
- Data loss risk
- Blocking others' work

**High** (Schedule this cycle):
- Major quality issue
- Standards violation
- Significant technical debt
- Usability problem

**Medium** (Next cycle):
- Minor quality issue
- Approaching threshold
- Nice-to-have improvement
- Optimization opportunity

**Low** (Monitor/Backlog):
- Cosmetic issue
- Edge case
- Unclear benefit
- Aspirational improvement

**Effort estimation**:
- Quick fix: <30 minutes
- Small: 1-2 hours
- Medium: Half day
- Large: Full day
- Very large: Multi-day

**Priority matrix**:

| Severity | Quick | Small | Medium | Large | Very Large |
|----------|-------|-------|--------|-------|------------|
| Critical | DO NOW | DO NOW | DO NOW | DO NOW | Plan carefully |
| High | Do this cycle | Do this cycle | Do this cycle | Plan & schedule | Consider breaking down |
| Medium | Nice wins | Next cycle | Next cycle | Backlog | Reconsider value |
| Low | Opportunistic | Backlog | Backlog | Probably not | Don't do |

---

### Component 7: Remediation Workflow

**Fix violations**:

1. **Create action plan**:
   - List all violations
   - Prioritize by matrix above
   - Assign ownership
   - Set target dates

2. **Execute fixes**:
   - Start with critical/high
   - Batch similar fixes (efficiency)
   - Test changes
   - Document what was done

3. **Validate**:
   - Re-run automated checks
   - Verify manual criteria
   - Check for regressions
   - Mark as complete

4. **Track completion**:
   - Progress percentage
   - Blockers/challenges
   - Completion date
   - Outcome

---

### Component 8: Standards Feedback Loop

**Learn from audits**:

**If many artifacts fail same check**:
→ Standard may be unclear or unrealistic
→ Refine standard definition
→ Add examples to clarify
→ Consider if threshold appropriate

**If new issue pattern emerges**:
→ Missing quality criterion
→ Add to checklist
→ Update automation if possible
→ Document in standards

**If compliance declining**:
→ Process not being followed
→ Standards drifting from practice
→ Need better tooling/automation
→ Review governance/ownership

**If compliance improving**:
→ Standards working
→ Continue current approach
→ Consider raising bar
→ Document success patterns

**Continuous improvement**:
- Update quality criteria based on findings
- Improve automation based on manual patterns
- Refine checklist based on effectiveness
- Evolve standards based on real-world experience

---

## Audit Cadence Recommendations

### By Artifact Type

**High-change artifacts** (monthly or quarterly):
- Skills (evolve frequently)
- Documentation (updates often)
- Active code (commits daily/weekly)

**Medium-change artifacts** (quarterly or semi-annually):
- Context files (periodic updates)
- Templates (stable but need review)
- Standards documents (evolve with learnings)

**Low-change artifacts** (annually):
- Archived content (verify still relevant)
- Foundational documents (rarely change)
- Historical records (completeness check)

### By Audit Depth

**Light audit** (monthly): Automated only, quick scan
**Standard audit** (quarterly): Automated + sample manual review
**Deep audit** (annually): Comprehensive manual assessment

---

## Implementation Checklist

**Setting up audit for a new artifact type**:

- [ ] **Define artifacts**: Type, scope, location
- [ ] **Establish quality criteria**: Quantitative + qualitative
- [ ] **Automate what you can**: Script or tool for checks
- [ ] **Create manual checklist**: For deeper assessment
- [ ] **Set up reporting**: Log format and location
- [ ] **Define cadence**: How often to audit
- [ ] **Baseline audit**: Establish starting point
- [ ] **Schedule recurring audits**: Calendar reminders

**Running an audit cycle**:

- [ ] **Run automated checks**: Generate metrics and flags
- [ ] **Manual review**: Use checklist on flagged items
- [ ] **Document findings**: Create audit report
- [ ] **Prioritize issues**: Severity + effort matrix
- [ ] **Create action plan**: Owners and deadlines
- [ ] **Execute fixes**: Remediate violations
- [ ] **Validate changes**: Re-check compliance
- [ ] **Track trends**: Compare to previous audits
- [ ] **Update standards**: Feed learnings back

---

## Pattern Implementations

### Active Implementations

- [[implementations/skill-audit-implementation]] - Claude Code skill quality auditing
- [[implementations/context-audit-implementation]] - Context system health checks (future)
- [[implementations/docs-audit-implementation]] - Documentation quality audits (future)

### How to Implement This Pattern

**For a new artifact type**:

1. **Read this pattern** to understand the framework
2. **Identify your artifacts**: What needs auditing?
3. **Define quality criteria**: What makes it "good"?
4. **Map to components**:
   - What can be automated?
   - What requires manual review?
   - How to prioritize findings?
   - How to track over time?
5. **Build tooling**:
   - Automation script (if applicable)
   - Manual checklist
   - Report template
6. **Run baseline audit**: Establish starting point
7. **Set cadence**: Schedule recurring audits

**Use the `/audit` skill** to orchestrate the process across artifact types.

---

## Success Criteria

**Effective audit process**:
- ✅ Regular cadence maintained (not one-off)
- ✅ Automation reduces manual burden
- ✅ Findings actionable and prioritized
- ✅ Trends tracked over time
- ✅ Learnings feed back to standards
- ✅ Compliance improving or stable

**Warning signs** (audit not working):
- ❌ Audits skipped or delayed
- ❌ Findings not acted upon
- ❌ Same issues every audit (no learning)
- ❌ Compliance declining
- ❌ No ownership/accountability
- ❌ Report created but not used

---

## Related Patterns

- [[standards-sync-pattern]] - Complements this pattern (sync updates quality criteria)
- [[processes/phased-execution]] - Remediation can use phased approach
- [[context-system/context-governance]] - Governance framework includes audits

---

## Further Reading

- [[implementations/skill-audit-implementation]] - Detailed example for Claude Code skills
- [[skills/audit-checklist]] - Example manual checklist
- `.claude/scripts/skill-audit.sh` - Example automation script

---

## Quick Reference

**When to use this pattern**: Any artifact that accumulates, evolves, or can degrade over time.

**Core cycle**: Automate → Manual → Document → Prioritize → Fix → Track → Learn → (repeat)

**Key success factor**: Balance automation (efficiency) with manual judgment (quality).

**Avoid**: One-time audit without follow-up (trends and learning require repetition).
