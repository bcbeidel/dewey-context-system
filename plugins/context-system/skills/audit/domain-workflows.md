# Domain-Specific Audit Workflows

Specialized audit workflows tailored to specific artifact types.

**Purpose**: Different artifact types have different quality criteria, automation scripts, and cadences. This guide provides domain-specific guidance.

---

## Claude Code Skills

**Status**: ✅ Fully implemented with automation

### Configuration

**Checklist**: [[skills/audit-checklist]]
**Automation**: `.claude/scripts/skill-audit.sh`
**Cadence**: Quarterly comprehensive, monthly light checks
**Implementation**: [[context/workflows/patterns/implementations/skill-audit-implementation]]

### Quality Criteria

**Automated checks**:
- Size thresholds (Ideal <300, Watch <400, Violation ≥400)
- Structure validation (frontmatter, sections)
- Link validation (wikilinks, relative paths)
- Progressive disclosure (reference file organization)

**Manual assessment**:
- Content quality (clear, accurate, complete)
- Usability (Quick Start, examples, troubleshooting)
- Maintainability (organization, naming, documentation)
- Standards alignment (follows structure-standard, execution-standards)

### Audit Process

1. Run `.claude/scripts/skill-audit.sh --verbose`
2. Review automated findings
3. Apply [[skills/audit-checklist]] to flagged skills
4. Document in `.claude/audits/skills-audit-YYYY-MM-DD.md`
5. If violations found, use [[skills/refactoring-workflow]]

### Typical Findings

**Common issues**:
- Size violations (skills approaching/exceeding 400 lines)
- Missing Quick Start sections
- Missing troubleshooting guidance
- Missing known limitations
- Reference files not used when >400 lines

**Remediation**:
- Refactor using progressive disclosure pattern
- Extract reference files (3-6 optimal)
- Add Quick Start navigation
- Add troubleshooting + limitations sections

---

## Context Files

**Status**: 🚧 Planned (infrastructure not yet implemented)

### Quality Criteria

**Relevance**:
- Content still applicable?
- Decisions still valid?
- Patterns still used?

**Accuracy**:
- Information correct?
- Examples work?
- Links valid?

**Currency**:
- Recently updated?
- Reflects current practices?
- No stale references?

**No Redundancy**:
- Information not duplicated?
- Cross-references used appropriately?
- Single source of truth maintained?

### Audit Process (When Implemented)

1. **Identify stale content** (not updated in 6+ months)
2. **Check for duplication** (grep for repeated content)
3. **Validate links** (check all wikilinks resolve)
4. **Review decisions** (are documented decisions still followed?)
5. **Assess relevance** (is content still needed?)

### Cadence

**Semi-annually** (context changes slower than code):
- Q2 audit: May/June
- Q4 audit: November/December

**Why less frequent**: Context files are more stable than skills; over-auditing creates maintenance burden.

### Implementation Plan

