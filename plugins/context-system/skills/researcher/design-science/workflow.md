# Design Science Research Workflow

**Purpose**: Build and evaluate technology artifacts through systematic, iterative cycles.

**Version**: 1.0
**Created**: 2026-02-08
**Status**: Production

---

## Overview

Design Science Research (DSR) creates innovative artifacts (software, systems, methods, models) to solve important problems, then rigorously evaluates their utility.

**Core cycle**: Build → Evaluate → Refine → Repeat

**When to use**: Building data platforms, ML systems, prototypes, frameworks, or evaluating technical solutions.

---

## Quick Start

**Choose your entry point**:

- **New to DSR?** → Start with "What is Design Science Research?" below
- **Ready to start?** → Jump to Phase 1: Problem Identification
- **Need examples?** → See [[examples]]
- **Want evaluation guidance?** → See Phase 4: Evaluation

---

## What is Design Science Research?

### Core Principles (Hevner et al. 2004)

**Seven guidelines**:
1. **Design as Artifact**: Create something tangible (system, method, model)
2. **Problem Relevance**: Solve important, previously unsolved business problem
3. **Design Evaluation**: Rigorously evaluate utility, quality, efficacy
4. **Research Contributions**: Contribute to knowledge base
5. **Research Rigor**: Apply rigorous methods in construction and evaluation
6. **Design as Search**: Iteratively search for effective solutions
7. **Communication**: Present to both technical and business audiences

**Source**: [[../../context/research/design-science-research-standards]]

---

### Four Artifact Types

1. **Constructs**: Vocabulary, symbols (taxonomies, conceptual models)
2. **Models**: Abstractions (design theories, frameworks)
3. **Methods**: Algorithms, practices (procedures, protocols)
4. **Instantiations**: Implemented systems (prototypes, products)

**Most common**: Software systems, algorithms, frameworks

---

## Six-Phase Workflow

### Timeline

**Typical DSR project**: 4-12 weeks (2-4 build-evaluate cycles)

**Phase breakdown**:
- Phase 1: Problem Identification (3-5 days)
- Phase 2: Solution Objectives (2-3 days)
- Phase 3: Design & Development (2-4 weeks per cycle)
- Phase 4: Demonstration (3-5 days per cycle)
- Phase 5: Evaluation (1 week per cycle)
- Phase 6: Communication (1 week)

---

## Phase 1: Problem Identification & Motivation

**Goal**: Define the problem and justify why a solution is valuable.

**Duration**: 3-5 days

---

### Activities

**1. Define the problem** (1-2 days)
- What problem are you solving?
- Why does it matter? (business impact, research gap)
- Who is affected?
- What are current limitations?

**Example questions**:
- "Current ML pipelines take 8 hours to retrain - need faster approach"
- "Data governance frameworks lack implementation guidance"
- "No standard methodology for evaluating data quality tools"

---

**2. Justify the solution value** (1 day)
- What are the consequences of not solving it?
- What benefits would solution provide?
- Why hasn't it been solved already?

**Output**: Problem statement document (1-2 pages)

**Template**:
```markdown
# Problem Statement

## Problem Definition
[Clear description of problem]

## Importance
- Business impact: [$ cost, time wasted, risks]
- Research gap: [What's missing in existing solutions]
- Affected stakeholders: [Who experiences this problem]

## Current Limitations
1. [Existing approach 1 and its limitation]
2. [Existing approach 2 and its limitation]

## Success Criteria
What would "solved" look like?
- [Measurable criterion 1]
- [Measurable criterion 2]
```

---

**3. Literature review** (2-3 days)
- What existing solutions exist?
- What are their strengths and weaknesses?
- What can you learn from them?

**Quick method**: Use [[../../evidence-synthesis/workflow]] (REA mode: 3-7 days) for rapid literature synthesis.

**Output**: Summary of existing solutions (1-2 pages)

---

### Phase 1 Outputs

