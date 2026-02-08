# Context System Marketplace

A Claude Code marketplace containing skills for persistent context management.

## Quick Installation

Add this marketplace to Claude Code:

```
/plugin marketplace add bcbeidel/skill-context-system
```

Then install the `context-system` plugin from the Discover tab.

## What's Included

### Context System Plugin

Make Claude persistently remember your preferences, decisions, and workflows across conversations.

**Skills:**
- `/init-context-system` - Initial setup wizard for creating your context management system
- `/context-update` - Ongoing maintenance for extracting and organizing context from conversations

**[View Plugin Documentation →](./plugins/context-system/README.md)**

## Repository Structure

This repository is organized as a Claude Code marketplace:

```
/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace configuration
└── plugins/
    └── context-system/           # Context management plugin
        ├── .claude-plugin/
        │   └── plugin.json       # Plugin metadata
        ├── commands/             # Skill definitions
        │   ├── init-context-system.md
        │   └── context-update.md
        ├── templates/            # Context templates
        ├── examples/             # Example context files
        └── README.md             # Full documentation
```

## Contributing

See [CONTRIBUTING.md](./plugins/context-system/CONTRIBUTING.md) for guidelines.

## License

MIT License - see [LICENSE](./LICENSE)
