# Phase 2: Execute Sync (Quarterly/Recurring)

9-step workflow for running a sync cycle on established domains.

**Time**: ~5 hours per quarter per domain

---

## Step 1: Ask User Which Domain

If not specified, ask which domain to sync:
- Skills (implemented)
- Security (planned)
- Python (planned)
- Context (planned)
- Custom

##Step 2: Load Domain Configuration

Read domain-specific files:
- `context/workflows/processes/[domain]-standards-sync.md` - Sync process
- `context/workflows/standards/[domain]-standards-sync-log.md` - Sync history
- `context/[domain]/*.md` - Current standards

## Step 3: Monitor External Sources

For each source in configuration:
1. WebFetch latest documentation
2. Check release notes (WebSearch)
3. Document: What changed? Breaking? Relevant?

## Step 4: Review Internal Learnings

Read retrospectives since last sync (Glob filter by date).

Extract:
- What worked → Codify
- What failed → Fix standards
- New patterns → Standardize
- Common violations → Clarify standards

## Step 5: Evaluate Candidate Updates

Use evaluation matrix from [[patterns/standards-sync-pattern#component-3-evaluation-criteria]]:

| Criteria | Weight | Assessment |
|----------|--------|------------|
| Relevance | High | Does it apply? |
| Compatibility | High | Breaking change? |
| Value | Medium | Impact on quality? |
| Cost | Medium | Migration effort? |
| Timing | Low | Urgent or defer? |

**Threshold**: 3+ High ratings → Adopt

## Step 6: Update Standards

For approved updates:
1. Edit standard file (Add/update content)
2. Increment version (major.minor.patch)
3. Cross-reference (Link related standards)
4. Document rationale (What, why, impact)

## Step 7: Plan Migration

Assess impact:
- Count affected artifacts (`find` + `wc -l`)
- Run audit if exists (`.claude/scripts/[domain]-audit.sh`)
- Prioritize (critical → nice-to-have)
- Estimate effort
- Set deadlines

## Step 8: Document in Sync Log

Update sync log with:
- External changes reviewed
- Internal learnings
- Standards updates (with versions)
- Migration plan
- Next sync date

## Step 9: Present Summary

Report:
- External changes found
- Internal patterns identified
- Standards updated
- Migration plan
- Next sync date
