# Diagram Types Reference

Complete guide to all supported Mermaid diagram types with syntax examples.

---

## Type 1: Flowchart (Process Flow)

**Use For**: Processes, workflows, decision trees, algorithms

**Mermaid Syntax**:
```mermaid
flowchart TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Action 1]
    B -->|No| D[Action 2]
    C --> E[End]
    D --> E
```

**Example**: First Principles Thinking process
```mermaid
flowchart TD
    A[Problem Statement] --> B[Identify Assumptions]
    B --> C[Challenge Each Assumption]
    C --> D{Assumption Valid?}
    D -->|No| E[Break Down Further]
    D -->|Yes| F[Keep as Fundamental]
    E --> G[Reach Ground Truth]
    F --> G
    G --> H[Reason Up from Fundamentals]
    H --> I[Novel Solution]
```

**Best For**:
- Sequential processes
- Decision logic
- Algorithm flows
- Step-by-step procedures

---

## Type 2: Concept Map (Relationships)

**Use For**: Mental model relationships, idea connections, concept hierarchies

**Mermaid Syntax**:
```mermaid
graph LR
    A[First Principles] -->|Breaks Down| B[Complex Problems]
    A -->|Identifies| C[Fundamental Truths]
    C -->|Enables| D[Novel Solutions]
    A -->|Contrasts With| E[Reasoning by Analogy]
    A -->|Builds On| F[Systems Thinking]
```

**Example**: Mental Model Ecosystem
```mermaid
graph TD
    FP[First Principles] -->|Foundation For| ST[Systems Thinking]
    FP -->|Enables| SOT[Second-Order Thinking]
    ST -->|Combines With| SOT
    SOT -->|Leads To| BC[Better Choices]
    FP -->|Avoids| RA[Reasoning by Analogy]
    ST -->|Reveals| EM[Emergent Properties]
```

**Best For**:
- Relationships between concepts
- Knowledge networks
- Cause-and-effect chains
- Conceptual dependencies

---

## Type 3: Class Diagrams (Structure)

**Use For**: Taxonomies, classifications, component breakdowns

**Mermaid Syntax**:
```mermaid
classDiagram
    MentalModel <|-- FirstPrinciples
    MentalModel <|-- SystemsThinking
    MentalModel <|-- SecondOrderThinking
    FirstPrinciples : +identify_assumptions()
    FirstPrinciples : +break_down()
    FirstPrinciples : +reason_up()
```

**Best For**:
- Inheritance relationships
- Component structures
- Classification systems
- Object hierarchies

---

## Type 4: Sequence Diagrams (Temporal Flow)

**Use For**: Workflows over time, interactions, step-by-step processes

**Mermaid Syntax**:
```mermaid
sequenceDiagram
    participant User
    participant FirstPrinciples
    participant Solution
    User->>FirstPrinciples: Problem Statement
    FirstPrinciples->>FirstPrinciples: Identify Assumptions
    FirstPrinciples->>FirstPrinciples: Break to Fundamentals
    FirstPrinciples->>Solution: Reason Up
    Solution->>User: Novel Approach
```

**Best For**:
- Actor interactions
- Message flows
- API call sequences
- Time-ordered events

---

## Type 5: Mindmaps (Radial Structure)

**Use For**: Brainstorming, topic exploration, hierarchical breakdowns

**Mermaid Syntax**:
```mermaid
mindmap
  root((First Principles))
    Origins
      Aristotle
      Descartes
      Elon Musk
    Process
      Identify Assumptions
      Break Down
      Reason Up
    Applications
      Battery Costs
      Meetings
      Architecture
    When to Use
      Novel Problems
      Flawed Assumptions
    When to Avoid
      Time Constrained
      Proven Solutions
```

**Best For**:
- Central concept with branches
- Hierarchical organization
- Brainstorming sessions
- Topic exploration

---

## Type 6: Gantt Charts (Timeline)

**Use For**: Schedules, project plans, temporal dependencies

**Mermaid Syntax**:
```mermaid
gantt
    title Learning Workflow
    dateFormat  YYYY-MM-DD
    section Study
    Read Mental Model    :2026-02-01, 1d
    Generate Flashcards  :2026-02-02, 1d
    section Review
    First Review         :2026-02-03, 1d
    Second Review        :2026-02-05, 1d
    section Apply
    Real-World Use       :2026-02-08, 7d
```

**Best For**:
- Project timelines
- Task dependencies
- Schedule planning
- Milestone tracking

---

## Quick Selection Guide

| Content Type | Recommended Diagram |
|--------------|---------------------|
| Process with steps | Flowchart |
| Idea relationships | Concept Map |
| Classification | Class Diagram |
| Actor interactions | Sequence Diagram |
| Hierarchical breakdown | Mindmap |
| Timeline/schedule | Gantt Chart |
| Decision logic | Flowchart |
| Network of concepts | Concept Map |

---

**Back to**: [[SKILL|Main Skill Documentation]]
