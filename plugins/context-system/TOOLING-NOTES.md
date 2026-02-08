# Tooling Considerations

## Markdown & Obsidian Bias

**Important**: This context management system is **optimized for markdown-based workflows**, particularly tools like Obsidian.

### What Works Well With This System

✅ **Markdown editors with wikilink support**:
- Obsidian
- Logseq
- Foam (VS Code)
- Dendron (VS Code)
- Notion (limited - supports markdown but not true wikilinks)

✅ **Plain text + file system**:
- Any text editor + file browser
- VS Code with markdown preview
- GitHub (renders markdown, but wikilinks show as plain text)

✅ **Git-based workflows**:
- Context can be checked into version control
- Shareable across team members
- History tracked in commits

### Design Decisions Tied to Markdown

The following design choices assume markdown compatibility:

1. **Wikilinks** (`[[file]]` syntax)
   - Used extensively for cross-references
   - Not standard markdown (Obsidian/Logseq extension)
   - Alternative: Standard markdown links `[text](path.md)`

2. **Frontmatter** (YAML at top of files)
   - Used for metadata (keywords, applies-to, tags)
   - Supported by static site generators and many markdown tools
   - Not rendered in basic markdown preview

3. **File-based organization**
   - Context as `.md` files in folders
   - Assumes file system navigation
   - Works well with grep, glob, file search

4. **Folder structure**
   - `context/communication/`, `context/project/`, etc.
   - Assumes hierarchical file system
   - Maps well to brain organization (semantic folders)

### Adapting to Other Tools

#### If You Use GitHub Wikis
- ✅ Supports markdown
- ⚠️ Wikilinks syntax slightly different (`[[File-Name]]` vs `[[file-name]]`)
- ⚠️ No frontmatter support (metadata goes in content)
- ✅ Can use folder structure with subpages
- **Adaptation**: Use GitHub wiki syntax for links, put metadata in headings

#### If You Use Notion
- ✅ Supports markdown syntax
- ❌ No true wikilinks (use `@mention` or links)
- ⚠️ Frontmatter goes into page properties
- ✅ Can replicate folder structure with nested pages
- **Adaptation**: Use `@mentions` for cross-references, page properties for metadata

#### If You Use Confluence
- ⚠️ Markdown support limited (some macros)
- ❌ No wikilinks (use page links)
- ❌ No frontmatter (use page properties or labels)
- ✅ Can replicate structure with page hierarchy
- **Adaptation**: Use native Confluence links, labels for metadata

#### If You Use Plain Text Files
- ✅ Works perfectly (markdown is plain text)
- ⚠️ Wikilinks won't be clickable (but grep/search still works)
- ⚠️ Frontmatter visible but not parsed
- ✅ Universal, no vendor lock-in
- **Adaptation**: Accept that links aren't clickable, rely on search

#### If You Use Google Docs / Word
- ❌ Not compatible (these are rich text, not plain text)
- ❌ No markdown support
- ❌ Can't use version control effectively
- **Not recommended**: Consider using a different tool for context management

### Why Markdown/Obsidian?

This bias exists because:

1. **Plain text**: Universal, future-proof, version controllable
2. **Markdown**: Widely supported, readable, portable
3. **Wikilinks**: Fast cross-referencing, bidirectional links
4. **File-based**: Works with git, CLI tools, search
5. **Local-first**: No vendor lock-in, fast, private

**The meta-problem is universal** (persistent context across conversations), but **the implementation is optimized for markdown workflows**.

### Adapting the Skill for Other Tools

If you want to use this context system with non-markdown tools:

**Core principles that transfer**:
- ✅ Semantic organization (communication/project/workflows/decisions)
- ✅ Task-based loading (map tasks to context)
- ✅ Evidence-based extraction (from real work)
- ✅ Template-first architecture (single source of truth)
- ✅ Maintenance through reflection (retrospectives)

**What you'll need to adapt**:
- ❌ Wikilink syntax → Your tool's linking mechanism
- ❌ Frontmatter → Your tool's metadata system
- ❌ File paths → Your tool's navigation system
- ❌ Grep/glob commands → Your tool's search functionality

**Effort to adapt**: Medium to High (depends on how far from markdown your tool is)

### Future: Tool-Agnostic Version?

A future version of this skill could support multiple tool backends, automatically adapting to different platforms (Notion, Confluence, GitHub wikis) while maintaining the same core principles.

**Current status**: This skill supports **markdown-based workflows only** (Obsidian, Logseq, Foam, plain text).

Tool-specific adaptations could be created as separate skills or variants in the future.

---

## Recommendations by Use Case

### Individual Developer, Local Workflow
**Best fit**: Obsidian or plain text
- Private, fast, no internet required
- Full wikilink support
- Version control friendly

### Team, Shared Documentation
**Good fit**: GitHub Wiki or Confluence
- Built into existing tools
- Access control
- Team familiar with tool
- **Tradeoff**: Less markdown-friendly, requires adaptation

### Multi-Tool Team
**Good fit**: Plain markdown in git repo
- Universal (works with any editor)
- Version controlled
- CI/CD integrable
- **Tradeoff**: No clickable wikilinks unless using compatible editor

### Non-Technical Team
**Not recommended**: Use tool-native documentation instead
- This system assumes comfort with files, folders, markdown
- Non-technical users likely prefer visual tools (Notion, Confluence, Google Docs)
- Consider different approach for non-technical stakeholders

---

*Last updated: 2026-02-07*
