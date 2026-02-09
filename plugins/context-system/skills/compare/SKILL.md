---
name: compare
description: "Create weighted decision matrices and systematic comparisons for evaluating multiple options against defined criteria"
allowed-tools: Read, Write, Edit, AskUserQuestion
---

# Compare - Systematic Option Comparison

**Purpose**: Generate structured comparisons and weighted decision matrices to evaluate multiple alternatives against defined criteria, reducing bias and improving decision quality.

**When to use**: Choosing between 2+ viable options where multiple criteria matter and the decision has significant consequences.

**Outputs**: Weighted scoring matrix, criteria rationale, recommendation with tradeoff analysis, sensitivity insights.

---

## Quick Start

**What are you comparing?**

1. **Technology/Tools** (frameworks, vendors, SaaS)
   - See [[weighted-matrix.md]] for step-by-step workflow

2. **Strategic Options** (business directions, product features)
   - See [[block-method.md]] for qualitative analysis

3. **Need examples?**
   - See [[examples.md]] for complete worked examples

4. **Best practices guidance**
   - See [[best-practices.md]] for DO/DON'T checklist

---

## Overview

This skill implements comparative analysis using two proven methods:

### Method 1: Weighted Decision Matrix (Quantitative)
**Best for**: Practical decisions with measurable criteria (vendor selection, tool evaluation, hiring)

**Process**: Define criteria → Assign weights → Score options → Calculate → Analyze sensitivity

**See**: [[weighted-matrix.md]] for complete workflow

### Method 2: Block Method (Qualitative)
**Best for**: Strategic decisions with complex, hard-to-quantify factors (business strategy, organizational design)

**Process**: Define dimensions → Analyze each option fully → Synthesize insights → Recommend

**See**: [[block-method.md]] for complete workflow

---

## When to Use Each Method

| Situation | Method | Why |
|-----------|--------|-----|
| Vendor selection | Weighted Matrix | Scorable criteria (cost, features, support) |
| Framework choice | Weighted Matrix | Measurable performance, ecosystem, learning curve |
| Business strategy | Block Method | Complex interdependencies, qualitative factors |
| Organizational design | Block Method | Cultural, political, long-term considerations |
| Hiring (structured) | Weighted Matrix | Scorable skills, experience, cultural fit |
| Product direction | Block Method | Market positioning, strategic fit, risk profile |

**Default**: Weighted Matrix for most practical decisions

---

## Integration

**Works with**:
- `/systematic-review` - Compare research methodologies
- `/audit` - Compare design approaches (we used this for skills audit!)
- Mental models - [[mental-models/comparative-analysis]]

---

## Troubleshooting

### Symptom: Weights don't sum to 100%

**Cause**: Math error or percentages entered incorrectly

**Fix**: Recalculate. Common approach: Start with round numbers (25%, 25%, 20%, 15%, 15%) then adjust

### Symptom: All options score similarly (within 0.5 points)

**Cause**: Criteria too broad, or options genuinely similar

**Fix**:
- Add more discriminating criteria
- Consider if decision actually matters (if options equivalent, pick any)
- Use qualitative tiebreakers

### Symptom: Winner changes dramatically with small weight adjustments

**Cause**: Decision is highly sensitive, no clear winner

**Fix**:
- Document sensitivity in recommendation
- Consider hybrid approach or phased decision
- May need more information to decide confidently

### Symptom: Quantification feels forced

**Cause**: Factors are qualitative or interconnected

**Fix**: Use Block Method instead (see [[block-method.md]])

---

## Known Limitations

**Cannot handle**:
- Decisions with <2 options (not a comparison)
- Single-criterion decisions (just optimize that criterion)
- Decisions where criteria can't be defined (pure intuition/gut feel)

**Struggles with**:
- Options >6 (suggests need for filtering first)
- Criteria >10 (too complex, need grouping)
- Highly interconnected criteria (violates independence assumption)

**Workarounds**:
- **Too many options**: Use elimination criteria first
- **Too many criteria**: Group into categories, score categories
- **Interconnected**: Use Block Method or decision trees

**Process limitations**:
- Requires upfront effort (1-2 hours for matrix)
- Assumes criteria can be weighted independently
- Scoring still subjective (but systematic)

---

## Related Documentation

**Reference Files (This Skill)**:
- [[weighted-matrix.md]] - 7-step weighted decision matrix workflow
- [[block-method.md]] - 4-step qualitative block method
- [[examples.md]] - Complete worked examples
- [[best-practices.md]] - DO/DON'T guidelines

**Mental Models**:
- [[mental-models/comparative-analysis]] - Thinking framework
- [[mental-models/mece-mutually-exclusive-collectively-exhaustive]] - Ensure criteria independence

**Skills**:
- `/systematic-review` - Academic research comparison
- `/audit` - Audit design approaches

---

## Quick Reference

**Weighted Matrix (1-2 hours)**:
1. Gather requirements (10 min)
2. Define criteria (20 min)
3. Assign weights (15 min)
4. Score options (30 min)
5. Generate matrix (10 min)
6. Analyze results (20 min)
7. Write recommendation (15 min)

**Block Method (2-4 hours)**:
1. Define dimensions (20 min)
2. Analyze options (1-2 hours)
3. Synthesize (30 min)
4. Recommend (30 min)

**Choose based on**: Measurability of criteria and decision complexity
