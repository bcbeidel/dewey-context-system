# Phase 3: Execute Migration

3-step process for applying standards updates to affected artifacts.

**Use when**: Standards changes require artifact updates

---

## Step 1: Prioritize Migrations

Use priority matrix:
- **Critical/Urgent**: Security fixes, breaking changes
- **High-impact**: Widely-used artifacts
- **Quick wins**: Low effort, clear benefit

## Step 2: Execute Updates

For each artifact:
1. Read current state
2. Apply standard changes
3. Test/validate
4. Mark complete in migration plan

**Batch similar changes** for efficiency

## Step 3: Validate Compliance

Run audit (if exists):
```bash
./scripts/[domain]-audit.sh
```

Verify:
- Compliance improved?
- No regressions?
- Migration complete?

---

## Migration Patterns

### Pattern 1: Immediate (Critical)
- Security vulnerabilities
- Breaking API changes
- Fix all affected artifacts immediately

### Pattern 2: Phased (Large scope)
- Week 1-2: Critical artifacts
- Week 3-4: High-priority artifacts
- Week 5-6: Remaining artifacts

### Pattern 3: Opportunistic (Low priority)
- Fix when touching file for other reasons
- "Leave it better than you found it"
- Track as bonus compliance

---

## Success Criteria

- [ ] All critical migrations complete
- [ ] High-priority migrations complete or scheduled
- [ ] Compliance metrics improved
- [ ] No new violations introduced
- [ ] Sync log updated with results
