
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
