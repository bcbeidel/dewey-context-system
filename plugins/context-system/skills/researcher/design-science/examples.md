# Design Science Research Examples

**Purpose**: Real-world DSR project walkthroughs showing workflow in action.

**Created**: 2026-02-08

---

## Example 1: ML Pipeline Optimization

### Context

**Problem**: ML model retraining takes 8 hours, delaying production updates and blocking experimentation.

**Stakeholders**: Data science team (6 people), ML engineers, product managers

**Constraints**: Must work with existing infrastructure (Kubernetes, Python), 6-week timeline

---

### DSR Process

**Phase 1: Problem Identification** (4 days)
- Current state: 8-hour retraining pipeline
- Impact: $50k/month in delayed features, blocked experiments
- Literature review: Found papers on incremental learning, caching strategies
- Success criterion: Reduce to <1 hour

**Phase 2: Solution Objectives** (2 days)
- Functional: Cache intermediate computations, parallelize training
- Performance: <1 hour end-to-end, <10% accuracy degradation
- Constraints: Python 3.9+, Kubernetes, no new infrastructure costs

**Phase 3-5: Build-Evaluate Cycles**

**Cycle 1** (2 weeks):
- Built: Basic caching layer for feature engineering
- Evaluated: Reduced time to 5 hours (38% improvement)
- Issue: Feature engineering cached, but training still slow

**Cycle 2** (2 weeks):
- Built: Model checkpointing + incremental training
- Evaluated: Reduced time to 2 hours (75% improvement)
- Issue: Accuracy dropped 3% - acceptable but concerning

**Cycle 3** (1.5 weeks):
- Built: Hybrid approach - full train weekly, incremental daily
- Evaluated: 45 minutes average, 1% accuracy degradation
- Success: Met all criteria ✅

**Phase 6: Communication** (1 week)
- Technical doc: Architecture, API, deployment guide
- Business case: $40k/month savings + faster experimentation
- Presented to engineering, documented in internal wiki

---

### Key Learnings

**What worked**:
- Iterative cycles revealed hybrid was better than pure incremental
- Early evaluation prevented over-investment in wrong approach
- Multiple evaluation methods (benchmarking + case study with real models)

**What didn't**:
- Initial assumption that caching alone would suffice
- Underestimated accuracy trade-offs

**Advice**: Don't expect first design to work - budget for 2-3 cycles.

---

## Example 2: Data Governance Framework

### Context

**Problem**: Organization has data governance policies but no implementation guidance. Teams don't know how to operationalize governance.

**Stakeholders**: Data governance team, 12 data product teams, CTO

**Constraints**: Framework must be practical, not just theoretical. 8-week timeline.

---

### DSR Process

**Phase 1: Problem Identification** (5 days)
- Gap: Policies exist (25 pages) but zero implementation examples
- Impact: Inconsistent governance, compliance risks, frustrated teams
- Literature: DAMA-DMBOK, academic papers on governance frameworks
- Success: Teams can implement governance in <1 week per product

**Phase 2: Solution Objectives** (3 days)
- Functional: Step-by-step implementation playbooks, decision trees, templates
- Usability: Non-technical product owners can follow without governance experts
- Constraints: Align with existing 25-page policy, work for all 12 team contexts

**Phase 3-5: Build-Evaluate Cycles**

**Cycle 1** (2 weeks):
- Built: Initial framework with 5 playbooks (data classification, access control, lineage, quality, retention)
- Evaluated: Expert review (governance team) + scenario walkthroughs
- Issue: Too abstract, needed more concrete examples

**Cycle 2** (2.5 weeks):
- Built: Added 15 concrete examples, decision tree for classification, template spreadsheets
- Evaluated: Pilot with 2 teams - implemented governance in 3-4 days
- Issue: Teams needed more guidance on edge cases

**Cycle 3** (2 weeks):
- Built: FAQ section (20 common questions), "when to escalate" guidance
- Evaluated: Pilot with 3 more teams - average 2 days implementation
- Success: Met usability criteria ✅

**Phase 6: Communication** (1 week)
- Framework published as internal wiki
- Lunch-and-learn sessions with all 12 teams
- Templates shared in Confluence
- Monthly office hours for questions

---

### Key Learnings

**What worked**:
- Pilot evaluation with real teams revealed usability issues early
- Concrete examples > abstract principles
- Decision trees helped teams make judgment calls

**What didn't**:
- Initial version too focused on "what" (principles) vs. "how" (steps)
- Underestimated need for edge case guidance

**Advice**: If artifact targets non-experts, evaluate with non-experts (not just domain experts).

---

## Example 3: Data Quality Tool Comparison Method

### Context

**Problem**: Teams waste weeks manually comparing data quality tools (Great Expectations, Soda, dbt tests). Need systematic comparison method.

