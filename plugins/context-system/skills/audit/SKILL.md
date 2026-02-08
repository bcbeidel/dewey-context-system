---
name: audit
description: "Orchestrate systematic audits (quality, compliance, security, performance) across any artifact type with automated checks, manual assessment, and trend tracking"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Audit

**Meta-Skill**: Orchestrate systematic audits for any artifact type across multiple dimensions (quality, compliance, security, performance), combining automated checks with manual assessment and trend tracking.

**When to use**: Quarterly comprehensive audits, monthly light checks, before major releases, when quality/compliance/security degrades.

**Pattern**: Implements [[patterns/audit-pattern]]

**Standards**: ISO 19011:2018 (Auditing Management Systems), ISO 25010 (Software Quality), OWASP (Security)

---

## Quick Start

**What type of audit do you need?**

1. **Quality audit** → Assess usability, maintainability, clarity (ISO 25010 dimensions)
2. **Compliance audit** → Check standards adherence, required fields, format validation
3. **Security audit** → Vulnerability assessment, OWASP compliance, dependency scanning
4. **Performance audit** → Size limits, efficiency, resource usage
5. **Comprehensive audit** → All dimensions (recommended quarterly)

**Then:**
- **Run audit** → See [Phase 2: Execute Audit](#phase-2-execute-audit)
- **Set up new artifact type** → See [Phase 1: Setup](#phase-1-setup)
- **Need examples** → See [[#audit-types]] or implementations: [[context/workflows/patterns/implementations/skill-audit-implementation]]

---

## Overview

This skill follows the [[patterns/audit-pattern|Audit Pattern]] based on ISO 19011:2018 principles:

**Core cycle**:
```
Risk Assessment → Automate Checks → Manual Assessment → Document Findings → Prioritize → Fix → Track Trends → Refine Standards
```

**Supports multiple audit types**:
- **Quality audits** - Usability, maintainability, clarity (ISO 25010)
- **Compliance audits** - Standards adherence, format validation
- **Security audits** - OWASP, vulnerability scanning, dependency checks
- **Performance audits** - Size, efficiency, resource usage
- **Comprehensive audits** - All dimensions combined

**Supports multiple artifact types**:
- Claude Code Skills (active - see [[context/workflows/patterns/implementations/skill-audit-implementation]])
- Context files (planned)
- Documentation (planned)
- Templates (planned)
- Code/security (planned)
- Any artifact that accumulates or evolves

---

## Audit Types

The audit skill supports five audit types based on ISO 19011:2018 and ISO 25010:2023:

| Type | Purpose | Standards | When to Use |
|------|---------|-----------|-------------|
| **Quality** | Assess 8 ISO 25010 dimensions (usability, maintainability, etc.) | ISO 25010 | Quarterly, after refactoring |
| **Compliance** | Verify standards adherence, format validation | Internal standards | Before releases, quarterly |
| **Security** | Identify vulnerabilities, OWASP compliance | OWASP Top 10:2025 | After deps update, quarterly |
| **Performance** | Assess efficiency, resource usage | Internal thresholds | When performance degrades |
| **Comprehensive** | All dimensions combined | All above | Quarterly (recommended) |

**For detailed audit type documentation**: See [[audit-types]]

**Quick selection guide**:
- Quality issues? → Quality Audit (ISO 25010 eight dimensions)
- Standards not followed? → Compliance Audit
- Security concerns? → Security Audit (OWASP, CVE scanning)
- Performance degraded? → Performance Audit
- Regular quarterly review? → Comprehensive Audit (all dimensions)

---

## Phase 1: Setup (New Artifact Type)

**For setting up audit infrastructure for a new artifact type (first-time setup):**

**8-Step Setup Process**:
1. Identify artifact type (skills, context, docs, templates, custom)
2. Define artifact scope (location, exclusions, count)
3. Define quality criteria (quantitative + qualitative)
4. Create automation script (`.claude/scripts/[type]-audit.sh`)
5. Create manual checklist (`context/workflows/standards/[type]-audit-checklist.md`)
6. Set up audit tracking (`.claude/audits/` directory, README, table)
7. Run baseline audit (establish starting point)
8. Schedule recurring audits (quarterly/monthly/as-needed)

**Time investment**: 5-8 hours for first-time setup
**Payoff**: Systematic quality tracking, trend analysis, automated enforcement

**For detailed setup instructions**: See [[audit-setup-guide]]

**Already implemented**:
- Skills audit (`.claude/scripts/skill-audit.sh` + checklist)
- See [[context/workflows/patterns/implementations/skill-audit-implementation]]

---

## Phase 2: Execute Audit (Quarterly/Recurring)

**For running an audit cycle:**

### Step 1: Ask User Which Artifact Type

If not specified, ask what to audit:
- Skills (implemented)
- Context (planned)
- Documentation (planned)
- Templates (planned)
- Custom

### Step 2: Run Automated Checks

**Execute audit script**:
```bash
cd .claude/scripts
./[artifact-type]-audit.sh --verbose
```

**Review output**:
- Terminal report (immediate feedback)
- Audit log: `.claude/audits/audit-log-YYYY-MM-DD.md`
- Violations by priority
- Compliance percentage

**Time**: 5-15 minutes

### Step 3: Manual Assessment

**For flagged artifacts**:

1. **Load checklist**:
   ```bash
   Read: context/workflows/standards/[artifact-type]-audit-checklist.md
   ```

2. **For each flagged artifact**:
   - Apply manual checklist
   - Document findings
   - Rate quality dimensions (1-5)
   - List specific issues
   - Recommend actions

3. **Identify patterns**:
   - Same issue across multiple artifacts?
   - Systemic problems vs one-offs?
   - Root causes?

**Time**: 15-30 minutes per artifact

### Step 4: Document Comprehensive Findings

**Update audit log with manual findings**:

```markdown
## Manual Assessment

### Artifact: [name]

**Automated**:
- Size: [PASS/FAIL] ([count])
- Structure: [PASS/FAIL]
- Links: [PASS/FAIL] ([broken])

**Manual** (1-5 rating):
- Content quality: [rating]
- Usability: [rating]
- Maintainability: [rating]

**Issues**:
1. [Priority] [Description]

**Recommendation**:
- [Action] [Effort estimate]
```

**Identify systemic issues**:
- Patterns observed across artifacts
- Common violations
- Standards gaps

### Step 5: Prioritize Findings

**Use priority matrix** from [[context/workflows/patterns/audit-pattern#component-6-prioritization-framework]]:

| Severity | Quick Fix | Small | Medium | Large |
|----------|-----------|-------|--------|-------|
| Critical | DO NOW | DO NOW | DO NOW | DO NOW |
| High | This cycle | This cycle | This cycle | Plan |
| Medium | Nice win | Next cycle | Next cycle | Backlog |
| Low | Opportunistic | Backlog | Backlog | Don't do |

**Create action plan**:
- List prioritized issues
- Assign owners
- Set target dates
- Track completion

### Step 6: Track Trends

**Compare to previous audits**:

| Date | Total | Compliant | % | Critical | High | Medium | Notes |
|------|-------|-----------|---|----------|------|--------|-------|
| [Previous] | X | Y | Z% | A | B | C | [notes] |
| [Current] | X | Y | Z% | A | B | C | [notes] |

**Analyze**:
- Compliance improving/declining?
- Same issues recurring?
- New patterns emerging?
- Standards working?

### Step 7: Feed Learnings Back to Standards

**If standards need updating**:

**Many artifacts fail same check**:
→ Standard may be unclear
→ Refine wording, add examples
→ Consider if threshold appropriate

**New issue pattern emerges**:
→ Missing quality criterion
→ Add to checklist
→ Update automation if possible

**Compliance declining**:
→ Process not followed
→ Need better tooling
→ Review governance

**Update standards documentation** and note in audit log.

### Step 8: Present Summary to User

**Report**:
- **Summary**: Total artifacts, compliance %, violations breakdown
- **Key findings**: Top 3-5 issues
- **Trends**: Comparison to previous audit
- **Systemic issues**: Cross-artifact patterns
- **Recommendations**: Prioritized action items
- **Standards updates**: If refinements needed
- **Next audit**: Scheduled date

---

## Phase 3: Execute Remediation (As Needed)

**If violations need fixing:**

### Step 1: Create Remediation Plan

**From prioritized findings**:
- List all violations
- Group by type (efficiency)
- Assign owners
- Set deadlines

### Step 2: Execute Fixes

**For each violation**:
1. Read artifact
2. Apply fix (follow refactoring workflow if exists)
3. Test/validate
4. Mark complete

**For systematic fixes**:
- Batch similar changes
- Consider automation
- Update documentation

### Step 3: Validate Changes

**Re-run audit**:
```bash
./[artifact-type]-audit.sh
```

**Verify**:
- Violations resolved?
- No regressions?
- Compliance improved?

### Step 4: Document Results

**Update audit log**:
- Remediation actions taken
- Violations resolved
- Compliance change
- Time invested

---

## Domain-Specific Workflows

### For Claude Code Skills

**Use**: [[skills/audit-checklist]]

**Automated**: `.claude/scripts/skill-audit.sh`
**Cadence**: Quarterly comprehensive, monthly light
**Implementation**: [[context/workflows/patterns/implementations/skill-audit-implementation]]

**Refactoring**: [[skills/refactoring-workflow]]

### For Context Files (Future)

**Quality criteria**: Relevance, accuracy, currency, no redundancy
**Cadence**: Semi-annually (context changes slower)
**Implementation**: [[context/workflows/patterns/implementations/_future-implementations#1-context-quality-audit]]

### For Documentation (Future)

**Quality criteria**: Completeness, accuracy, clarity, examples working
**Cadence**: Quarterly
**Implementation**: [[context/workflows/patterns/implementations/_future-implementations#3-documentation-quality-audit]]

### For Templates (Future)

**Quality criteria**: Matches standards, all fields documented, skills use correctly
**Cadence**: Annually or when standards change
**Implementation**: [[context/workflows/patterns/implementations/_future-implementations#5-template-audit]]

### For Custom Artifact Type

Follow Phase 1 (Setup) to define scope, criteria, and process.

---

## Integration

**Works with**:
- `/standards-sync` - Sync updates audit criteria (quality, compliance, security)
- `/context-update` - Audit findings feed into context updates
- Domain-specific refactoring workflows - Fix violations
- Security workflows - Security audits integrate with OWASP practices

**Complements**:
- [[patterns/standards-sync-pattern]] - Sync keeps audit criteria current

---

## Related Documentation

**Pattern**:
- [[patterns/audit-pattern]] - Generic pattern this implements (ISO 19011-based)

**Active Implementations**:
- [[context/workflows/patterns/implementations/skill-audit-implementation]] - Skills example
- [[context/workflows/patterns/implementations/_future-implementations]] - Future artifact types

**Domain-Specific Checklists**:
- [[skills/audit-checklist]] - Skills checklist

**Automation**:
- `.claude/scripts/skill-audit.sh` - Skills audit script

---

## Quick Reference

**Quarterly audit workflow**:
1. Run automated checks (5-15 min)
2. Manual assessment of flagged items (1-2 hours)
3. Document findings (30 min)
4. Prioritize issues (30 min)
5. Track trends (15 min)
6. Update standards if needed (1 hour)
7. Present summary (15 min)

**Total time**: 3-5 hours per quarter per artifact type

**Next audit dates**:
- Skills: 2026-05-07 (Q2)
- Context: TBD (set up first)
- Documentation: TBD (set up first)

**Compliance target**: >80% for most artifact types
