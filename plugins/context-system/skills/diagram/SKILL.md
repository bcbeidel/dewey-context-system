---
name: diagram
description: "Generate Mermaid diagrams, concept maps, and flowcharts from mental models, processes, and relationships for visual learning"
allowed-tools: Read, Write, Edit, AskUserQuestion
---

# Diagram Generator

Creates visual diagrams from mental models, processes, workflows, and relationships using Mermaid syntax that renders natively in Obsidian.

**Problem Solved**: Mental models and syntheses benefit from visual representations but require manual diagram creation.

**Use Case**: Visualize concepts, processes, relationships, and hierarchies to enhance comprehension and retention.

---

## Core Principles

1. **Visual Learning Complements Text** - Diagrams provide a different cognitive pathway for understanding concepts
2. **Mermaid for Obsidian Compatibility** - Native rendering in Obsidian markdown preview, no external tools required
3. **Simplicity Over Complexity** - Clear, simple diagrams are more valuable than complex, cluttered ones
4. **Multiple Diagram Types** - Different concepts need different visual formats (flowcharts, concept maps, hierarchies, sequences, mindmaps)

---

## Quick Start

Choose your diagram type:
- **Process or workflow?** → [Flowchart](diagram-types.md#type-1-flowchart-process-flow)
- **Concept relationships?** → [Concept Map](diagram-types.md#type-2-concept-map-relationships)
- **Temporal sequence?** → [Sequence Diagram](diagram-types.md#type-4-sequence-diagrams-temporal-flow)
- **Hierarchical structure?** → [Class Diagram](diagram-types.md#type-3-class-diagrams-structure) or [Mindmap](diagram-types.md#type-5-mindmaps-radial-structure)
- **Timeline/schedule?** → [Gantt Chart](diagram-types.md#type-6-gantt-charts-timeline)

**See**: [diagram-types.md](diagram-types.md) for all types with complete syntax examples

---

## Workflow Overview

Create diagrams in 4 phases:

1. **Content Analysis** - Identify source material and extract key elements (concepts, relationships, flow)
2. **Diagram Design** - Choose appropriate diagram type based on content structure
3. **Mermaid Generation** - Generate clean, properly formatted Mermaid syntax
4. **Integration** - Embed in source note or create separate diagram file with bidirectional links

**See**: [workflow.md](workflow.md) for complete step-by-step guide

**Key Decision Points**:
- Flowchart: Process with sequential steps and decision points
- Concept Map: Network of relationships between ideas
- Mind Map: Central concept with hierarchical branches
- Class Diagram: Classification or inheritance structure
- Sequence Diagram: Temporal interactions between actors

---

## Supported Diagram Types

### Quick Reference

| Type | Use For | Syntax |
|------|---------|--------|
| Flowchart | Processes, workflows, decisions | `flowchart TD` |
| Concept Map | Idea relationships, networks | `graph LR` |
| Class Diagram | Structures, hierarchies | `classDiagram` |
| Sequence | Temporal flow, interactions | `sequenceDiagram` |
| Mindmap | Radial concepts, brainstorming | `mindmap` |
| Gantt | Timelines, schedules | `gantt` |

**See**: [diagram-types.md](diagram-types.md) for detailed syntax and examples

---

## Examples & Patterns

**Common Use Cases**:
- Visualize mental model processes (flowchart)
- Show relationships between mental models (concept map)
- Map research synthesis structure (mindmap)
- Illustrate workflow sequences (sequence diagram)

**Common Patterns**:
- Decision trees
- Comparison matrices
- Feedback loops
- Hierarchical classifications

**See**: [examples.md](examples.md) for:
- Real-world usage examples
- Common diagram patterns
- Integration with mental-model and research-synthesis skills

---

## Advanced Usage

**Features Available**:
- Styling and color themes
- Subgraphs for grouping
- Clickable links (Obsidian-specific)
- Custom node shapes
- Edge styling

**See**: [syntax-reference.md](syntax-reference.md) for:
- Quality guidelines
- Advanced Mermaid features
- Customization options
- Troubleshooting tips
- Performance considerations

---

## Best Practices

**Create Diagrams For**:
- Processes with 3+ steps
- Concepts with 4+ relationships
- Hierarchies or taxonomies
- Complex workflows

**Diagram Quality**:
- Keep to 7-12 nodes (unless complexity required)
- Use clear, concise labels
- Label relationships in concept maps
- Choose appropriate diagram type for content structure

**See**: [syntax-reference.md](syntax-reference.md#best-practices) for complete guidelines

---

## Troubleshooting

**Symptom**: Diagram doesn't render in Obsidian preview
- **Cause**: Mermaid syntax error (missing semicolons, wrong keywords, unclosed quotes)
- **Fix**: Check syntax against [diagram-types.md](diagram-types.md) examples, validate at [Mermaid Live Editor](https://mermaid.live)

**Symptom**: Diagram renders but looks cluttered or unreadable
- **Cause**: Too many nodes (>15), unclear labels, or inappropriate diagram type
- **Fix**: Simplify to 7-12 key nodes, use subgraphs for grouping, or switch diagram type (e.g., mindmap → flowchart)

**Symptom**: Relationships difficult to follow
- **Cause**: Missing edge labels, wrong diagram type (flowchart used for network relationships)
- **Fix**: Add labels to edges in concept maps, consider using `graph LR` instead of `flowchart TD` for non-linear relationships

**Symptom**: Diagram doesn't match content structure
- **Cause**: Wrong diagram type selected (e.g., flowchart for hierarchical content)
- **Fix**: Review [Quick Start](#quick-start) decision tree, match diagram type to content structure

---

## Known Limitations

**Cannot handle**:
- **Interactive diagrams** - Mermaid generates static SVG images (no zoom, pan, collapse)
- **Non-Mermaid syntaxes** - Limited to Mermaid (no PlantUML, D2, Graphviz support)
- **Very complex diagrams** - Mermaid rendering may fail or become unreadable with >25-30 nodes
- **Real-time data** - Diagrams are static snapshots, not live visualizations

**Workarounds**:
- **For interactivity**: Export to external tools (draw.io, Excalidraw) if needed
- **For complex systems**: Create multiple focused diagrams instead of one comprehensive diagram
- **For alternative syntaxes**: Manually create diagrams in preferred tool, embed images in notes

---

## Related Documentation

- [diagram-types.md](diagram-types.md) - All diagram types with syntax examples
- [workflow.md](workflow.md) - Complete 4-phase workflow guide
- [examples.md](examples.md) - Usage examples and common patterns
- [syntax-reference.md](syntax-reference.md) - Advanced features and troubleshooting
- [resources.md](resources.md) - Related skills and external resources

---

## Quick Commands

```bash
# Visualize a mental model
/diagram "mental-models/First Principles Thinking.md" --type=flowchart

# Show relationships between concepts
/diagram --relationships "First Principles, Systems Thinking"

# Create hierarchical mindmap
/diagram "path/to/note.md" --type=mindmap

# Visualize workflow
/diagram "context/workflows/processes/research-synthesis-pipeline.md"
```

---

**First Use**: Visualize a mental model you're currently studying to enhance comprehension

**Success Criteria**: Diagram clarifies concept better than text alone
