---
name: compare
description: "Create weighted decision matrices and systematic comparisons for evaluating multiple options against defined criteria"
allowed-tools: Read, Write, Edit, AskUserQuestion
---

# Compare - Systematic Option Comparison

**Purpose**: Generate structured comparisons and weighted decision matrices to evaluate multiple alternatives against defined criteria, reducing bias and improving decision quality.

**When to use**: Choosing between 2+ viable options (vendors, frameworks, strategies, candidates) where multiple criteria matter and the decision has significant consequences.

**Outputs**: Weighted scoring matrix (markdown table), criteria rationale, recommendation with tradeoff analysis, sensitivity insights.

---

## Quick Start

**What are you comparing?**

1. **Technology/Tools** (frameworks, vendors, SaaS) → Use [[#Weighted Decision Matrix]]
2. **Strategic Options** (business directions, product features) → Use [[#Block Method Comparison]]
3. **Research Methods/Findings** (academic) → Use [[.claude/skills/systematic-review/methodology-comparison|Literature Review Skill]]
4. **Ideas/Concepts** (learning, understanding) → Use [[mental-models/comparative-analysis|Comparative Analysis Mental Model]]

**Not sure?** Default to [[#Weighted Decision Matrix]] for practical decisions.

---

## Overview

This skill implements comparative analysis using two proven methods:

### Method 1: Weighted Decision Matrix (Quantitative)
**Best for**: Practical decisions with measurable/scorable criteria (vendor selection, tool evaluation, hiring)

**Process**:
1. Define evaluation criteria
2. Assign importance weights (must sum to 100%)
3. Score each option (1-10 scale)
4. Calculate weighted scores
5. Analyze results and sensitivity

### Method 2: Block Method (Qualitative)
**Best for**: Strategic decisions with complex, hard-to-quantify factors (business strategy, organizational design)

**Process**:
1. Define evaluation dimensions
2. Fully analyze Option 1 across all dimensions
3. Fully analyze Option 2 across all dimensions
4. Synthesize insights and tradeoffs
5. Make recommendation with rationale

---

## Workflow: Weighted Decision Matrix

### Step 1: Gather Requirements

Ask the user:

**Required inputs**:
- What options are you comparing? (2-6 options; more than 6 suggests need for filtering first)
- What are you optimizing for? (goal/outcome)
- What factors matter for this decision? (initial list)

**Context questions**:
- Who else is involved in this decision?
- What's the timeline/urgency?
- Are there any must-have requirements (binary yes/no)?
- What's the cost of being wrong?

### Step 2: Define Evaluation Criteria

**Characteristics of good criteria**:
- **Specific**: "Cost" is vague; "Total 3-year TCO" is specific
- **Measurable**: Can be scored objectively or with clear rubric
- **Independent**: Criteria shouldn't overlap (see MECE principle)
- **Relevant**: Directly impacts the goal
- **Actionable**: Helps discriminate between options

**Common criteria by domain**:

**Technology/Tools**:
- Performance/Speed
- Cost (initial + ongoing)
- Learning curve / Developer experience
- Ecosystem size / Community support
- Vendor stability / Long-term viability
- Security / Compliance
- Scalability
- Integration capabilities

**Vendors/Partners**:
- Price / Value
- Quality / Track record
- Responsiveness / Support
- Cultural fit
- Financial stability
- Geographic coverage
- Flexibility / Customization

**People/Hiring**:
- Technical skills match
- Experience level
- Cultural fit
- Growth potential
- Availability / Start date
- Communication skills
- Domain expertise

**Typical criteria count**: 4-8 criteria (fewer than 4 suggests simple decision; more than 8 suggests need to group related criteria)

### Step 3: Assign Weights

Weights represent **relative importance** and must sum to 100%.

**Weighting approaches**:

1. **Direct allocation**: Assign percentages directly
   - "Cost is 40%, Performance 30%, Ease of Use 20%, Support 10%"

2. **Pairwise comparison**: Compare criteria head-to-head
   - "If I had to choose, is Cost or Performance more important?"
   - Build weights from pairwise rankings

3. **Must-have vs Nice-to-have**: Heavily weight must-haves (30-50%), distribute rest

**Weight distribution patterns**:
- **Dominant criterion** (one 40-50%, rest 10-20%): Clear priority
- **Balanced** (all 15-30%): Multiple factors equally important
- **Tiered** (2-3 at 25-35%, rest at 5-15%): Few critical, some supporting

**Validate weights**: Do they reflect true priorities? Test: "Would I accept 20% worse on Criterion A to gain 20% better on Criterion B?"

### Step 4: Score Each Option

**Scoring scale**: 1-10 (where 1 = poor, 5-6 = acceptable, 10 = excellent)

**Scoring tips**:
- **Use relative scoring**: Best option gets 9-10, worst gets 2-4 (avoid 1 and 10 unless truly extreme)
- **Be consistent**: Score all options on Criterion A before moving to Criterion B
- **Document evidence**: Note why each score was assigned
- **Involve stakeholders**: Collaborative scoring reduces individual bias

**Example scoring rubric (Performance criterion)**:
- 9-10: Exceeds all performance requirements, industry-leading
- 7-8: Meets all requirements with headroom
- 5-6: Meets requirements, minimal headroom
- 3-4: Meets some requirements, gaps exist
- 1-2: Does not meet requirements

### Step 5: Generate Decision Matrix

Create markdown table:

```markdown
## Decision Matrix: [Decision Name]

**Goal**: [What you're optimizing for]

**Date**: [YYYY-MM-DD]

| Criterion | Weight | Option A | Option B | Option C |
|-----------|--------|----------|----------|----------|
| Performance | 30% | 8 (2.4) | 6 (1.8) | 9 (2.7) |
| Cost | 25% | 7 (1.75) | 9 (2.25) | 5 (1.25) |
| Ease of Use | 20% | 9 (1.8) | 7 (1.4) | 6 (1.2) |
| Ecosystem | 15% | 8 (1.2) | 9 (1.35) | 6 (0.9) |
| Support | 10% | 6 (0.6) | 8 (0.8) | 7 (0.7) |
| **TOTAL** | **100%** | **7.75** | **7.6** | **6.75** |

**Ranking**: Option A (7.75) > Option B (7.6) > Option C (6.75)

### Score Explanations

**Performance**:
- Option A (8): Handles 10k req/sec in benchmarks
- Option B (6): Handles 5k req/sec, adequate for current needs
- Option C (9): Handles 15k req/sec, fastest in category

**Cost**:
- Option A (7): $50k/year, moderate pricing
- Option B (9): $30k/year, most affordable
- Option C (5): $80k/year, premium pricing

[Continue for all criteria...]
```

### Step 6: Analyze Results

**Interpret the scores**:

1. **Check margin of victory**:
   - **Large gap** (>1.0 points): Clear winner
   - **Small gap** (<0.5 points): Too close to call, need sensitivity analysis
   - **Tie**: Dig deeper or use tiebreakers

2. **Identify dominant criteria**:
   - Which criteria contributed most to the winner's score?
   - Would changing those criteria change the outcome?

3. **Look for tradeoffs**:
   - Where does the winner lose? (e.g., "Option A wins overall but is weakest on Cost")
   - Are those weaknesses acceptable?

4. **Perform sensitivity analysis**:
   - What if we increased Cost weight from 25% to 35%? (Would Option B win?)
   - What if Option A's Performance score was 7 instead of 8? (Does ranking change?)

### Step 7: Generate Recommendation

**Structure**:

```markdown
## Recommendation: [Chosen Option]

**Winner**: Option A (Weighted Score: 7.75)

### Why This Option?

Option A wins because:
1. **Strongest on critical criteria**: Scores highest on Performance (8) and Ease of Use (9), our top two priorities
2. **Balanced profile**: No major weaknesses (lowest score is 6 on Support, still acceptable)
3. **Best long-term fit**: Superior ecosystem positions us for future growth

### Tradeoffs Accepted

By choosing Option A, we accept:
- **Higher cost** (7/10 vs Option B's 9/10): Adds $20k/year vs cheapest option
- **Weaker support** (6/10 vs Option B's 8/10): Community-driven vs vendor support

**Risk mitigation**: Budget allocated for Option A's cost. Team training planned to reduce support dependency.

### Alternatives Considered

**Option B** (Score: 7.6) - Very close second
- **Strengths**: Most affordable, strong support
- **Why not chosen**: Performance (6/10) may bottleneck as we scale
- **When to reconsider**: If budget becomes constrained or performance requirements decrease

**Option C** (Score: 6.75) - Not recommended
- **Strengths**: Best raw performance
- **Why not chosen**: Premium cost (+60% vs Option B) not justified by needs; weak ease of use creates adoption risk

### Sensitivity Analysis

This recommendation is **robust** to:
- ±10% weight changes on any single criterion
- ±1 point score changes on non-critical criteria

This recommendation is **sensitive** to:
- If Performance weight drops below 20% (Option B would win)
- If Cost weight exceeds 35% (Option B would win)

**Confidence**: High (scores align with qualitative assessment; margin sufficient; tradeoffs acceptable)
```

---

## Workflow: Block Method Comparison

**When to use**: Strategic decisions where quantification feels forced or factors are deeply interconnected.

### Step 1: Define Evaluation Dimensions

Instead of scorable criteria, define **analytical dimensions**:
- Financial impact (revenue, cost, risk)
- Strategic fit (alignment with goals, competitive positioning)
- Operational feasibility (resources, timeline, capabilities)
- Risk profile (what could go wrong, mitigation options)

### Step 2: Analyze Each Option Fully

For each option, write a comprehensive analysis:

```markdown
## Option 1: [Name]

### Financial Impact
[Revenue potential, cost structure, payback period, ROI]

### Strategic Fit
[How this advances company strategy, competitive implications, market positioning]

### Operational Feasibility
[Resource requirements, timeline, capabilities needed, dependencies]

### Risk Profile
[Key risks, probability and impact, mitigation strategies, exit options]

### Summary
[3-5 sentence synthesis: What makes this option compelling? What are the gotchas?]

---

[Repeat for Option 2, Option 3, etc.]
```

### Step 3: Cross-Option Synthesis

After analyzing all options individually:

```markdown
## Comparative Insights

### Revenue Potential
- **Highest**: Option B ($50M in 3 years)
- **Lowest**: Option A ($30M in 3 years)
- **Most certain**: Option A (90% confidence vs Option B's 60%)

### Risk-Adjusted Returns
- Option A: $27M expected value (0.9 × $30M), low variance
- Option B: $30M expected value (0.6 × $50M), high variance
- Option C: $20M expected value (0.5 × $40M), highest uncertainty

### Resource Requirements
- **Least intensive**: Option A (existing team can execute)
- **Most intensive**: Option C (requires new capabilities)

### Time to Impact
- **Fastest**: Option A (6-12 months)
- **Slowest**: Option C (24-36 months)

### Strategic Alignment
[Which option best advances long-term strategy?]
```

### Step 4: Make Recommendation

Synthesize across dimensions to identify the best option given context and priorities.

---

## Examples

### Example 1: Cloud Provider Selection

See [[#Step 5 Generate Decision Matrix]] above for complete worked example.

### Example 2: Product Strategy (Block Method)

See [[mental-models/comparative-analysis#Example 3]] for strategic options comparison.

---

## Best Practices

### DO:
- ✅ **Define criteria before** evaluating options (prevents cherry-picking)
- ✅ **Involve stakeholders** in weighting and scoring (builds buy-in)
- ✅ **Document assumptions** (makes analysis auditable)
- ✅ **Test sensitivity** (understand which factors drive the decision)
- ✅ **Revisit when context changes** (weights shift over time)

### DON'T:
- ❌ **Force quantification** when qualitative matters (use Block Method instead)
- ❌ **Over-engineer with 15+ criteria** (diminishing returns; combine related factors)
- ❌ **Ignore close scores** (<0.5 gap = need deeper analysis or tiebreaker)
- ❌ **Weight retroactively** (don't adjust weights to get desired winner)
- ❌ **Use when only 1 option exists** (analysis paralysis; just evaluate that option)

---

## Related Documentation

**Mental Models**:
- [[mental-models/comparative-analysis]] - Thinking framework for comparison
- [[mental-models/mece-mutually-exclusive-collectively-exhaustive]] - Ensure criteria don't overlap
- [[mental-models/issue-trees]] - Break down complex decisions

**Skills**:
- SKILL - Academic research comparison
- SKILL - Synthesize findings across sources

**Context**:
- [[data/accuracy-standards]] - Source verification for comparison data

---

## Version History

**v1.0 (2026-02-07)**: Initial skill creation
- Weighted decision matrix workflow
- Block method comparison
- Sensitivity analysis guidance
- Best practices and examples
