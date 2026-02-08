## Phase 1: Domain Discovery (15-30 min)

**Goal**: Identify YOUR key domains through guided questions.

### Step 1.1: Explain the Approach

Say:
```
I'll help you set up a context management system using Anthropic's best practices.

Instead of generic categories like "preferences" or "standards," we'll organize by the TOPICS that matter to your work—like "python," "security," or "research."

This makes context instantly discoverable: need Python conventions? → context/python/

First, let's discover what domains are relevant to you.

Ready?
```

### Step 1.2: Discover Work Context

Ask discovery questions using AskUserQuestion:

**Question 1: Primary Work Type**
```yaml
question: "What type of work do you primarily do with Claude?"
header: "Work Type"
multiSelect: false
options:
  - label: "Software Development"
    description: "Writing code, building applications, engineering work"
  - label: "Research & Analysis"
    description: "Literature reviews, data analysis, academic work"
  - label: "Knowledge Management"
    description: "Note-taking, PKM, documentation, learning"
  - label: "Mixed/Multiple"
    description: "Combination of the above"
```

**Question 2: Programming Languages** (if software dev selected)
```yaml
question: "Which programming languages do you use regularly?"
header: "Languages"
multiSelect: true
options:
  - label: "Python"
    description: "Python development, scripting, data science"
  - label: "JavaScript/TypeScript"
    description: "Web development, Node.js"
  - label: "Other languages"
    description: "Go, Rust, Java, C#, etc."
```

**Question 3: Security & Standards** (if software dev selected)
```yaml
question: "Do you need security standards in your work?"
header: "Security"
multiSelect: false
options:
  - label: "Yes - OWASP/OAuth/API security"
    description: "Building production systems with security requirements"
  - label: "Yes - Data privacy/compliance"
    description: "GDPR, HIPAA, or other compliance frameworks"
  - label: "Not currently"
    description: "May need in future"
```

**Question 4: Research Domains** (if research selected)
```yaml
question: "What research methods do you use?"
header: "Research"
multiSelect: true
options:
  - label: "Systematic Reviews"
    description: "PRISMA, literature synthesis, meta-analysis"
  - label: "Qualitative Analysis"
    description: "Interviews, case studies, thematic analysis"
  - label: "Data Analysis"
    description: "Statistical analysis, data science"
```

**Question 5: Knowledge Management** (if PKM selected)
```yaml
question: "What types of notes do you create?"
header: "Note Types"
multiSelect: true
options:
  - label: "Book Notes & Reading"
    description: "Book summaries, reading notes, learning materials"
  - label: "Mental Models & Frameworks"
    description: "Conceptual frameworks, thinking tools"
  - label: "Recipes or Collections"
    description: "Structured collections with templates"
```

**Question 6: Communication Preferences**
```yaml
question: "How should Claude communicate with you?"
header: "Communication"
multiSelect: false
options:
  - label: "Review-first (propose before acting)"
    description: "Prefer to review plans before execution"
  - label: "Action-first (execute immediately)"
    description: "Prefer Claude to act and iterate"
  - label: "Balanced (context-dependent)"
    description: "Depends on the task"
```

### Step 1.3: Map Responses to Domains

Based on answers, recommend domains:

**Software Development** → Suggest:
- `skills/` - Claude Code skill development standards
- `{language}/` - Language-specific conventions (python, javascript, etc.)
- `security/` - Security standards (if selected)
- `patterns/` - Reusable patterns (if building tools)

**Research** → Suggest:
- `research/` - Research methods and synthesis
- `learning/` - Learning frameworks and note-taking
- `patterns/` - Analysis patterns

**Knowledge Management** → Suggest:
- `obsidian/` (if using Obsidian) or `note-system/`
- `learning/` - Learning preferences
- `{note-type}/` - Domain for specific note types (recipes, mental-models)

**Always include**:
- `communication/` - Communication preferences
- `decisions/` - Architectural decisions
- `context-system/` - Meta documentation about the system itself

### Step 1.4: Present Recommended Structure

**IMPORTANT**: Ensure at least ONE user domain (beyond core) is selected. If user's answers suggest no clear domains, recommend `learning/` or `workflows/` as starter domain.

Say:
```
Based on your work, I recommend these domains:

Core Domains (everyone):
  - communication/ - How you prefer to work with Claude
  - decisions/ - Architectural decisions with rationale
  - context-system/ - Meta documentation (what is context, organizing principles, quality standards)

Your Domains (based on your work):
  - [domain 1]/ - [description]
  - [domain 2]/ - [description]
  - [domain 3]/ - [description]

[If no user domains emerged from discovery, add:]
Recommended Starter Domain:
  - learning/ or workflows/ - General patterns and processes

Optional Domains (you can add later):
  - [optional 1]/ - [description]

This structure follows Anthropic's concept-based organization: each folder represents a TOPIC, not a document type.

context-system/ will include foundational guidance so you can reference your own context system's documentation.

Sound good? Want to adjust anything?
```

**Validation**: Ensure domain list includes:
- 3 core domains (communication, decisions, context-system)
- At least 1 user domain (python, security, learning, etc.)

Use AskUserQuestion to let user approve or modify.

### Step 1.5: Create Domain Structure

Create directories based on approved domains:
```bash
mkdir -p context/{communication,decisions,context-system,[user-domains]}
```

Say:
```
✓ Created concept-based context structure

Each domain will contain:
- _index.md - Navigation with "When to Use" guidance
- Topic-specific files (max 2 levels deep)

This follows [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) for skill structure.
```

---