- ✅ Problem statement document
- ✅ Justification of solution value
- ✅ Summary of existing solutions
- ✅ Success criteria defined

---

## Phase 2: Define Solution Objectives

**Goal**: Translate problem into specific, measurable objectives for the artifact.

**Duration**: 2-3 days

---

### Activities

**1. Infer objectives from problem** (1 day)
- What must the artifact do to solve the problem?
- What are the functional requirements?
- What are the non-functional requirements (performance, usability)?

**Example objectives**:
- "Reduce ML pipeline retraining time from 8 hours to <1 hour"
- "Provide step-by-step implementation guidance for data governance"
- "Enable comparison of 5+ data quality tools in <2 hours"

---

**2. Define constraints** (1 day)
- Technical constraints (platforms, languages, tools)
- Resource constraints (time, budget, people)
- Organizational constraints (policies, existing systems)

---

**3. Identify evaluation criteria** (1 day)
- How will you know if artifact succeeds?
- What will you measure?
- What are acceptable thresholds?

**Criteria types**:
- **Functional**: Does it work as intended?
- **Performance**: How fast, efficient, scalable?
- **Usability**: Can users actually use it?
- **Value**: Does it solve the problem?

**Template**:
```markdown
# Solution Objectives

## Functional Objectives
1. [What artifact must do - objective 1]
2. [What artifact must do - objective 2]

## Non-Functional Objectives
- Performance: [e.g., <1 second response time]
- Usability: [e.g., 5-minute learning curve]
- Scalability: [e.g., handle 10k records]

## Constraints
- Technical: [e.g., must work with Python 3.9+]
- Resource: [e.g., 4-week timeline]
- Organizational: [e.g., must integrate with existing auth]

## Evaluation Criteria
| Criterion | Measurement | Threshold |
|-----------|-------------|-----------|
| Speed | Processing time | <1 hour |
| Accuracy | Error rate | <5% |
| Usability | Task success | >80% |
```

---

### Phase 2 Outputs

- ✅ Solution objectives document
- ✅ Constraints documented
- ✅ Evaluation criteria defined
- ✅ Measurable thresholds set

---

## Phase 3: Design & Development

**Goal**: Create the artifact.

**Duration**: 2-4 weeks (per build-evaluate cycle)

---

### Build-Evaluate Cycles

**Typical project**: 2-4 cycles
- **Cycle 1**: Basic prototype (proof of concept)
- **Cycle 2**: Functional prototype (core features)
- **Cycle 3**: Refined prototype (based on evaluation)
- **Cycle 4**: Production-ready (if needed)

**Key**: Each cycle includes development AND evaluation.

---

### Activities

**1. Design the artifact** (3-5 days)
- Architecture/structure
- Key components
- Interfaces and interactions
- Technical approach

**Documentation**:
- Architecture diagrams
- Component specifications
- Data models (if applicable)
- API design (if applicable)

**Tools**: Use `/diagram` for visualizing architecture.

---

**2. Build the artifact** (1-3 weeks)
- Implement according to design
- Follow engineering best practices
- Document code and decisions
- Track design rationale

