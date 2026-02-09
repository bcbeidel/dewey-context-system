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

**What do you need help with?**

1. **Understand sync process** → Read overview below

2. **Set up sync for new domain** (first-time configuration)
   - See [[phase-1-setup.md]] for 7-step setup (2-4 hours)

3. **Run quarterly sync** (existing domain)
   - See [[phase-2-execute-sync.md]] for 9-step workflow (~5 hours)

4. **Apply standards updates** (migration)
   - See [[phase-3-migration.md]] for 3-step migration process

5. **Domain-specific guidance** (skills, security, Python, context)
   - See [[domain-workflows.md]] for configured domains

6. **Check sync registry** → See [[context-system/standards-sync-registry]]

---

## Overview

This skill follows the [[patterns/standards-sync-pattern|Standards Sync Pattern]]:

**Core cycle**:
```
Monitor External Sources → Evaluate Relevance → Update Internal Standards → Migrate Implementations → Measure Results
```

**Active domains** (see [[domain-workflows.md]] for complete list):
- ✅ Skills development - [[skills/standards-sync]] (Q2 2026: May 7)
- ✅ Security standards - [[security/standards-sync]] (Q2 2026: May 8)
- ⏳ Python, Context, Research - Planned

**Registry**: [[context-system/standards-sync-registry]]

---

## Phase 1: Setup (New Domain)

**For setting up sync infrastructure for a new domain (first-time configuration).**

### Process Overview

**7-Step Setup**:
1. Identify domain (skills, security, Python, context, custom)
2. Identify external sources (URLs, authority, frequency)
3. Map internal standards (files, versions, affected artifacts)
4. Create sync process documentation (`context/workflows/processes/[domain]-sync.md`)
5. Create sync log (`context/workflows/standards/[domain]-sync-log.md`)
6. Register in sync registry
7. Schedule first sync

**Time**: 2-4 hours

**Output**: Infrastructure ready for quarterly sync cycles

**For detailed setup instructions**: See [[phase-1-setup.md]]

---

## Phase 2: Execute Sync (Quarterly/Recurring)

**For running a sync cycle on established domains.**

### Process Overview

**9-Step Sync Workflow**:
1. Ask user which domain
2. Load domain configuration
3. Monitor external sources (WebFetch + WebSearch)
4. Review internal learnings (retrospectives)
5. Evaluate candidate updates (evaluation matrix)
6. Update standards (edit files, version increment)
7. Plan migration (assess impact, prioritize)
8. Document in sync log
9. Present summary to user

**Time**: ~5 hours per quarter per domain

**Outputs**:
- Updated standards (with version increments)
- Migration plan (if artifacts affected)
- Sync log entry

**For detailed step-by-step workflow**: See [[phase-2-execute-sync.md]]

---

## Phase 3: Execute Migration (As Needed)

**For applying standards updates to affected artifacts.**

### Process Overview

**3-Step Migration**:
1. Prioritize migrations (critical → high → medium)
2. Execute updates (batch similar changes)
3. Validate compliance (run audit if exists)

**Patterns**:
- **Immediate**: Security fixes, breaking changes
- **Phased**: Large scope (week-by-week)
- **Opportunistic**: Low priority (fix when touching file)

**For detailed migration guidance**: See [[phase-3-migration.md]]

---

## Domain-Specific Workflows

**Active**:
- **Skills**: [[skills/standards-sync]] (quarterly, 3 sources, next: 2026-05-07)

**Planned**:
- **Security**: Quarterly (OWASP, Python Security, OAuth 2.1, CVE)
- **Python**: Quarterly (PEPs, best practices, type checking)
- **Context**: Annually (PKM, note-taking research)
- **Research**: Annually (PRISMA, systematic review methods)

**For domain details**: See [[domain-workflows.md]]

---

## Integration

**Works with**:
- `/audit` - Audit identifies gaps, sync addresses them
- `/context-curator` - Extract patterns, feed into sync
- Domain-specific skills - Implement updated standards

**Complements**:
- [[patterns/audit-pattern]] - Audits validate sync effectiveness

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
- Security: TBD (setup first)

---

## Troubleshooting

### Symptom: External source unavailable or changed URL

**Cause**: Documentation moved, site redesign, or service down

**Fix**:
- Search for new URL (WebSearch: "[source name] documentation 2026")
- Update sync process file with new URL
- Document change in sync log

### Symptom: Unsure if external update is relevant

**Cause**: Update applies to different use case or context

**Fix**:
- Use evaluation matrix from [[phase-2-execute-sync.md#step-5-evaluate-candidate-updates]]
- Focus on relevance and compatibility criteria
- When in doubt, defer to next sync (quarterly check prevents stale)

### Symptom: Migration plan too large to execute

**Cause**: Many affected artifacts or high-effort changes

**Fix**:
- Break into phases (critical → high → medium)
- Use opportunistic pattern (fix when touching file)
- Consider if standard needs adjustment (too aggressive?)

### Symptom: Internal standards and external sources diverging

**Cause**: Not syncing regularly, or intentional local adaptation

**Fix**:
- If intentional: Document rationale in standard file
- If missed syncs: Catch up with backlog review
- If fundamental mismatch: Re-evaluate external source choice

---

## Known Limitations

**Cannot sync**:
- Sources requiring authentication (paywalls, private repos)
- Sources without version history (can't detect changes)
- Rapidly changing sources (daily/weekly updates - overhead too high)

**Workarounds**:
- **Paywalled sources**: Manual review by authorized user, summarize findings
- **No version history**: Use announcement channels (mailing lists, blogs)
- **Rapid changes**: Curated summaries (monthly digests vs daily tracking)

**Process limitations**:
- Manual evaluation required (can't fully automate adoption decisions)
- Quarterly cadence may miss urgent changes (rely on ad-hoc triggers)
- Migration effort can be significant (10-40 hours for large updates)

**When sync may not be worth it**:
- Very stable domain (no external updates for years)
- No clear authoritative sources (fragmented best practices)
- Few affected artifacts (<5 implementations)

---

## Related Documentation

**Pattern**:
- [[patterns/standards-sync-pattern]] - Generic pattern this implements

**Reference Files (This Skill)**:
- [[phase-1-setup.md]] - 7-step setup for new domains
- [[phase-2-execute-sync.md]] - 9-step sync execution workflow
- [[phase-3-migration.md]] - 3-step migration process
- [[domain-workflows.md]] - Domain-specific configurations

**Active Implementations**:
- [[skills/sync-implementation]] - Skills sync example
- [[patterns/future-implementations]] - Future domains (security, Python, context)

**Registry**:
- [[context-system/standards-sync-registry]] - Central tracking of all domains
