# Contributing to Context System Skill

Thank you for considering contributing! This project aims to help Claude Code users create persistent context systems.

---

## Ways to Contribute

### 1. Report Issues
- Found a bug? [Open an issue](https://github.com/bcbeidel/skill-context-system/issues)
- Unclear documentation? Let us know
- Feature request? Describe your use case

### 2. Share Examples
- Created context for a specific domain? Share it!
- Found patterns worth documenting? Submit an example
- Adapted skill for different tools? Share your adaptation

### 3. Improve Documentation
- Fix typos or unclear sections
- Add more examples
- Improve installation instructions
- Translate documentation

### 4. Add Features
- Validation checks
- Additional templates
- Tool-specific adaptations (Notion, Confluence)
- Automation scripts

### 5. Test and Provide Feedback
- Try the skill in your projects
- Report what works well
- Suggest improvements

---

## Development Guidelines

### File Structure
```
skill-context-system/
├── README.md              # Repo overview
├── SKILL-README.md        # Detailed skill explanation
├── SKILL.md              # Implementation guide
├── TOOLING-NOTES.md      # Tool compatibility notes
├── plugin.json           # Plugin manifest (for claude plugin install)
├── templates/            # Reusable templates
├── examples/             # Real-world examples
└── CONTRIBUTING.md       # This file
```

**Important files**:
- `plugin.json` - Plugin manifest, must be updated when version changes
- `SKILL.md` - Main skill implementation (what Claude executes)
- `README.md` - User-facing documentation

### Documentation Standards

- **Clear**: Use simple language, avoid jargon
- **Examples**: Show, don't just tell
- **Specific**: "Use lowercase tags" not "use consistent formatting"
- **Rationale**: Explain the "why" not just the "what"

### Code/Content Standards

- Use markdown for all documentation
- Follow existing template structure
- Include frontmatter on context files (title, created, keywords, applies-to, tags, type)
- Add examples (good and bad patterns)
- Cross-reference related files

---

## Pull Request Process

1. **Fork the repository**
2. **Create a branch**: `git checkout -b feature/your-feature-name`
3. **Make your changes**:
   - Follow existing patterns
   - Add examples if adding features
   - Update documentation
4. **Test your changes**: Verify formatting, links, examples work
5. **Commit with clear messages**:
   ```
   feat(templates): add workflow template for code review

   Added code-review-workflow.md template with:
   - Step-by-step review process
   - Quality checkpoints
   - Common pitfalls
   ```
6. **Push to your fork**: `git push origin feature/your-feature-name`
7. **Open Pull Request**: Describe what you changed and why

### PR Checklist

- [ ] Follows existing structure and conventions
- [ ] Documentation updated (if applicable)
- [ ] Examples added (if adding features)
- [ ] All links work (wikilinks resolve)
- [ ] Frontmatter present on new context files
- [ ] Clear commit messages

---

## Adaptation Guidelines

Want to adapt this skill for other tools (Notion, Confluence, etc.)?

### Creating Tool Adaptations

1. **Preserve core principles** (10 tenets):
   - Semantic organization
   - Task-based loading
   - Evidence-based extraction
   - Template-first
   - etc.

2. **Adapt implementation details**:
   - Linking mechanism (wikilinks → tool-specific)
   - Metadata format (frontmatter → tool-specific)
   - Navigation (file paths → tool-specific)

3. **Document changes**:
   - What's different from markdown version?
   - What tradeoffs exist?
   - What features are gained/lost?

4. **Provide examples**:
   - Show actual screenshots or exports
   - Demonstrate the pattern in that tool

5. **Submit as separate file**:
   - `NOTION-ADAPTATION.md`
   - `CONFLUENCE-ADAPTATION.md`
   - Keep core skill intact

---

## Style Guide

### Markdown

- Use `##` for main sections, `###` for subsections
- Use bullet lists for items without specific order
- Use numbered lists for sequential steps
- Use code blocks with language identifiers: ` ```bash `
- Use **bold** for emphasis, `code` for commands/files

### Tone

- Concise but complete
- Friendly but professional
- Active voice ("Create the file" not "The file should be created")
- Direct ("Do this" not "You might want to consider doing this")

### Examples

Always include both good and bad examples:

**Good:**
```
[Show the right way]
```

**Avoid:**
```
[Show the wrong way + explain why]
```

---

## Questions?

- Open an issue for questions
- Start a discussion for broader topics
- Tag @bcbeidel if urgent

---

## Code of Conduct

Be respectful, constructive, and inclusive. We're all here to learn and improve.

---

Thank you for contributing! 🎉
