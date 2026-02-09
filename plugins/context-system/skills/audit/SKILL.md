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

**What do you need help with?**

1. **Understand audit types** (quality, compliance, security, performance, comprehensive)
   - See [[audit-types.md]] for detailed comparison and selection guide

2. **Set up audits for new artifact type** (first-time setup)
   - See [[audit-setup-guide.md]] for 8-step setup process (5-8 hours)

3. **Run audit on existing artifact type** (quarterly/recurring)
   - See [[phase-2-execute-audit.md]] for 8-step execution workflow (3-5 hours)

4. **Fix violations from audit** (remediation)
   - See [[phase-3-remediation.md]] for remediation process

5. **Domain-specific guidance** (skills, context, docs, templates)
   - See [[domain-workflows.md]] for artifact-specific workflows

6. **Ready to audit** → Continue with overview below

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
- Claude Code Skills (active - see [[domain-workflows.md#claude-code-skills]])
- Context files (planned)
- Documentation (planned)
- Templates (planned)
- Code/security (planned)
- Any artifact that accumulates or evolves

**For detailed audit type comparison**: See [[audit-types.md]]

---

## Phase 1: Setup (New Artifact Type)

**For setting up audit infrastructure for a new artifact type (first-time setup).**

### Process Overview

**8-Step Setup**:
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

**Already implemented**:
- Skills audit (`.claude/scripts/skill-audit.sh` + checklist)
- See [[domain-workflows.md#claude-code-skills]]

**For detailed setup instructions**: See [[audit-setup-guide.md]]

---

## Phase 2: Execute Audit (Quarterly/Recurring)

**For running an audit cycle on established artifact types.**

### Process Overview

**8-Step Execution Workflow**:

1. **Ask user which artifact type** (skills, context, docs, templates, custom)
2. **Run automated checks** (execute `.claude/scripts/[type]-audit.sh`)
3. **Manual assessment** (apply checklist to flagged artifacts)
4. **Document findings** (update audit log with manual assessment)
5. **Prioritize findings** (use priority matrix: Critical/High/Medium/Low)
6. **Track trends** (compare to previous audits, analyze patterns)
7. **Feed learnings to standards** (refine standards based on findings)
8. **Present summary** (deliver actionable report to user)

**Time estimate**: 3-5 hours per quarter per artifact type

**Outputs**:
- Audit log (`.claude/audits/audit-log-YYYY-MM-DD.md`)
- Compliance metrics (percentage, trend analysis)
- Prioritized action plan (violations by priority)
- Standards updates (if needed)

**For detailed step-by-step workflow**: See [[phase-2-execute-audit.md]]

---

## Phase 3: Execute Remediation (As Needed)

**For fixing violations identified in audit.**

### Process Overview

**4-Step Remediation Workflow**:

1. **Create remediation plan** (group by type, assign owners, set deadlines)
2. **Execute fixes** (apply appropriate fix workflow per violation type)
3. **Validate changes** (re-run audit, verify compliance improved)
4. **Document results** (update audit log, commit changes, mark complete)

**Common fix types**:
- **Size violations**: Refactoring (extract reference files)
- **Missing sections**: Add troubleshooting, limitations, examples
- **Broken links**: Fix paths, update references
- **Format violations**: Apply standards, fix formatting

**Efficiency patterns**:
- Batch similar fixes together
- Reuse patterns across artifacts
- Automate where possible
- Test after each batch

**For detailed remediation guidance**: See [[phase-3-remediation.md]]

---

## Domain-Specific Workflows

Different artifact types have specialized quality criteria and audit processes.

### Claude Code Skills

**Status**: ✅ Fully implemented

**Automation**: `.claude/scripts/skill-audit.sh`
**Checklist**: [[skills/audit-checklist]]
**Cadence**: Quarterly comprehensive, monthly light
**Refactoring**: [[skills/refactoring-workflow]]

### Other Artifact Types

**Context Files**: 🚧 Planned (semi-annual audit)
**Documentation**: 🚧 Planned (quarterly audit)
**Templates**: 🚧 Planned (annual audit)
**Code/Security**: 🚧 Planned (monthly/quarterly)

**For detailed domain guidance**: See [[domain-workflows.md]]

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

---

## Troubleshooting

### Symptom: Automated script fails or returns errors

**Cause**: Script not executable, dependencies missing, or path issues

**Fix**:
- Make script executable: `chmod +x .claude/scripts/[type]-audit.sh`
- Run from correct directory: `cd .claude/scripts`
- Check dependencies (e.g., `wc`, `grep`, `find` available)

### Symptom: Compliance percentage seems wrong

**Cause**: Threshold misconfigured or artifacts miscounted

**Fix**:
- Review script logic (check threshold values)
- Verify artifact count (script may exclude/include unexpected files)
- Compare manual count vs script count

### Symptom: Manual assessment taking too long

**Cause**: Assessing too many artifacts or too detailed

**Fix**:
- Focus on flagged artifacts only (automated checks filter)
- Use checklist as guide, not exhaustive review
- Time-box assessment (30 min per artifact max)
- For initial audits, sample approach acceptable

### Symptom: Same violations recurring across audits

**Cause**: Standards unclear, fixes not applied, or process not followed

**Fix**:
- Review standards for clarity (add examples)
- Check if remediation completed (were fixes actually applied?)
- Improve automation (catch violations earlier)
- Review governance (why are standards not followed?)

### Symptom: Unsure how to prioritize findings

**Cause**: Multiple violations with unclear impact

**Fix**:
- Use priority matrix from [[phase-2-execute-audit.md#step-5-prioritize-findings]]
- Focus on severity first (Critical > High > Medium > Low)
- Then consider effort (Quick wins vs large projects)
- Ask: "What breaks user experience most?"

---

## Known Limitations

**Cannot audit**:
- Artifacts with no quantifiable criteria (purely subjective)
- One-off artifacts (need 5+ to justify setup)
- Rapidly changing artifacts (audit overhead exceeds value)

**Automation limitations**:
- Qualitative assessment always requires human judgment
- Context-dependent criteria hard to automate
- Some quality dimensions resist quantification (clarity, usability)

**Workarounds**:
- **Few artifacts**: Manual periodic review instead of full audit
- **Subjective criteria**: Peer review or user feedback instead of audit
- **Rapid change**: Lightweight checks (linting) instead of comprehensive audit

**Process limitations**:
- Initial setup time-intensive (5-8 hours)
- Quarterly audits require 3-5 hours time commitment
- Remediation can be significant effort (10-40 hours)

**When audit skill may not be worth it**:
- <5 artifacts in category
- Artifacts very stable (rarely change)
- Low impact artifacts (internal tools, temporary)
- No automation possible (100% manual assessment)

---

## Related Documentation

**Pattern**:
- [[patterns/audit-pattern]] - Generic pattern this implements (ISO 19011-based)

**Reference Files (This Skill)**:
- [[audit-types.md]] - Five audit types (quality, compliance, security, performance, comprehensive)
- [[audit-setup-guide.md]] - 8-step setup for new artifact types
- [[phase-2-execute-audit.md]] - 8-step execution workflow (quarterly audits)
- [[phase-3-remediation.md]] - 4-step remediation process (fixing violations)
- [[domain-workflows.md]] - Domain-specific guidance (skills, context, docs, templates)

**Active Implementations**:
- [[context/workflows/patterns/implementations/skill-audit-implementation]] - Skills example
- [[context/workflows/patterns/implementations/_future-implementations]] - Future artifact types

**Domain-Specific Resources**:
- [[skills/audit-checklist]] - Skills quality checklist
- `.claude/scripts/skill-audit.sh` - Skills automation script
- [[skills/refactoring-workflow]] - Refactoring process for size violations
