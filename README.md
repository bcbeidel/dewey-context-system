# Context System - Dewey Plugin Development

This repository contains **Dewey**, a context optimization plugin for Claude Code.

## What is Dewey?

Dewey is a Claude Code plugin that helps you intelligently manage, analyze, and optimize your context files using LLM-based analysis. It uses your existing Claude Code session - no additional API keys or costs required.

**Key Features:**
- ✅ **Zero dependencies** - Uses only Python built-in libraries
- ✅ **No installation required** - Works immediately after plugin install
- ✅ **No API costs** - Uses your existing Claude Code session
- ✅ **Portable** - Works anywhere Python 3.9+ exists

## Quick Start

### Install the Plugin

```bash
# Add the dewey marketplace
/plugin marketplace add bcbeidel/dewey

# Install the dewey plugin
/plugin install dewey
```

That's it! No additional setup needed.

### Use Commands

Once installed, you can use dewey commands in your Claude Code sessions:

```bash
# Analyze your context directory (defaults to ./context/)
/dewey:analyze

# Analyze a specific directory
/dewey:analyze path/to/directory

# Split a large file using LLM semantic analysis
/dewey:split large-file.md
```

### Development Setup

For local development:

```bash
# Clone the repository
git clone https://github.com/bcbeidel/dewey.git
cd dewey

# Create symlink to plugins directory
ln -s "$(pwd)/dewey" ~/.claude/plugins/dewey

# Restart Claude Code
```

## Documentation

- **[Plugin README](dewey/README.md)** - Complete plugin documentation
- **[Implementation Plan](IMPLEMENTATION_PLAN.md)** - Development roadmap

## Plugin Structure

```
dewey/
├── .claude-plugin/plugin.json    # Plugin manifest
├── skills/                        # Claude Code skills
│   ├── analyze/                   # Context analysis skill
│   │   ├── SKILL.md               # Skill definition
│   │   └── scripts/               # Python helpers
│   └── split/                     # File splitting skill
│       ├── SKILL.md               # Skill definition
│       └── scripts/               # Python helpers
├── scripts/                       # Standalone CLI tools
├── tests/                         # Test suite
└── README.md                      # Plugin documentation
```

## Features

**Version**: 0.0.5

### `/dewey:analyze` - Context Analysis
- Analyzes your context directory (defaults to `./context/`)
- Identifies token usage, large files, and optimization opportunities
- Provides prioritized recommendations with token impact estimates
- Suggests specific actions like splitting files or removing duplicates

### `/dewey:split` - Intelligent File Splitting
- Uses LLM semantic analysis (not mechanical splitting)
- Maintains semantic coherence across split boundaries
- Creates scannable main file + topical reference files
- Follows Anthropic's context organization best practices
- Backs up original files automatically

## Status

- ✅ Zero dependencies - Uses only Python built-in libraries
- ✅ Skills-based structure following Claude Code best practices
- ✅ LLM-driven semantic analysis for intelligent optimization
- ✅ Context-aware defaults (analyzes `./context/` by default)
- 📋 Additional optimization features planned

See [IMPLEMENTATION_PLAN.md](IMPLEMENTATION_PLAN.md) for details.

## Project Files

- `dewey/` - Plugin implementation
- `IMPLEMENTATION_PLAN.md` - Development roadmap v2.0
- `README.md` - This file

---

**For full plugin documentation, see [dewey/README.md](dewey/README.md)**
