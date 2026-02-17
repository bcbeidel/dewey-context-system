# Knowledge Record Operations

## The Record as a Data Structure

A knowledge record is a markdown file with predictable structure. We can
decompose it into parts, manipulate the parts, and reassemble it. Every
operation is deterministic — Claude handles judgment, Python handles files.

```python
@dataclass
class Section:
    heading: str        # "Guidance", "Context", etc. (without ##)
    content: str        # everything between this ## and the next

@dataclass
class KnowledgeRecord:
    frontmatter: dict            # YAML fields
    title: str                   # H1 text (without #)
    sections: list[Section]      # ordered sections
    link_defs: list[str]         # reference-style [ref]: url lines at bottom
```

---

## Atomic Operations

### Parse

```python
def parse_record(path: Path) -> KnowledgeRecord:
    """Decompose a markdown file into its parts."""

def parse_record_text(text: str) -> KnowledgeRecord:
    """Same, from a string."""

def render_record(record: KnowledgeRecord) -> str:
    """Reassemble a KnowledgeRecord into markdown text."""

def write_record(path: Path, record: KnowledgeRecord) -> None:
    """Render and write to disk."""
```

Round-trip invariant: `render_record(parse_record_text(text))` preserves
the semantic content. Whitespace normalization is acceptable (consistent
blank lines between sections).

### Frontmatter

```python
def get_field(record: KnowledgeRecord, key: str) -> Any:
    """Get a frontmatter field value. Returns None if missing."""

def set_field(record: KnowledgeRecord, key: str, value: Any) -> KnowledgeRecord:
    """Set or update a frontmatter field. Returns a new record."""

def remove_field(record: KnowledgeRecord, key: str) -> KnowledgeRecord:
    """Remove a frontmatter field. Returns a new record."""
```

### Sections

```python
def get_section(record: KnowledgeRecord, heading: str) -> Optional[Section]:
    """Find a section by heading (case-insensitive substring match)."""

def add_section(
    record: KnowledgeRecord,
    heading: str,
    content: str,
    after: Optional[str] = None,
) -> KnowledgeRecord:
    """Insert a new section. If after is None, append at end (before link defs).
    If after is a heading name, insert after that section."""

def remove_section(
    record: KnowledgeRecord,
    heading: str,
) -> tuple[KnowledgeRecord, Optional[Section]]:
    """Remove a section. Returns (new_record, removed_section)."""

def replace_section(
    record: KnowledgeRecord,
    heading: str,
    content: str,
) -> KnowledgeRecord:
    """Replace a section's content. Heading stays the same."""

def rename_section(
    record: KnowledgeRecord,
    old_heading: str,
    new_heading: str,
) -> KnowledgeRecord:
    """Rename a section heading."""

def reorder_sections(
    record: KnowledgeRecord,
    order: list[str],
) -> KnowledgeRecord:
    """Reorder sections to match the given heading list.
    Sections not in the list are appended at the end."""
```

### Links

```python
def get_link_defs(record: KnowledgeRecord) -> dict[str, str]:
    """Return {ref_name: url} for all reference-style link definitions."""

def set_link_def(
    record: KnowledgeRecord,
    ref_name: str,
    url: str,
) -> KnowledgeRecord:
    """Add or update a reference-style link definition."""

def inline_to_reference_links(record: KnowledgeRecord) -> KnowledgeRecord:
    """Convert inline [text](url) links to reference-style [text][ref]
    with definitions at the bottom. Deduplicates URLs."""
```

### Provenance

```python
def extract_source_evaluation(record: KnowledgeRecord) -> Optional[dict]:
    """Parse a Source Evaluation markdown table into structured data.
    Returns None if no Source Evaluation section exists."""

def write_provenance(path: Path, data: dict) -> None:
    """Write provenance JSON to .dewey/provenance/<slug>.json.
    Creates parent directories if needed."""

def read_provenance(path: Path) -> Optional[dict]:
    """Read provenance JSON. Returns None if file doesn't exist."""
```

### Scaffolding

```python
def create_record(
    title: str,
    depth: str,
    frontmatter: dict,
    sections: Optional[list[Section]] = None,
) -> KnowledgeRecord:
    """Create a new record with required structure.
    If sections is None, generates stub sections for the depth."""

def stub_sections(depth: str) -> list[Section]:
    """Return the canonical section stubs for a depth.
    working: Guidance, Context, In Practice, Pitfalls, Go Deeper
    overview: What This Covers, Topics, Key Sources"""
```

---

## Division of Labor

| Concern | Who | Why |
|---------|-----|-----|
| Parse, render, write files | **Python** | Deterministic, testable |
| Reorder, rename, add/remove sections | **Python** | Structural manipulation |
| Frontmatter field CRUD | **Python** | Data manipulation |
| Link conversion and deduplication | **Python** | Deterministic transformation |
| Source evaluation extraction | **Python** | Table parsing |
| Validate structure and quality | **Python** | Health checks (existing) |
| Decide what summary to write | **Claude** | Judgment |
| Decide what guidance to include | **Claude** | Judgment |
| Evaluate source quality | **Claude** | Judgment |
| Research and synthesize content | **Claude** | Judgment |
| Choose which sections need updating | **Claude** | Judgment |
| Write prose content | **Claude** | Judgment |

