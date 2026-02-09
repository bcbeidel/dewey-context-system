# Design Science Research Standards

**Purpose**: Best practices and frameworks for Design Science Research (DSR) methodology

**Created**: 2026-02-08
**Status**: Research synthesis for `/researcher` skill implementation

---

## Overview

Design Science Research (DSR) is a research paradigm focusing on the development and validation of prescriptive knowledge through artifact creation and evaluation.

**Core principle**: "Build and evaluate" - create innovative artifacts to solve important problems, then rigorously evaluate their utility.

---

## Foundational Framework (Hevner et al. 2004)

### Seven Guidelines for DSR

1. **Design as an Artifact**: Research must produce an artifact created to address a problem
2. **Problem Relevance**: Artifact should solve "heretofore unsolved and important business problem"
3. **Design Evaluation**: Artifact's "utility, quality, and efficacy" must be rigorously evaluated
4. **Research Contributions**: Provide clear contribution to knowledge base
5. **Research Rigor**: Apply rigorous methods in construction and evaluation
6. **Design as a Search Process**: Utilize available means to reach desired ends, iteratively
7. **Communication**: Present results to both technology-oriented and management-oriented audiences

**Sources**:
- [Hevner et al. Design Science Methodology](https://www.sciencedirect.com/science/article/pii/S1877050924011128)
- [Design Science Research Guidelines](https://link.springer.com/chapter/10.1007/978-3-030-35629-3_11)

---

## DSR Process Steps

### Six-Step Process

1. **Problem identification and motivation**: Define research problem and justify solution value
2. **Definition of objectives for solution**: Infer objectives from problem definition
3. **Design and development**: Create artifact (construct, model, method, instantiation)
4. **Demonstration**: Show artifact solves problem (via experimentation, simulation, case study, proof)
5. **Evaluation**: Observe and measure how well artifact supports solution
6. **Communication**: Communicate problem importance, artifact novelty, rigor, effectiveness

**Sources**:
- [Design Science Process](https://en.wikipedia.org/wiki/Design_science_(methodology))
- [DSR Methodology Framework](https://dl.acm.org/doi/10.2753/MIS0742-1222240302)

---

## Evaluation Framework (FEDS)

### Framework for Evaluation in Design Science

**Two dimensions**:
1. **Functional purpose**: Formative (improve artifact) vs. Summative (assess achievement)
2. **Evaluation paradigm**: Artificial (lab-based) vs. Naturalistic (real-world)

**Evaluation methods** (can be mixed):
- Non-empirical (argument, scenarios)
- Empirical positivist (experiments, simulations)
- Empirical interpretive (case studies, action research)
- Critical (contextual analysis)

**Best practice**: Use multiple evaluation methods for robust validation, transitioning from artificial/formative early to naturalistic/summative later.

**Sources**:
- [FEDS Framework](https://www.tandfonline.com/doi/full/10.1057/ejis.2014.36)
- [Comprehensive Evaluation Framework](https://link.springer.com/chapter/10.1007/978-3-642-29863-9_31)

---

## Recent Developments (2024-2025)

### Design Echelons for Complexity

**Challenge**: Complex DSR projects can be overwhelming.

**Solution**: Decompose DSR into "echelons" (smaller logically coherent components) based on hierarchical, multilevel systems theory.

**Benefit**: More manageable components while maintaining coherence.

**Source**: [Dealing with Complexity in DSR](https://misq.umn.edu/misq/article/48/2/427/2267/Dealing-with-Complexity-in-Design-Science-Research)

---

### Validity Framework

**Three validity types**:
1. **Criterion validity**: Does artifact meet specified criteria?
2. **Causal validity**: Does artifact cause intended outcomes?
3. **Context validity**: When and where does artifact work?

**Best practice**: Specify conditions and boundaries under which artifact is expected to achieve outcomes.

**Source**: [Validity in Design Science](https://misq.umn.edu/misq/article/49/4/1267/3273/Validity-in-Design-Science1)

---

### Knowledge Communication

**What to communicate**:
- How artifact was built (code repositories, conceptual descriptions)
- When and under what conditions artifact achieves outcomes
- Boundary conditions and limitations
- Theoretical contributions

**Audiences**: Both technical (implementation details) and managerial (business value)

**Source**: [DSR Post Hevner](https://link.springer.com/chapter/10.1007/978-3-642-13335-0_8)

---

## Common Artifacts in DSR

**Four types**:
1. **Constructs**: Vocabulary and symbols (conceptual models, taxonomies)
2. **Models**: Abstractions and representations (design theories, frameworks)
3. **Methods**: Algorithms and practices (procedures, protocols)
4. **Instantiations**: Implemented systems (prototypes, products)

**Most common in IS**: Software systems, algorithms, design theories, frameworks

---

## Iteration and Rigor

**Build-Evaluate Cycle**: Cyclical model of DSR iterations comprising development, building, and evaluation activities.

**Rigor requirements**:
- Use established theories and methods
- Document design decisions and rationale
- Systematic evaluation against objectives
- Acknowledge limitations and threats to validity

**Timeline**: Typically 2-4 build-evaluate cycles over 4-12 weeks

---

## Integration with Other Methods

**Common combinations**:
- **DSR + Systematic Review**: Review existing solutions → Build improved artifact
- **DSR + UX Research**: Understand users → Build user-centered artifact
- **DSR + Case Study**: Evaluate artifact in real organizational context

---

## Quality Criteria

**High-quality DSR demonstrates**:
- Clear problem importance (relevance)
- Novel artifact contribution (innovation)
- Rigorous evaluation (multiple methods)
- Explicit design knowledge (communicable)
- Practical utility (solves real problem)

---

## When NOT to Use DSR

**Inappropriate scenarios**:
- Pure exploratory research (no artifact to build)
- Routine application of existing solutions
- Purely theoretical research
- When evaluation in context not feasible

---

## Related Standards

- [[systematic-review-standards]] - For literature component in DSR
- [[ux-research-standards]] - For user validation in DSR
- [[case-study-standards]] - For naturalistic evaluation

---

## Sources Summary

**Foundational**:
- Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design science in information systems research.
- [A Design Science Research Methodology for IS Research](https://dl.acm.org/doi/10.2753/MIS0742-1222240302)

**Evaluation**:
- [FEDS: Framework for Evaluation in Design Science](https://www.tandfonline.com/doi/full/10.1057/ejis.2014.36)
- [Comprehensive Framework for Evaluation in DSR](https://link.springer.com/chapter/10.1007/978-3-642-29863-9_31)

**Recent Developments**:
- [Dealing with Complexity in DSR (2024)](https://misq.umn.edu/misq/article/48/2/427/2267/Dealing-with-Complexity-in-Design-Science-Research)
- [Validity in Design Science (2025)](https://misq.umn.edu/misq/article/49/4/1267/3273/Validity-in-Design-Science1)
- [DSR Post Hevner Guidelines](https://link.springer.com/chapter/10.1007/978-3-642-13335-0_8)

---

**Use for**: Implementing `researcher/design-science/workflow.md`
