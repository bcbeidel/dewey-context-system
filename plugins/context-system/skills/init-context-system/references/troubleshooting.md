# Troubleshooting

## Existing context/ Directory

If `context/` already exists:

**Ask user intent**:
```
I notice you already have a context system.

Would you like to:
1. Extend it (add more domains)
2. Validate it (run quality checks)
3. Migrate it (convert to concept-based if needed)
4. Start fresh (backup and rebuild)
```

### Option 1: Extend
- Read existing `context/_index.md` to discover current domains
- Suggest complementary domains based on discovery questions
- Create new domains without touching existing ones

### Option 2: Validate
- Run quality checks (see `/audit` skill)
- Check for concept-based vs type-based organization
- Verify frontmatter, links, structure

### Option 3: Migrate
- If current structure is type-based (standards/, preferences/, workflows/):
  - Explain concept-based benefits
  - Propose migration plan
  - Create backup first
  - Map existing files to new domains

### Option 4: Start Fresh
```bash
# Backup existing
mv context/ context-backup-$(date +%Y%m%d)/

# Run setup
# (proceed with Phase 1)
```

---

## No User Domains Identified

If discovery questions don't clearly map to specific domains:

**Always recommend at least one starter domain:**
- `learning/` - General learning preferences and patterns
- `workflows/` - General workflows and processes
- `patterns/` - Reusable patterns

**Rationale**: Ensures system is useful immediately, even if domains aren't obvious yet.

---

## Custom Domain Creation

If user wants a domain not in standard recommendations:

1. **Validate domain makes sense**:
   - Is it a topic/concept (not a document type)?
   - Will multiple files fit this topic?
   - Is there an external authority to ground it in?

2. **Create domain structure**:
   ```bash
   mkdir -p context/custom-domain/
   ```

3. **Create _index.md** with:
   - When to Use guidance
   - External Authorities (if applicable)
   - File listing

4. **Update main index** and loading map

---

## Domain Naming Conventions

**Good domain names** (concept-based):
- `python/` - Programming language
- `security/` - Security standards
- `research/` - Research methods
- `obsidian/` - Tool-specific conventions

**Bad domain names** (type-based):
- `standards/` - What kind of standards?
- `preferences/` - Preferences about what?
- `conventions/` - Too vague
- `documents/` - Document type, not topic

**Test**: Can you fill in the blank? "Load context/___/ when working on ___"
- Good: "Load context/python/ when working on Python code"
- Bad: "Load context/standards/ when working on ???"

---

## Migration from Type-Based to Concept-Based

If user has existing type-based structure:

**Example migration**:
```
OLD (type-based):
context/
├── standards/
│   ├── python-pep8.md
│   ├── security-owasp.md
│   └── skill-structure.md
└── preferences/
    ├── communication.md
    └── git-workflow.md

NEW (concept-based):
context/
├── python/
│   └── coding-conventions.md    # was standards/python-pep8.md
├── security/
│   └── best-practices.md        # was standards/security-owasp.md
├── skills/
│   └── structure-standard.md    # was standards/skill-structure.md
├── communication/
│   └── style-preferences.md     # was preferences/communication.md
└── git/
    └── workflow.md              # was preferences/git-workflow.md
```

**Migration process**:
1. Identify topic for each existing file
2. Create topic-based domains
3. Move files to appropriate domains
4. Update internal links
5. Create domain _index.md files
6. Update main context/_index.md

---

## Handling Unclear Mappings

If content doesn't clearly fit one domain:

**Primary domain rule**: Choose the most specific domain
- "Python error handling with logging" → `python/` (language is more specific)
- "Security logging for SIEM" → `security/` (security is more specific)

**Cross-reference**: Add Related Context sections
```markdown
## Related Context
- [[context/security/logging-requirements]]
- [[context/python/error-handling]]
```

**If truly spans multiple domains**: Consider if it's actually a cross-cutting pattern
- Might belong in `patterns/` domain
- Or create decision log explaining the trade-off

---

## Large Domain Files

If a domain file exceeds 400 lines:

**Apply progressive disclosure**:
```
python/
├── _index.md          # Overview + links to all files
├── conventions.md     # General conventions
├── error-handling.md  # Focused on errors
├── testing.md         # Focused on testing
└── type-hints.md      # Focused on types
```

Instead of one massive `python-standards.md`

---

## Related Skills

- `/context-update` - Maintain and evolve context
- `/audit` - Validate context quality
- `/standards-sync` - Sync with external authorities
