# Index Update Quick Reference

Use this template when Step 7.4 validation fails to quickly fix index mismatches.

## Domain Index Update Template

**File**: `context/[DOMAIN]/_index.md`

### Fix 1: Add Missing File to All Files Table

**Location**: `## All Files (N)` section

**Calculate size indicator**:
```bash
lines=$(wc -l < context/[DOMAIN]/[FILENAME].md)
# 🟢 if <150, 🟡 if 150-400, 🔴 if >400
```

**Add row (alphabetically)**:
```markdown
| [[domain/filename|filename.md]] | 🟢/🟡/🔴 | First 60 chars of purpose |
```

---

### Fix 2: Update File Count

**Location**: `## All Files (N)` header

**Count actual files**:
```bash
find context/[DOMAIN] -name "*.md" -not -name "_index.md" | wc -l
# Result: X files
```

**Update header**:
```markdown
## All Files (N) → ## All Files (X)
```

---

### Fix 3: Update Large File Count

**Location**: `**Note**: N files >150 lines...`

**Count large files**:
```bash
find context/[DOMAIN] -name "*.md" -not -name "_index.md" -exec wc -l {} \; | \
  awk '$1 > 150' | wc -l
# Result: Y files
```

**Update note**:
```markdown
**Note**: N files >150 lines → **Note**: Y files >150 lines
```

---

## Main Index Update Template

**File**: `context/_index.md`

### Fix 1: Update Total File Count

**Location**: `**Total**: N files across 17 domains`

**Count total files**:
```bash
find context -name "*.md" \
  -not -name "_index.md" \
  -not -path "*/archive/*" \
  -not -path "*/private/*" | wc -l
# Result: Z files
```

**Update total**:
```markdown
**Total**: N files → **Total**: Z files
```

---

### Fix 2: Update Domain File Count

**Location**: "All Domains" section

**Get domain count** (from domain index):
```bash
grep "^## All Files (" context/[DOMAIN]/_index.md | grep -o '([0-9]\+)'
# Result: (X)
```

**Update domain line**:
```markdown
- **[[domain/_index|Domain Name]]** (N files) → (X files)
```

---

### Fix 3: Sync Domain Counts

**If domain index says X but main index says Y**:

1. **Verify domain count is correct**:
   ```bash
   find context/[DOMAIN] -name "*.md" -not -name "_index.md" | wc -l
   ```

2. **Update whichever is wrong** (usually domain index is canonical)

3. **Make them match**

---

## Validation

**After updates, re-run**:
```bash
.claude/scripts/context-curator-validate-indexes.sh
```

**Expected**: All ✅, no ❌

**If still failing**: Check for:
- Typos in file counts
- Missing domain in main index
- Incorrect grep patterns (domain name mismatch)