---

## Workflows

### 1. Create Record

A new knowledge record from external sources.

```
┌─────────────────────────────────────────────────────────┐
│ Claude: Research & Author                               │
│                                                         │
│  1. Research topic using provided sources                │
│  2. Evaluate source quality (authority, accuracy, etc.)  │
│  3. Search for counter-evidence                          │
│  4. Write content for each section                       │
│  5. Write summary (1-3 sentences, standalone)            │
│  6. Call Python to assemble the file                     │
│                                                         │
│ Python: Assemble & Write                                │
│                                                         │
│  record = create_record(                                │
│      title="Optimal Strategy",                          │
│      depth="working",                                   │
│      frontmatter={                                      │
│          "summary": summary_text,                       │
│          "sources": source_list,                        │
│          "last_validated": today(),                      │
│          "relevance": relevance_text,                   │
│          "tags": tag_list,                              │
│      },                                                 │
│      sections=[                                         │
│          Section("Guidance", guidance_text),             │
│          Section("Context", context_text),               │
│          Section("In Practice", practice_text),          │
│          Section("Pitfalls", pitfalls_text),             │
│          Section("Go Deeper", links_text),               │
│      ],                                                 │
│  )                                                      │
│  write_record(path, record)                             │
│  write_provenance(prov_path, evaluation_data)           │
│                                                         │
│ Python: Validate                                        │
│                                                         │
│  issues = check_all(path)                               │
│  # Returns any structural/quality issues                │
│                                                         │
│ Claude: Fix                                             │
│                                                         │
│  If issues found, revise content and re-assemble        │
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py create \
  --title "Optimal Strategy" \
  --depth working \
  --output references/tic-tac-toe/optimal-strategy.md \
  --frontmatter '{"summary": "...", "sources": [...], ...}' \
  --sections-json sections.json
```

### 2. Update Section

Modify one section of an existing record.

```
┌─────────────────────────────────────────────────────────┐
│ Python: Parse                                           │
│                                                         │
│  record = parse_record(path)                            │
│  old_section = get_section(record, "Guidance")          │
│  # Return old content to Claude for context             │
│                                                         │
│ Claude: Revise                                          │
│                                                         │
│  Write new section content based on old + new info      │
│                                                         │
│ Python: Replace & Write                                 │
│                                                         │
│  record = replace_section(record, "Guidance", new_text) │
│  record = set_field(record, "last_validated", today())  │
│  write_record(path, record)                             │
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py get-section \
  --file references/tic-tac-toe/optimal-strategy.md \
  --section "Guidance"

python3 record.py replace-section \
  --file references/tic-tac-toe/optimal-strategy.md \
  --section "Guidance" \
  --content-file new-guidance.md

python3 record.py set-field \
  --file references/tic-tac-toe/optimal-strategy.md \
  --key last_validated \
  --value 2026-02-16
```

### 3. Add Quick Reference

Add a Quick Reference section to a topic that doesn't have one.

```
┌─────────────────────────────────────────────────────────┐
│ Python: Parse                                           │
│                                                         │
│  record = parse_record(path)                            │
│  # Return full record to Claude for context             │
│                                                         │
│ Claude: Author                                          │
│                                                         │
│  Write terse lookup content (tables, lists)             │
│                                                         │
│ Python: Insert & Write                                  │
│                                                         │
│  record = add_section(                                  │
│      record, "Quick Reference", qr_text,                │
│      after="Pitfalls"                                   │
│  )                                                      │
│  write_record(path, record)                             │
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py add-section \
  --file references/tic-tac-toe/optimal-strategy.md \
  --heading "Quick Reference" \
  --after "Pitfalls" \
  --content-file qr-content.md
```

### 4. Migrate (v1 → v2)

Transform an existing v1 file to v2 format.

