# Systematic Review: Integration Patterns

**Purpose**: How systematic-review integrates with other skills and customization options.

---

## Integration with Other Skills

### With `/research-synthesis`
- **Systematic Review**: Academic papers, formal structure, citations, PRISMA compliance
- **Research Synthesis**: General sources (podcasts, books, articles), pattern-based, flexible

**When to use which:**
- Use `/systematic-review` for academic rigor, publication-ready output
- Use `/research-synthesis` for broader synthesis across diverse sources

### With `/mental-model`
Extract mental models from academic research:
```bash
/systematic-review "Decision Making Under Uncertainty"
# Reviews academic literature, identifies theoretical frameworks

/mental-model "Prospect Theory"
# Create mental model based on research findings
```

### With `/learn`
Learn concepts from research findings:
```bash
/systematic-review "Spaced Repetition"
# Creates comprehensive academic review

/learn start [key concept from review]
# Learn the research-backed principles
```

### With `/diagram`
Visualize research findings:
```bash
/systematic-review "Cognitive Load Theory"
# Complete literature review

/diagram
# Create concept map of theoretical relationships
```

---

## Customization Options

### Review Depth

| Depth | Papers | Output | Time | Best For |
|-------|--------|--------|------|----------|
| Comprehensive | 20+ | 15-20 pages | 8-12h | Dissertation, thesis |
| Focused | 10-15 | 8-12 pages | 4-6h | Research papers |
| Moderate | 5-8 | 4-6 pages | 2-4h | Background sections |
| Quick | 3-5 | 2-3 pages | 1-2h | Preliminary research |

**Usage:**
```bash
--depth=comprehensive  # Full systematic review (20+ papers)
--depth=focused        # Standard review (10-15 papers)
--depth=moderate       # Moderate review (5-8 papers)
--depth=quick          # Rapid assessment (3-5 papers)
```

### Citation Style
```bash
--citation=apa         # APA 7th edition (default)
--citation=chicago     # Chicago style
--citation=mla         # MLA style
```

### Output Format
```bash
--format=full          # Complete review document (default)
--format=summary       # Executive summary only
--format=table         # Comparison table focus
--format=annotated     # Annotated bibliography style
```

---

## Related Documentation

- [[workflow]] - Main skill documentation
- [[examples]] - Usage examples and scenarios
- [[strengths-limitations]] - What works well and challenges
