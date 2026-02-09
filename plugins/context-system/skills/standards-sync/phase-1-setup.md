# Phase 1: Setup (New Domain)

**For setting up standards synchronization for a new domain (first-time configuration).**

**Use this phase when**: You need to establish sync infrastructure for a domain that doesn't have external source monitoring yet.

**Time estimate**: 2-4 hours for initial setup

---

## Step 1: Identify Domain

Ask user what domain needs sync. Common domains:
- **Skills** (Claude Code skills development)
- **Security** (security practices, OAuth, auditing)
- **Python** (coding conventions, tooling)
- **Context** (context management patterns)
- **Documentation** (documentation standards)
- **Research** (research methodology)
- **Custom** (user-defined domain)

---

## Step 2: Identify External Sources

For the chosen domain, define authoritative sources to monitor.

### Source Configuration

**For each source, document**:
- **Source name** (e.g., "Anthropic Claude Code Docs")
- **URL** (documentation homepage, GitHub, etc.)
- **Authority level**:
  - **Official**: First-party documentation (Anthropic, OWASP)
  - **Community**: Respected community resources (production patterns, frameworks)
- **Check frequency**:
  - **Quarterly**: Most domains (balances currency vs overhead)
  - **Monthly**: Rapidly evolving (security, AI model providers)
  - **Annually**: Stable domains (context principles, PKM practices)
- **What to monitor**:
  - Breaking changes (API deprecations, methodology shifts)
  - New patterns (emerging best practices)
  - Deprecations (outdated approaches to remove)
  - Recommendations (official guidance updates)

### Examples

**Skills domain**:
- Anthropic Claude Code Documentation (official, quarterly)
- Claude Code GitHub repo (official, quarterly)
- Awesome Claude Code community (community, quarterly)

**Security domain**:
- OWASP Top 10 (official, quarterly)
- Python Security best practices (official, quarterly)
- OAuth 2.1 specification (official, annually)

**Guidance**: See [[patterns/standards-sync-pattern#component-1-external-sources-configuration]]

---

## Step 3: Map Internal Standards

Identify which internal standards files need to be kept in sync.

### Discovery Commands

```bash
# Find existing standards for domain
grep -r "standard" context/[domain]/*.md

# Find best practices docs
grep -r "best-practices" context/**/*.md

# Find process docs
ls context/workflows/processes/*-[domain]-*.md

# Check decision records
ls context/decisions/*-[domain]-*.md
```

### Document Internal Standards

**For each standard, capture**:
- **Standard name** (e.g., "Progressive Disclosure Standard")
- **File path** (`context/skills/progressive-disclosure-standard.md`)
- **Current version** (v1.0.0 or date-based)
- **Last updated** (date)
- **Affected implementations** (what artifacts follow this standard)
  - Example: "All skills in `.claude/skills/`"
- **Audit exists?** (Yes/No - does automation check compliance?)

### Example

**Skills domain internal standards**:
- structure-standard.md → All SKILL.md files
- execution-standards.md → All skills
- progressive-disclosure-standard.md → Skills >300 lines
- reference-organization.md → Skills with reference files

---

## Step 4: Create Sync Process Documentation

Create domain-specific sync process file.

### File Location

`context/workflows/processes/[domain]-standards-sync.md`

Examples:
- `context/workflows/processes/skills-standards-sync.md`
- `context/workflows/processes/security-standards-sync.md`

### Template

```markdown
---
title: [Domain] Standards Synchronization
category: workflow
type: process
tags:
  - standards
  - [domain]
  - sync
created: YYYY-MM-DD
---

# [Domain] Standards Synchronization

**Pattern**: [[patterns/standards-sync-pattern]]

**Purpose**: Keep [domain] standards aligned with external best practices from [list key sources].

---

## External Sources

| Source | Authority | URL | Frequency | Focus |
|--------|-----------|-----|-----------|-------|
| [Name 1] | Official | [URL] | Quarterly | [What to watch] |
| [Name 2] | Community | [URL] | Quarterly | [What to watch] |

---

## Internal Standards

| Standard | Path | Version | Affected Artifacts | Audit |
|----------|------|---------|---------------------|-------|
| [Name] | context/[domain]/[file] | v1.0 | [Description] | [Yes/No] |

---

## Sync Cadence

**Frequency**: [Quarterly/Monthly/Annually]

**Next scheduled sync**: YYYY-MM-DD

**Trigger conditions** (ad-hoc syncs):
- Major external update announced
- Significant internal pattern changes
- Quality degradation detected

---

## Evaluation Criteria

[Domain-specific decision framework for adopting external updates]

**Adopt if**:
- [Criterion 1]
- [Criterion 2]

**Reject if**:
- [Criterion 1]
- [Criterion 2]

---

## Related

- **Pattern**: [[patterns/standards-sync-pattern]]
- **Implementation**: [[context/workflows/patterns/implementations/[domain]-sync-implementation]]
- **Sync Log**: [[context/workflows/standards/[domain]-standards-sync-log]]
```

---

## Step 5: Create Sync Log

Create tracking document to record all sync cycles.

### File Location

`context/workflows/standards/[domain]-standards-sync-log.md`

### Template

Use [[skills/standards-sync-log]] as example template.

**Structure**:
```markdown
---
title: [Domain] Standards Sync Log
domain: [domain]
type: tracking
---

# [Domain] Standards Sync Log

Tracks synchronization between external best practices and internal [domain] standards.

**Pattern**: [[patterns/standards-sync-pattern]]
**Process**: [[context/workflows/processes/[domain]-standards-sync]]

---

## Sync History

### Sync: YYYY-MM-DD (Q[N] [YEAR])

**External Changes Reviewed**:
- [Source]: [Summary of changes]

**Internal Learnings**:
- [Pattern identified]

**Standards Updates**:
- Updated [standard-name] v[X.Y.Z]
  - **What**: [Description]
  - **Why**: [Rationale]
  - **Impact**: [Affected artifacts]
  - **Migration**: [Yes/No]

**Next Sync**: YYYY-MM-DD

---

[Template repeats for each sync cycle]
```

---

## Step 6: Register in Sync Registry

Add domain to central registry.

### Update Registry

File: `context/context-system/standards-sync-registry.md`

**Add entry**:
```markdown
| Domain | Status | Next Sync | Process | Log |
|--------|--------|-----------|---------|-----|
| [Domain] | ✅ Active | YYYY-MM-DD | [[processes/[domain]-standards-sync]] | [[standards/[domain]-sync-log]] |
```

---

## Step 7: Schedule First Sync

Add to calendar or reminder system.

**Recommendations**:
- **Quarterly domains**: Q1 (Feb), Q2 (May), Q3 (Aug), Q4 (Nov)
- **Monthly domains**: First week of each month
- **Annual domains**: Beginning of fiscal/calendar year

**Buffer**: Add 1-week buffer before deadline for flexibility

---

## Success Criteria

Setup is complete when:

- [ ] Domain identified and sources defined
- [ ] Internal standards mapped
- [ ] Sync process documentation created
- [ ] Sync log initialized
- [ ] Registry updated
- [ ] First sync scheduled
- [ ] User understands process

**Result**: Infrastructure ready for first sync cycle