```
┌─────────────────────────────────────────────────────────┐
│ Python: Parse & Transform (fully deterministic)         │
│                                                         │
│  record = parse_record(path)                            │
│                                                         │
│  # Rename sections                                      │
│  record = rename_section(record,                        │
│      "Key Guidance", "Guidance")                        │
│  record = rename_section(record,                        │
│      "Why This Matters", "Context")                     │
│  record = rename_section(record,                        │
│      "Watch Out For", "Pitfalls")                       │
│                                                         │
│  # Reorder sections                                     │
│  record = reorder_sections(record, [                    │
│      "Guidance", "Context", "In Practice",              │
│      "Pitfalls", "Go Deeper",                           │
│  ])                                                     │
│                                                         │
│  # Extract provenance                                   │
│  prov = extract_source_evaluation(record)               │
│  if prov:                                               │
│      write_provenance(prov_path, prov)                  │
│      record, _ = remove_section(record,                 │
│          "Source Evaluation")                            │
│                                                         │
│  # Convert links                                        │
│  record = inline_to_reference_links(record)             │
│                                                         │
│  write_record(path, record)                             │
│                                                         │
│ Claude: Add summary (requires judgment)                 │
│                                                         │
│  Read the migrated file, write a summary field          │
│  record = parse_record(path)                            │
│  record = set_field(record, "summary", summary_text)    │
│  write_record(path, record)                             │
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py migrate --file references/tic-tac-toe/optimal-strategy.md

# Deterministic steps complete. Summary requires Claude:
python3 record.py get-field \
  --file references/tic-tac-toe/optimal-strategy.md \
  --key summary
# Returns: null (not yet set)

python3 record.py set-field \
  --file references/tic-tac-toe/optimal-strategy.md \
  --key summary \
  --value "Tic-tac-toe is a solved game where..."
```

### 5. Refresh Sources

Re-validate a record against its sources.

```
┌─────────────────────────────────────────────────────────┐
│ Python: Parse                                           │
│                                                         │
│  record = parse_record(path)                            │
│  sources = get_field(record, "sources")                 │
│  last_validated = get_field(record, "last_validated")   │
│  prov = read_provenance(prov_path)                      │
│  # Return to Claude                                     │
│                                                         │
│ Claude: Review                                          │
│                                                         │
│  Check each source URL for changes                      │
│  Assess whether content is still accurate               │
│  Decide: still valid / needs update / stale             │
│                                                         │
│ Python: Update metadata                                 │
│                                                         │
│  record = set_field(record, "last_validated", today())  │
│  write_record(path, record)                             │
│                                                         │
│ (If content needs updating, hand off to Update workflow)│
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py get-field \
  --file references/tic-tac-toe/optimal-strategy.md \
  --key sources

python3 record.py set-field \
  --file references/tic-tac-toe/optimal-strategy.md \
  --key last_validated \
  --value 2026-02-16
```

### 6. Merge .ref.md Into Parent

Consolidate a companion reference file into its parent topic.

```
┌─────────────────────────────────────────────────────────┐
│ Python: Parse both files                                │
│                                                         │
│  parent = parse_record(parent_path)                     │
│  ref = parse_record(ref_path)                           │
│                                                         │
│  # Take all sections from ref file as Quick Reference   │
│  qr_lines = []                                          │
│  for section in ref.sections:                           │
│      if "see also" not in section.heading.lower():      │
│          qr_lines.append(f"## {section.heading}")       │
│          qr_lines.append(section.content)               │
│                                                         │
│  # Flatten into single Quick Reference section          │
│  # (demote ## to ### within quick reference)            │
│  parent = add_section(parent,                           │
│      "Quick Reference", qr_content,                     │
│      after="Pitfalls")                                  │
│                                                         │
│  # Remove Go Deeper ref link if it exists               │
│  # (the reference is now inline)                        │
│                                                         │
│  write_record(parent_path, parent)                      │
│  # Delete ref file                                      │
│  ref_path.unlink()                                      │
└─────────────────────────────────────────────────────────┘
```

**CLI entry point:**
```bash
python3 record.py merge-ref \
  --file references/tic-tac-toe/optimal-strategy.md
  # Finds and merges optimal-strategy.ref.md automatically
```

---

## Module Structure

```
dewey/skills/curate/scripts/
  record.py          # The atomic operations module + CLI
  templates.py       # Scaffolding (calls record.py for create_record)
  config.py          # Configuration (read_knowledge_dir, etc.)
  create_topic.py    # Workflow orchestration (calls record.py)
  propose.py         # Proposal workflow
  promote.py         # Promotion workflow
  scaffold.py        # Knowledge base scaffolding

dewey/skills/health/scripts/
  validators.py      # Imports parse_record from record.py
  cross_validators.py
  auto_fix.py        # Imports section operations from record.py
  ...
```

`record.py` becomes the foundation. Validators import from it instead of
reimplementing parsing. Auto-fix composes its operations instead of
hand-rolling line manipulation. Templates call `create_record()` instead
of string concatenation.

---

## What This Replaces

| Current | New |
|---------|-----|
| `_body_without_frontmatter()` in validators.py | `parse_record()` |
| `_extract_section()` in validators.py | `get_section()` |
| `parse_frontmatter()` in validators.py | `parse_record().frontmatter` |
| `_frontmatter()` in templates.py | `render_record()` handles frontmatter |
| `render_topic_md()` string concatenation | `create_record()` + `render_record()` |
| `fix_missing_sections()` line insertion | `add_section()` |
| `fix_missing_cross_links()` line scanning | `add_section()` / `replace_section()` |

The existing functions in validators.py become thin wrappers or are replaced
by imports from record.py. The parse-once, validate-many pattern becomes
natural — parse the record once, pass it to multiple validators.