**Stakeholders**: 5 data engineering teams evaluating tools

**Constraints**: Method must complete evaluation in <1 day per tool. 4-week timeline.

---

### DSR Process

**Phase 1: Problem Identification** (3 days)
- Current: Ad-hoc evaluations, 2-3 weeks per tool, inconsistent criteria
- Impact: Delayed decisions, suboptimal tool choices
- Literature: Tool evaluation frameworks from software engineering
- Success: Complete 3-tool comparison in 1 day

**Phase 2: Solution Objectives** (2 days)
- Functional: Structured evaluation method with criteria, scoring, templates
- Efficiency: <8 hours per tool evaluation
- Constraints: Work for CLI tools, SaaS tools, open-source tools

**Phase 3-5: Build-Evaluate Cycles**

**Cycle 1** (1 week):
- Built: Evaluation criteria matrix (12 criteria), scoring rubric (1-5 scale)
- Evaluated: Applied to Great Expectations
- Issue: Took 12 hours - too slow

**Cycle 2** (1.5 weeks):
- Built: Streamlined to 6 core criteria, added quick-start templates, automated scoring
- Evaluated: Applied to Soda Core, took 5 hours
- Success: Met efficiency criteria ✅

**Cycle 3** (1 week):
- Built: Added comparison report template, decision matrix
- Evaluated: Team used method to compare 3 tools in 1 day (6 hours total)
- Success: Met all criteria ✅

**Phase 6: Communication** (0.5 weeks)
- Published method as internal guide
- Template spreadsheet shared in Drive
- Presented at data eng weekly

---

### Key Learnings

**What worked**:
- Applying method to real tools (not hypothetical) revealed practical issues
- Automation (auto-scoring) critical for efficiency
- Template-driven approach made method accessible

**What didn't**:
- Initial 12 criteria too comprehensive - diminishing returns
- Needed multiple rounds to find "minimum viable evaluation"

**Advice**: For efficiency-focused artifacts, measure actual time in evaluation - don't guess.

---

## Common Patterns

### Pattern 1: Hybrid Approaches Often Win

All three examples found hybrid solutions better than pure approaches:
- Example 1: Hybrid (full + incremental) beat pure incremental
- Example 2: Hybrid (principles + examples + templates) beat pure principles
- Example 3: Hybrid (manual + automated) beat pure manual

**Lesson**: First design rarely optimal - iteration reveals hybrid sweet spots.

---

### Pattern 2: Usability Testing is Critical

All three evaluated with real users in naturalistic settings:
- Example 1: Real models, real data science team
- Example 2: Real governance teams, real products
- Example 3: Real tool evaluation scenarios

**Lesson**: Lab evaluation insufficient - need real-world testing.

---

### Pattern 3: Start Formative, End Summative

All three progressed from formative to summative evaluation:
- Early cycles: Expert review, scenario walkthroughs (formative)
- Later cycles: Pilot studies, real use cases (summative)

**Lesson**: Don't jump to summative too early - iterate first.

---

## Anti-Patterns to Avoid

### Anti-Pattern 1: Building Without Evaluating

**Problem**: Build entire artifact, then discover it doesn't work.

**Better**: Build → Evaluate → Refine in short cycles.

---

### Anti-Pattern 2: Ignoring Context Validity

**Problem**: Artifact works in lab but fails in real contexts.

**Better**: Evaluate in naturalistic settings (case studies, pilots) before finalizing.

---

### Anti-Pattern 3: Treating First Cycle as Final

**Problem**: Expecting first design to be production-ready.

**Better**: Budget for 2-4 cycles, expect iteration.

---

## Template for Your Project

```markdown
# DSR Project: [Your Artifact Name]

## Context
- Problem: [What problem]
- Stakeholders: [Who cares]
- Constraints: [Time, tech, resources]

## Phase 1: Problem Identification
- Current state: [Baseline]
- Impact: [Why it matters]
- Literature: [What exists]
- Success criteria: [How to know you succeeded]

## Cycles (2-4 expected)

### Cycle 1
- Built: [What you built]
- Evaluated: [How you tested]
- Results: [What happened]
- Issues: [What to improve]

### Cycle 2
- Built: [Improvements]
- Evaluated: [How you tested]
- Results: [What happened]
- Decision: [Continue or done?]

## Outcomes
- Artifact: [Final artifact description]
- Value: [Business impact]
- Learnings: [What you learned]
```

---

## Additional Resources

**Related workflows**:
- [[workflow]] - Full DSR workflow guide
- [[../evidence-synthesis/workflow]] - For literature review in Phase 1
- [[../ux-research/workflow]] - For user validation

**Research standards**:
- [[../../context/research/design-science-research-standards]] - Academic foundations
