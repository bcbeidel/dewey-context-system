---
name: standards-sync
description: "Orchestrate synchronization between external best practices and internal standards across any domain"
allowed-tools: Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, AskUserQuestion, Bash
---

# Standards Synchronization

**Meta-Skill**: Orchestrate synchronization between external authoritative sources and internal standards for any domain.

**When to use**: Quarterly sync cycles, after discovering external updates, when standards feel outdated.

**Pattern**: Implements [[patterns/standards-sync-pattern]]

---

## Quick Start

Choose your entry point:
- **Check which domains need sync** → See [[context-system/standards-sync-registry]] (centralized registry)
- **Run quarterly sync** → See [Phase 2: Execute Sync](#phase-2-execute-sync)
- **Set up new domain** → See [Phase 1: Setup](#phase-1-setup)
- **Need examples** → See implementations: [[skills/sync-implementation]] | [[patterns/future-implementations]]

---

## Overview

This skill follows the [[patterns/standards-sync-pattern|Standards Sync Pattern]]:

**Core cycle**:
```
Monitor External Sources → Evaluate Relevance → Update Internal Standards → Migrate Implementations → Measure Results
```

**Configured domains** (see [[context-system/standards-sync-registry]] for complete list):
- ✅ Skills development - [[skills/standards-sync]] (Q2 2026 sync: May 7)
- ✅ Security standards - [[security/standards-sync]] (Q2 2026 sync: May 8)
- ⏳ Python standards - Planned
- ⏳ Research methods - Planned
- ⏳ Quality auditing - Planned
- Any domain with external authorities

---

## Phase 1: Setup (New Domain)

**For setting up sync for a new domain:**

### Step 1: Identify Domain

Ask user what domain needs sync:
- Skills, Security, Context, Documentation, or Custom

### Step 2: Identify External Sources

**For user's chosen domain, define**:
- Source name and URL
- Authority level (official vs community)
- Check frequency (quarterly, monthly, annually)
- What to monitor (breaking changes, new patterns, deprecations)

**Read pattern for guidance**: [[context/workflows/patterns/standards-sync-pattern#component-1-external-sources-configuration]]

### Step 3: Map Internal Standards

**Identify internal documentation**:
```bash
# Find existing standards for domain
grep -r "standard" context/project/*.md
grep -r "best-practices" context/**/*.md

# Find relevant process docs
ls context/workflows/processes/*-[domain]-*.md
```

**Document**:
- Standard name and path
- Current version
- Last updated date
- What implementations/artifacts affected

### Step 4: Create Sync Process Documentation

**Create**: `context/workflows/processes/[domain]-standards-sync.md`

**Structure**:
```markdown
---
title: [Domain] Standards Synchronization
category: workflow
type: process
---

# [Domain] Standards Synchronization

**Pattern**: [[patterns/standards-sync-pattern]]

## External Sources
[List with URLs, authority, frequency]

## Internal Standards
[List with paths, versions, affected artifacts]

## Sync Cadence
[Quarterly/Monthly/Annually]

## Evaluation Criteria
[Domain-specific decision framework]

## Related
- Pattern: [[patterns/standards-sync-pattern]]
- Implementation: [[context/workflows/patterns/implementations/[domain]-sync-implementation]]
```

### Step 5: Create Sync Log

**Create**: `context/workflows/standards/[domain]-standards-sync-log.md`

**Use template** from [[skills/standards-sync-log]] as example.

### Step 6: Schedule First Sync

Add to calendar with appropriate cadence.

---

## Phase 2: Execute Sync (Quarterly/Recurring)

**For running a sync cycle:**

### Step 1: Ask User Which Domain

If not specified, ask which domain to sync:
- Skills (implemented)
- Security (planned)
- Context (planned)
- Documentation (planned)
- Custom

### Step 2: Load Domain Configuration

**Read domain-specific documentation**:
```bash
# Load sync process
Read: context/workflows/processes/[domain]-standards-sync.md

# Load sync log (track changes)
Read: context/workflows/standards/[domain]-standards-sync-log.md

# Load current standards (what we're syncing)
Read: context/project/[domain]-*.md
```

### Step 3: Monitor External Sources

**For each external source**:

1. **Fetch latest documentation**:
   ```bash
   WebFetch: [source-url]
   Prompt: "Summarize any changes since [last-check-date]. Focus on: [domain-focus-areas]"
   ```

2. **Check release notes** (if applicable):
   ```bash
   WebSearch: "[project-name] releases [current-year]"
   ```

3. **Document findings**:
   - What changed?
   - Effective date?
   - Breaking change?
   - Relevance to our domain?

### Step 4: Review Internal Learnings

**Read retrospectives since last sync**:
```bash
Glob: context/workflows/retrospectives/*.md
Filter: created >= [last-sync-date]
```

**Extract patterns**:
- What worked well → Codify
- What went poorly → Fix standards
- New patterns emerged → Candidate for standardization
- Common violations → Standard unclear

### Step 5: Evaluate Candidate Updates

**For each potential update**:

Use evaluation matrix from [[context/workflows/patterns/standards-sync-pattern#component-3-evaluation-criteria]]:

| Criteria | High | Medium | Low | Reject |
|----------|------|--------|-----|--------|
| Relevance | ✓ | ✓ | | |
| Compatibility | ✓ | | ✓ | |
| Value | ✓ | ✓ | | |
| Cost | ✓ | | ✓ | |
| Timing | ✓ | | ✓ | |

**Threshold**: 3+ High → Immediate action

### Step 6: Update Standards

**For approved updates**:

1. **Edit relevant standard file**:
   ```bash
   Edit: context/project/[standard-name].md
   - Add/update content
   - Increment version (major.minor.patch)
   - Document in version history
   ```

2. **Cross-reference**:
   - Link related standards
   - Update indexes (context/_index.md)
   - Update CLAUDE.md if vault-level

3. **Document rationale**:
   - What changed and why
   - External source or internal learning
   - Impact on implementations

### Step 7: Plan Migration

**Assess impact**:
```bash
# Count affected artifacts
find [artifact-location] -name "[pattern]" | wc -l

# Identify violations (if audit exists)
./scripts/[domain]-audit.sh
```

**Create migration plan**:
- List affected artifacts
- Prioritize (critical → nice-to-have)
- Estimate effort
- Set target completion
- Assign ownership

### Step 8: Document in Sync Log

**Update sync log**:
```markdown
## Sync: YYYY-MM-DD (Q[N] [YEAR])

### External Changes Reviewed
- Source 1: [summary]
- Source 2: [summary]

### Internal Learnings Reviewed
- Retrospectives: [count] ([date range])
- Key patterns: [list]

### Standards Updates Made
- Updated: [standard-name] v[X.Y.Z]
  - What: [description]
  - Why: [rationale]
  - Impact: [affected artifacts]
  - Migration: [Yes/No - plan]

### Action Items
- [ ] Migrate [count] artifacts
- [ ] Schedule follow-up

### Next Sync
Date: [3 months from now]
```

### Step 9: Present Summary to User

**Report**:
- External changes found
- Internal patterns identified
- Standards updated (with versions)
- Migration plan (if needed)
- Next sync date

---

## Phase 3: Execute Migration (As Needed)

**If standards changes require artifact updates:**

### Step 1: Prioritize Migrations

Use priority matrix:
- Critical/urgent first
- High-impact artifacts
- Quick wins (low effort, clear benefit)

### Step 2: Execute Updates

**For each artifact**:
1. Read current state
2. Apply standard changes
3. Test/validate
4. Mark complete in migration plan

### Step 3: Validate Compliance

**Run audit** (if exists):
```bash
./scripts/[domain]-audit.sh
```

**Verify**:
- Compliance improved?
- No regressions?
- Migration complete?

---

## Domain-Specific Workflows

### For Claude Code Skills

**Use**: [[skills/standards-sync]]

**External sources**: Anthropic docs, Claude Code GitHub, community
**Cadence**: Quarterly
**Implementation**: [[skills/sync-implementation]]

### For Security Practices (Future)

**External sources**: OWASP, NIST, Python Security, CVE databases
**Cadence**: Quarterly (security evolves quickly)
**Implementation**: [[patterns/future-implementations#2-security-best-practices-sync]]

### For Context System (Future)

**External sources**: Teresa Torres context patterns, PKM best practices
**Cadence**: Annually (context principles stable)
**Implementation**: [[patterns/future-implementations#1-context-quality-audit]]

### For Custom Domain

Follow Phase 1 (Setup) to define sources, standards, and process.

---

## Integration

**Works with**:
- `/audit` - Audit identifies gaps, sync addresses them
- `/context-update` - Extract patterns, feed into sync process
- Domain-specific skills - Implement updated standards

**Complements**:
- [[patterns/audit-pattern]] - Audits validate sync effectiveness

---

## Related Documentation

**Pattern**:
- [[patterns/standards-sync-pattern]] - Generic pattern this implements

**Active Implementations**:
- [[skills/sync-implementation]] - Skills example
- [[patterns/future-implementations]] - Future domains

**Domain-Specific Processes**:
- [[skills/standards-sync]] - Skills sync process
- [[skills/standards-sync-log]] - Skills sync log

---

## Quick Reference

**Quarterly sync workflow**:
1. Monitor external sources (30 min)
2. Review internal learnings (1 hour)
3. Evaluate updates (1 hour)
4. Update standards (2 hours)
5. Plan migration (30 min)
6. Document in sync log (30 min)

**Total time**: ~5 hours per quarter per domain

**Next sync dates**:
- Skills: 2026-05-07 (Q2)
- Security: TBD (set up first)
- Context: TBD (set up first)