**Best practices**:
- Iterative development (don't build everything at once)
- Version control (git)
- Document why decisions were made
- Keep prototype focused (don't over-engineer)

---

**3. Document build process** (ongoing)
- What did you build?
- How did you build it?
- What decisions did you make and why?
- What challenges did you encounter?

**Why documentation matters**: Others need to understand and reproduce your work.

**Template**:
```markdown
# Build Log - Cycle [N]

## What We Built
[Description of artifact at this stage]

## Key Decisions
1. **Decision**: [What you decided]
   - **Rationale**: [Why]
   - **Alternatives considered**: [What you rejected and why]

## Technical Approach
[Architecture, components, implementation details]

## Challenges & Solutions
- **Challenge**: [Problem encountered]
  - **Solution**: [How you solved it]

## Current State
- What's working: [Features completed]
- What's not working: [Known issues]
- Next steps: [What to build next]
```

---

### Phase 3 Outputs

- ✅ Working artifact (prototype)
- ✅ Architecture documentation
- ✅ Build log with rationale
- ✅ Source code (if software)

---

## Phase 4: Demonstration

**Goal**: Show that the artifact can solve the problem.

**Duration**: 3-5 days (per cycle)

---

### Demonstration Methods

**1. Experimentation**: Run experiments showing artifact performance
- Example: "Retraining time reduced from 8 hours to 45 minutes"

**2. Simulation**: Simulate artifact in controlled environment
- Example: "Framework applied to 3 synthetic data governance scenarios"

**3. Case Study**: Apply artifact in real organizational context
- Example: "Implemented data quality tool comparison with real team"

**4. Proof**: Mathematical or logical proof of properties
- Example: "Algorithm proven to converge in O(n log n) time"

**5. Scenario**: Walk through usage scenarios
- Example: "Demonstrated 5 common data governance use cases"

---

### Activities

**1. Prepare demonstration** (1-2 days)
- Select demonstration method (often multiple)
- Prepare test data/scenarios
- Set up environment
- Define success metrics

---

**2. Execute demonstration** (1-2 days)
- Run the demonstration
- Collect data/evidence
- Document results
- Capture screenshots/recordings

---

**3. Analyze results** (1 day)
- Did artifact solve the problem?
- What worked well?
- What didn't work?
- What surprised you?

**Template**:
```markdown
# Demonstration Results - Cycle [N]

## Method
[How you demonstrated: experiment, case study, etc.]

## Setup
[Environment, data, scenarios used]

## Results
[What happened - be specific with numbers/evidence]

## Success Metrics
| Metric | Target | Achieved | Status |
|--------|--------|----------|--------|
| Speed | <1 hour | 45 min | ✅ |
| Accuracy | >95% | 92% | ⚠️ |

## Observations
- What worked: [Positive findings]
- What didn't work: [Issues discovered]
- Surprises: [Unexpected results]

## Next Steps
[What to change/improve in next cycle]
```

---

### Phase 4 Outputs

- ✅ Demonstration results
- ✅ Evidence artifact solves problem
- ✅ Metrics collected
- ✅ Issues identified for next cycle

---

## Phase 5: Evaluation

**Goal**: Rigorously assess artifact's utility, quality, and efficacy.

**Duration**: 1 week (per cycle)

---

### FEDS Framework

**Two dimensions** for planning evaluation:

1. **Functional purpose**:
   - **Formative**: Improve artifact (early cycles)
   - **Summative**: Assess final achievement (late cycles)

2. **Evaluation paradigm**:
   - **Artificial**: Controlled, lab-based
   - **Naturalistic**: Real-world, organizational context

**Best practice**: Start artificial/formative → Progress to naturalistic/summative.

**Source**: [[../../context/research/design-science-research-standards#feds-framework]]

---

### Evaluation Methods (Mix Multiple)

**Non-empirical**:
- **Argument**: Logical argument artifact will work
- **Scenarios**: Walk through use cases
- **Expert review**: Get expert opinion

**Empirical Positivist**:
- **Experiments**: Controlled tests with metrics
- **Simulations**: Model-based evaluation
- **Benchmarking**: Compare to alternatives

**Empirical Interpretive**:
- **Case studies**: Real-world application
- **Action research**: Collaborative evaluation in org
- **User studies**: Observe users with artifact

**Critical**:
- **Contextual analysis**: Examine social/organizational impact

---

### Activities

**1. Select evaluation methods** (1 day)
- Choose 2-3 methods for robust evaluation
- Consider cycle stage (early = formative, late = summative)
- Balance effort vs. rigor

**Early cycles**: Expert review + scenario walkthrough + simple experiment
**Late cycles**: User study + case study + benchmarking

---

**2. Execute evaluation** (3-4 days)
- Conduct each evaluation method
- Collect systematic data
- Document observations
- Track both successes and failures

---

**3. Analyze evaluation results** (2-3 days)
- Synthesize findings across methods
- Compare against objectives (Phase 2)
- Identify strengths and weaknesses
- Assess validity threats

**Validity types** (check all three):
- **Criterion**: Does it meet specified criteria?
- **Causal**: Does it cause intended outcomes?
- **Context**: When/where does it work?

**Source**: [[../../context/research/design-science-research-standards#validity-framework]]

---

**4. Decide next steps** (1 day)
- **If successful**: Move to Phase 6 (Communication) OR run additional naturalistic evaluation
- **If issues found**: Plan next build-evaluate cycle with improvements
- **If fundamental problems**: Revisit Phase 2 (Objectives) or Phase 3 (Design)

**Template**:
```markdown
# Evaluation Report - Cycle [N]

## Methods Used
1. [Method 1]: [Brief description]
2. [Method 2]: [Brief description]

## Findings

### Criterion Validity (Does it meet criteria?)
| Criterion | Target | Result | Met? |
|-----------|--------|--------|------|
| Speed | <1 hour | 45 min | ✅ |
| Accuracy | >95% | 92% | ⚠️ |

### Causal Validity (Does it work?)
- **Intended outcome**: [e.g., Faster retraining]
- **Evidence**: [Experimental results, user feedback]
- **Confidence**: [High/Medium/Low]

### Context Validity (Where does it work?)
- **Tested contexts**: [Where evaluated]
- **Works well in**: [Contexts where successful]
- **Limitations**: [Where it doesn't work]

## Strengths
1. [Strength 1 with evidence]
2. [Strength 2 with evidence]

## Weaknesses
1. [Weakness 1 with evidence]
2. [Weakness 2 with evidence]

## Rival Explanations Considered
- **Alternative explanation 1**: [Why results might not be due to artifact]
  - **Ruled out because**: [Evidence]

## Decision
- [ ] Ready for Phase 6 (Communication)
- [ ] Need another build-evaluate cycle
- [ ] Need to revisit design (Phase 3)
- [ ] Need to revisit objectives (Phase 2)

## Recommendations for Next Cycle
[If continuing, what to improve]
```

---

### Phase 5 Outputs

- ✅ Evaluation report with multiple methods
- ✅ Validity assessment (criterion, causal, context)
- ✅ Strengths and weaknesses identified
- ✅ Decision on next steps

---

## Phase 6: Communication

**Goal**: Share the problem, artifact, rigor, and effectiveness with appropriate audiences.

**Duration**: 1 week

---

### Two Audiences

**1. Technical audience** (implementation details)
- Researchers, developers, engineers
- **Focus**: How to build, how it works, technical contributions
- **Deliverable**: Technical report, code repository, API documentation

**2. Business audience** (business value)
- Executives, managers, stakeholders
- **Focus**: Problem solved, value delivered, when to use
- **Deliverable**: Executive summary, ROI analysis, implementation guide

---

### Activities

**1. Document artifact** (2-3 days)

**Technical documentation**:
- Architecture and design
- Implementation details
- Code repository (if software)
- Installation/setup instructions
- API documentation (if applicable)

**Business documentation**:
- Problem statement and justification
- Solution overview (non-technical)
- Benefits and value delivered
- Use cases and examples
- When to use / when not to use

---

**2. Document research process** (2-3 days)

**What to include**:
- Problem identification rationale
- Design decisions and rationale
- Build process and challenges
- Evaluation methods and results
- Validity assessment
- Limitations and future work

**Why**: Others need to understand and trust your work.

---

**3. Create deliverables** (2-3 days)

**For technical audience**:
- Technical report (10-20 pages)
- Code repository (GitHub, GitLab)
- Demo video or walkthrough
- API documentation
- Installation guide

**For business audience**:
- Executive summary (2-3 pages)
- Business case / ROI analysis
- Implementation guide (how to adopt)
- Use case examples
- Presentation slides

---

**4. Present findings** (varies)
- Present to stakeholders
- Publish research (if academic)
- Share with community (blog, conference)
- Document learnings internally

**Template**:
```markdown
# DSR Project Report: [Artifact Name]

## Executive Summary (1 page)
- Problem and its importance
- Solution overview
- Key benefits
- Results achieved

## Problem (2-3 pages)
- Detailed problem statement
- Why it matters
- Existing solutions and their limitations

## Solution (3-5 pages)
- Artifact description
- How it works (non-technical)
- Key features
- Example usage

## Research Process (3-5 pages)
- Build-evaluate cycles
- Design decisions
- Evaluation methods
- Results and findings

## Technical Details (5-10 pages)
- Architecture
- Implementation
- Performance characteristics
- Integration guidance

## Evaluation Results (3-5 pages)
- Methods used
- Findings (strengths, weaknesses)
- Validity assessment
- Comparison to alternatives (if applicable)

## Limitations & Future Work (1-2 pages)
- Known limitations
- Boundary conditions (where it works / doesn't work)
- Future enhancements
- Research opportunities

## Appendices
- Code repository link
- Demo videos
- Detailed specifications
```

---

### Phase 6 Outputs

- ✅ Technical documentation
- ✅ Business documentation
- ✅ Code repository (if applicable)
- ✅ Presentations / reports
- ✅ Learnings documented

---

## Troubleshooting

### "My artifact doesn't work in evaluation"

**Common causes**:
- Objectives too ambitious for timeline
- Insufficient understanding of problem
- Technical challenges underestimated

**Solutions**:
1. **Reduce scope**: Focus on core problem
2. **Iterate**: Expect 2-4 cycles, not 1
3. **Seek expertise**: Get help with technical challenges
4. **Revisit objectives**: May need to adjust expectations

**Remember**: DSR is iterative - failures inform improvements.

---

### "Evaluation shows mixed results"

**This is normal!** Artifacts often work in some contexts but not others.

**Solutions**:
1. **Clarify context validity**: Document where it works well
2. **Improve weaknesses**: Next cycle focuses on weak areas
3. **Accept trade-offs**: Perfect is impossible, good enough is fine
4. **Be transparent**: Report both strengths and limitations

---

### "I'm not sure if this is 'research' or just 'development'"

**Key differences**:

**Development**: Build solution for known problem with known approach
**Design Science Research**: Build solution for novel problem OR novel approach, with rigorous evaluation and knowledge contribution

**Research characteristics**:
- Contributes new knowledge (not just new implementation)
- Rigorously evaluates artifact
- Considers rival explanations
- Documents design rationale
- Communicates to broader community

**If your work checks these boxes**, it's DSR.

---

## Known Limitations

**When DSR may not be appropriate**:
- Pure exploratory research (no artifact to build)
- Routine application of existing solutions
- Purely theoretical research
- When evaluation in context not feasible

**DSR requires**:
- Ability to build artifact (technical skills, resources)
- Access to evaluation context (users, data, organizations)
- 4-12 weeks timeline
- Tolerance for iteration and failure

---

## Integration with Other Methods

**Common combinations**:
- **DSR + Evidence Synthesis**: Literature review → Build informed artifact
- **DSR + UX Research**: User research → User-centered artifact
- **DSR + Case Study**: Evaluate artifact in organizational case context

---

## Related Documentation

**Core reference**:
- [[../../context/research/design-science-research-standards]] - Research standards and sources

**Examples**:
- [[examples]] - Real DSR projects walkthrough

**Other methodologies**:
- [[../evidence-synthesis/workflow]] - For literature review component
- [[../ux-research/workflow]] - For user validation component
- [[../case-study/workflow]] - For naturalistic evaluation

---

## Sources

Based on:
- Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design science in IS research
- FEDS Framework (Venable, Pries-Heje, Baskerville, 2014)
- Design Science validity framework (2025)
- [[../../context/research/design-science-research-standards]]

---

**First Use**: Define problem you want to solve with technology artifact, then work through Phase 1
