## Edge Cases

### Case 1: Unclear Which Domain

If pattern doesn't clearly map to a domain:

```
This pattern could fit in multiple domains:
- security/best-practices.md (security aspect)
- python/error-handling.md (implementation aspect)

Which domain is primary for this context?
```

Use AskUserQuestion to clarify.

### Case 2: Domain Doesn't Exist Yet

If pattern suggests new domain:

```
This pattern relates to [topic], but you don't have a context/[topic]/ domain yet.

Would you like to:
1. Create new domain: context/[topic]/
2. Add to existing domain: context/[closest-match]/
3. Skip for now
```

If creating new domain:
1. Create `context/[topic]/_index.md` with "When to Use"
2. Create initial file with extracted content
3. Update `context/_index.md`
4. Update `context/context-system/loading-map.md`

### Case 3: Conflicting Context

If new context conflicts with existing:

```
⚠️ Conflict detected:

Existing (context/python/conventions.md):
"Use 79 character line length"

New (from conversation):
"Use 100 character line length"

Which should I keep?
1. Keep existing (79 chars)
2. Update to new (100 chars)
3. Document both with conditions
```

If updating:
1. Update file with new content
2. Create decision log explaining change
3. Update "Last updated" timestamp

### Case 4: Too Much Context

If extraction creates >10 new items:

```
I identified 15 context items to extract, which might be overwhelming.

Would you like to:
1. Extract all 15 items now
2. Prioritize top 5 most important
3. Extract by domain (do one domain at a time)
```

---