See [[context/workflows/patterns/implementations/_future-implementations#1-context-quality-audit]]

---

## Documentation

**Status**: 🚧 Planned (infrastructure not yet implemented)

### Quality Criteria

**Completeness**:
- All features documented?
- All edge cases covered?
- All examples provided?

**Accuracy**:
- Instructions work?
- Code examples run?
- Links valid?
- Screenshots current?

**Clarity**:
- Easy to understand?
- Well-organized?
- Good use of examples?
- Appropriate level of detail?

### Audit Process (When Implemented)

1. **Test all code examples** (run them, verify output)
2. **Click all links** (ensure navigation works)
3. **Check screenshots** (are they current?)
4. **Assess completeness** (are any features undocumented?)
5. **Review clarity** (can a new user follow it?)

### Cadence

**Quarterly**:
- After major feature releases
- After significant changes
- Regular Q1, Q2, Q3, Q4 audits

### Implementation Plan

See [[context/workflows/patterns/implementations/_future-implementations#3-documentation-quality-audit]]

---

## Templates

**Status**: 🚧 Planned (infrastructure not yet implemented)

### Quality Criteria

**Standards Compliance**:
- Matches current standards?
- All required fields present?
- Correct formatting?

**Documentation**:
- Fields explained?
- Examples provided?
- Usage notes clear?

**Skills Integration**:
- Skills use templates correctly?
- Template-first principle followed?
- No hardcoded formats in skills?

### Audit Process (When Implemented)

1. **Compare templates to standards**
2. **Check skills usage** (do skills read template?)
3. **Validate field completeness** (all necessary fields present?)
4. **Test template usage** (create note with template, verify format)
5. **Document any discrepancies**

### Cadence

**Annually** or when standards change:
- Templates are very stable
- Changes to standards trigger template review
- Ad-hoc audits when skills report template issues

### Implementation Plan

See [[context/workflows/patterns/implementations/_future-implementations#5-template-audit]]

---

## Code & Security

**Status**: 🚧 Planned (infrastructure not yet implemented)

### Quality Criteria (Security)

**OWASP Top 10 Compliance**:
- Injection vulnerabilities (SQL, command, XSS)
- Broken authentication
- Sensitive data exposure
- XML external entities
- Broken access control
- Security misconfiguration
- Cross-site scripting (XSS)
- Insecure deserialization
- Components with known vulnerabilities
- Insufficient logging & monitoring

**Dependency Security**:
- Known CVEs in dependencies?
- Outdated packages?
- Unmaintained dependencies?

### Quality Criteria (Code)

**Maintainability**:
- Clear structure?
- Well-documented?
- Consistent style?

**Testing**:
- Tests present?
- Coverage adequate?
- Tests passing?

### Audit Process (When Implemented)

**Security**:
1. Run `npm audit` or equivalent
2. Check for OWASP Top 10 vulnerabilities
3. Review authentication/authorization
4. Check credential storage
5. Validate input sanitization

**Code**:
1. Run linters
2. Check test coverage
3. Review recent changes
4. Identify technical debt

### Cadence

**Security**: Monthly (rapid threat landscape changes)
**Code Quality**: Quarterly (aligns with feature releases)

---

## Custom Artifact Type

**When to use**: You have a specific artifact type not covered above

### Setup Process

Follow **Phase 1 (Setup)** from main SKILL.md:

1. **Identify artifact type** (what are you auditing?)
2. **Define artifact scope** (location, count, exclusions)
3. **Define quality criteria** (what makes it "good"?)
4. **Create automation** (shell script for quantitative checks)
5. **Create checklist** (markdown doc for qualitative checks)
6. **Set up tracking** (`.claude/audits/` directory, tracking table)
7. **Run baseline audit** (establish starting point)
8. **Schedule cadence** (quarterly, monthly, annually?)

### Time Investment

**Initial setup**: 5-8 hours
**Quarterly audits**: 3-5 hours
**Annual maintenance**: 2-3 hours

### ROI Threshold

**Worth auditing if**:
- 10+ artifacts in category
- Artifacts evolve over time
- Quality matters (user-facing, critical)
- Automation possible (quantitative checks)

**Not worth auditing if**:
- Few artifacts (<5)
- Very stable (rarely change)
- Low impact (internal, temporary)
- No automatable criteria (pure judgment)

---

## Comparison Matrix

| Artifact Type | Status | Cadence | Automation | Time per Audit | Maturity |
|---------------|--------|---------|------------|----------------|----------|
| **Skills** | ✅ Active | Quarterly | Full | 3-5 hours | Mature |
| **Context** | 🚧 Planned | Semi-annual | Partial | 2-4 hours | Planned |
| **Documentation** | 🚧 Planned | Quarterly | Partial | 3-4 hours | Planned |
| **Templates** | 🚧 Planned | Annual | Manual | 1-2 hours | Planned |
| **Code/Security** | 🚧 Planned | Monthly/Quarterly | Full | 2-3 hours | Planned |

**Legend**:
- ✅ Active: Fully implemented and in use
- 🚧 Planned: Designed but not yet implemented
- Automation: Full (script + checklist), Partial (checklist only), Manual (no automation)

---

## Adding New Domain

When you implement a new domain-specific workflow:

1. **Document here** (add new section to this file)
2. **Update main SKILL.md** (add to Domain-Specific Workflows section)
3. **Create implementation** (add to `patterns/implementations/`)
4. **Update tracking** (add to comparison matrix)

**Goal**: Keep domain workflows centralized for easy reference
