## Context Extraction Patterns

### Pattern 1: Repeated Preference

**Signals**:
- User says "I prefer..." or "Always..."
- User corrects same thing multiple times
- Consistent pattern across conversations

**Example**:
```
User: "Please don't use emojis in responses"
[Later in conversation]
User: "Again, no emojis please"
```

**Extract to**: `communication/style-preferences.md`

---

### Pattern 2: Technical Standard

**Signals**:
- References external authority (PEP 8, OWASP)
- Code pattern user follows consistently
- Quality requirement stated

**Example**:
```
User: "Store credentials in OS keychain following OWASP A02"
```

**Extract to**: `security/best-practices.md` (with OWASP link)

---

### Pattern 3: Architectural Decision

**Signals**:
- Choice between alternatives
- Rationale provided ("because...")
- Significant implications
- Won't change frequently

**Example**:
```
User: "Use flat folder structure with MOCs for navigation instead of nested folders because it scales better with 100+ files"
```

**Extract to**: `decisions/YYYY-MM-DD-flat-structure.md`

---

### Pattern 4: Workflow/Process

**Signals**:
- Multi-step process
- "When doing X, follow these steps..."
- Quality checkpoints mentioned

**Example**:
```
User: "When creating commits: 1) Run tests, 2) Add files specifically, 3) Write conventional commit message, 4) Include co-author"
```

**Extract to**: Depends on discovered domains
- If `git/` exists → `git/commit-workflow.md`
- If `workflows/` exists → `workflows/git-commits.md`
- Otherwise ask user which domain

---

