# Audit Setup Guide

**Purpose**: Step-by-step guide for setting up audit infrastructure for a new artifact type.

**When to use**: First-time audit setup for context files, documentation, templates, or custom artifact types.

**See also**: [[SKILL#phase-2-execute-audit]] for running audits once setup is complete.

---

## Overview

Setting up audit for a new artifact type requires:
1. Define what you're auditing (scope)
2. Establish quality criteria (what "good" means)
3. Create automation (quantitative checks)
4. Create checklist (qualitative assessment)
5. Set up tracking (audit logs, trends)
6. Run baseline audit (starting point)
7. Schedule recurring audits (cadence)

**Time investment**: 4-6 hours for first-time setup
**Payoff**: Systematic quality tracking, trend analysis, automated enforcement

---

## Phase 1: Setup (New Artifact Type)

**For setting up audit for a new artifact type:**

### Step 1: Identify Artifact Type

Ask user what needs auditing:
- Skills, Context Files, Documentation, Templates, or Custom

**Examples**:
- **Skills**: Claude Code skills in `.claude/skills/*/SKILL.md`
- **Context**: Context files in `context/**/*.md`
- **Documentation**: Project docs in `docs/**/*.md`
- **Templates**: Note templates in `extras/templates/*.md`
- **Custom**: Any artifact that accumulates or evolves

### Step 2: Define Artifact Scope

**Determine**:
- What type of artifact?
- Where are they located? (glob pattern)
- What to exclude? (archived, deprecated)
- How many artifacts currently?

**Example**:
```yaml
artifact:
  type: "Context Files"
  location: "context/**/*.md"
  exclusions:
    - "context/**/archive/**"
    - "context/_*.md" (indexes)
  count: ~85
```

**Tip**: Use `find` or `glob` to count artifacts before defining scope:
```bash
find context -name "*.md" -not -path "*/archive/*" | wc -l
```

---

### Step 3: Define Quality Criteria

**Quantitative (automatable)**:
- Size limits (line counts, file sizes)
- Required fields/sections (frontmatter, structure)
- Format compliance (YAML syntax, markdown)
- Link integrity (no broken references)
- Metadata validation (dates, tags)
- File organization patterns (naming conventions)

**Qualitative (manual)**:
- Content quality and clarity
- Appropriateness and relevance
- Usability and discoverability
- Maintainability
- Standards alignment

**Read pattern for guidance**: [[context/workflows/patterns/audit-pattern#component-2-quality-criteria]]

**Example criteria for context files**:
```yaml
quantitative:
  size:
    - <300 lines (proactive threshold)
    - <400 lines (watch threshold)
    - <500 lines (hard limit)
  frontmatter:
    - title present
    - category present
    - created date valid
  links:
    - no broken internal links
    - cross-references bidirectional

qualitative:
  relevance:
    - still applicable (not outdated)
    - no redundancy with other context
  clarity:
    - actionable guidance (not vague)
    - concrete examples provided
  currency:
    - updated within last 6 months (or marked stable)
```

---

### Step 4: Create Automation Script

**Identify what can be automated**:
- ✅ File counts, sizes
- ✅ Required field presence
- ✅ Pattern matching (regex)
- ✅ Link validation (internal)
- ✅ Structure validation (sections present)
- ⚠️ Content quality (heuristics only)
- ❌ Appropriateness (requires human judgment)

**Create script**: `.claude/scripts/[artifact-type]-audit.sh`

**Use skill-audit.sh as template**: `.claude/scripts/skill-audit.sh`

**Script should**:
- Check quantitative criteria
- Generate priority levels (CRITICAL/HIGH/MEDIUM/LOW)
- Output terminal report (immediate feedback)
- Output markdown log (persistence)
- Save to `.claude/audits/`

**Example script structure**:
```bash
#!/bin/bash
# context-audit.sh

# Check 1: Size compliance
find context -name "*.md" -exec wc -l {} + | awk '$1 > 500 {print}'

# Check 2: Frontmatter validation
grep -L "^title:" context/**/*.md

# Check 3: Broken links
# ... (validation logic)

# Generate report
echo "## Context Audit - $(date +%Y-%m-%d)" > .claude/audits/context-audit-$(date +%Y-%m-%d).md
```

---

### Step 5: Create Manual Checklist

**Create**: `context/workflows/standards/[artifact-type]-audit-checklist.md`

**Structure** (organize by category):
1. **Structure & Format**
   - Size, frontmatter, required sections
2. **Content Quality**
   - Clarity, examples, actionability
3. **Technical Validation**
   - Links, references, tool usage
4. **Standards Alignment**
   - Follows current standards, consistent
5. **Usability Assessment**
   - Discoverability, cognitive load, navigation
6. **Maintainability**
   - Complexity, ownership, dependencies

**Include**:
- Pass/fail criteria for each check
- Examples of good/bad
- Effort estimates (how long to assess)
- Priority levels (CRITICAL/HIGH/MEDIUM/LOW)

**Use skill-audit-checklist.md as template**: [[skills/audit-checklist]]

**Tip**: Start with 15-20 checks. Add more as patterns emerge from audits.

---

### Step 6: Set Up Audit Tracking

**Create audit log directory** (if doesn't exist):
```bash
mkdir -p .claude/audits
```

**Create README**: `.claude/audits/[artifact-type]-README.md`

**Document**:
- Audit cadence (quarterly, monthly, as-needed)
- How to run audit (command, checklist reference)
- Report format (template)
- Tracking table (trends over time)

**Example tracking table**:
```markdown
## Context Audit History

| Date | Total | Compliant | % | Critical | High | Medium | Notes |
|------|-------|-----------|---|----------|------|--------|-------|
| 2026-02-08 | 85 | 68 | 80% | 0 | 3 | 14 | Baseline audit |
| 2026-05-08 | 92 | 75 | 82% | 0 | 2 | 15 | Q2 audit |
```

---

### Step 7: Run Baseline Audit

**Execute**:
```bash
cd .claude/scripts
./[artifact-type]-audit.sh --verbose
```

**Document baseline**:
- Total artifacts
- Compliance percentage
- Violations by priority
- Common issues

**This becomes starting point** for trend tracking.

**Example baseline**:
```markdown
## Baseline Audit - 2026-02-08

- **Total**: 85 context files
- **Compliant**: 68 (80%)
- **Violations**: 17
  - Critical: 0
  - High: 3 (size >500 lines)
  - Medium: 14 (missing frontmatter fields)

**Common issues**:
1. Outdated "updated" dates (12 files)
2. Missing "applies-to" fields (8 files)
3. Large files >400 lines (3 files)
```

---

### Step 8: Schedule Recurring Audits

Add to calendar based on artifact change frequency:

**High-change artifacts** (quarterly or monthly):
- Skills (evolve frequently)
- Documentation (updates often)
- Active code

**Medium-change artifacts** (quarterly or semi-annually):
- Context files (periodic updates)
- Templates (stable but need review)

**Low-change artifacts** (annually):
- Archived content
- Foundational documents

**Audit depth by frequency**:
- **Quarterly**: Comprehensive (automated + manual assessment)
- **Monthly**: Light (automated only, quick scan)
- **As-needed**: After major changes, validate specific artifacts

**Example calendar entries**:
```
- 2026-05-08: Q2 Context Audit (Comprehensive)
- 2026-06-01: Context Audit Light Check (Automated)
- 2026-07-01: Context Audit Light Check (Automated)
- 2026-08-08: Q3 Context Audit (Comprehensive)
```

---

## Post-Setup: First Audit

After setup is complete, proceed to [[SKILL#phase-2-execute-audit]] for running audits.

**Checklist before first audit**:
- [ ] Artifact scope defined
- [ ] Quality criteria documented
- [ ] Automation script created and tested
- [ ] Manual checklist created
- [ ] Audit tracking set up (.claude/audits/)
- [ ] Baseline audit run
- [ ] Recurring audits scheduled

---

## Domain-Specific Setup Examples

### Skills Audit Setup (Completed)
- **Script**: `.claude/scripts/skill-audit.sh`
- **Checklist**: [[skills/audit-checklist]]
- **Implementation**: [[context/workflows/patterns/implementations/skill-audit-implementation]]
- **Cadence**: Quarterly comprehensive, monthly light

### Context Audit Setup (Planned)
- **Criteria**: Relevance, accuracy, currency, no redundancy
- **Cadence**: Semi-annually (context changes slower)
- **Implementation**: [[context/workflows/patterns/implementations/_future-implementations#1-context-quality-audit]]

### Documentation Audit Setup (Planned)
- **Criteria**: Completeness, accuracy, clarity, working examples
- **Cadence**: Quarterly
- **Implementation**: [[context/workflows/patterns/implementations/_future-implementations#3-documentation-quality-audit]]

---

## Related Documentation

- [[SKILL]] - Main audit orchestration skill
- [[audit-types]] - Audit type details (quality, compliance, security, performance)
- [[patterns/audit-pattern]] - Generic audit pattern (ISO 19011-based)
- [[skills/audit-checklist]] - Example checklist (skills)

---

## Tips for Successful Setup

### Do:
- ✅ Start with 15-20 quality checks (expand later)
- ✅ Automate what you can (quantitative criteria)
- ✅ Run baseline audit immediately (establishes trends)
- ✅ Schedule recurring audits (consistency matters)
- ✅ Use existing audit as template (skills audit proven)

### Don't:
- ❌ Over-engineer with 50+ criteria (diminishing returns)
- ❌ Skip baseline audit (need starting point for trends)
- ❌ Automate everything (some checks need human judgment)
- ❌ Set up without clear quality criteria (what are you measuring?)
- ❌ Forget to schedule recurring audits (one-off audits don't build trends)

---

## Estimated Effort

| Task | Time | Notes |
|------|------|-------|
| Define scope & criteria | 1-2h | Research artifact type, define "good" |
| Create automation script | 2-3h | Use existing script as template |
| Create manual checklist | 1h | 15-20 checks, examples |
| Set up tracking | 30min | Directories, README, table template |
| Run baseline audit | 1-2h | Automated + sample manual review |
| **Total** | **5-8h** | First-time setup investment |

**Ongoing effort**: 3-5 hours per quarter per artifact type (once set up)

---

## Success Criteria

**Setup is complete when**:
- ✅ Can run audit script and get quantitative results
- ✅ Have checklist for manual quality assessment
- ✅ Baseline audit documented (starting point)
- ✅ Recurring audits scheduled
- ✅ Know what "compliant" means for this artifact type

**Setup is successful when** (after 2-3 audits):
- ✅ Compliance trends tracked over time
- ✅ Common issues identified and addressed
- ✅ Standards refined based on findings
- ✅ Audit process smooth and efficient
