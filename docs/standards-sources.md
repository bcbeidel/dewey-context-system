# Standards & Sources

**Purpose**: Explicitly document the external authoritative sources that ground this context system's patterns and recommendations.

This document makes it **self-evident** that we're not inventing best practices - we're operationalizing proven standards from authoritative sources.

---

## Quick Reference

All patterns in this repository are grounded in external authoritative sources:

| Pattern | Authority | Verification URL |
|---------|-----------|------------------|
| **Skill Structure** | Anthropic Best Practices | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices |
| **Audit Framework** | ISO 19011:2018 | https://www.iso.org/standard/70017.html |
| **Security** | OWASP Top 10 (2025) | https://owasp.org/www-project-top-ten/ |
| **Research Synthesis** | PRISMA 2020 | http://www.prisma-statement.org/ |
| **Python Conventions** | PEP 8 | https://peps.python.org/pep-0008/ |
| **OAuth Implementation** | OAuth 2.1 (RFC Draft) | https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11 |

**For detailed mapping and implementation guidance, see sections below.**

---

## Core Principle: Grounded in External Authorities

Every pattern in this system is **anchored to an external authority**:
- ✅ **Skill structure** → Anthropic's official best practices
- ✅ **Audit framework** → ISO 19011:2018
- ✅ **Security standards** → OWASP Top 10
- ✅ **Research synthesis** → PRISMA 2020
- ✅ **Python conventions** → PEP 8

**Why this matters**: External authorities provide:
- **Credibility** - Not opinions, but proven standards
- **Verifiability** - Anyone can check the source
- **Stability** - Standards evolve slowly and deliberately
- **Transferability** - Recognized across organizations

---

## 1. Skill Structure & Best Practices

### Primary Source: Anthropic Documentation
**URL**: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices

**Key principles from Anthropic**:

#### Progressive Disclosure
> "Start with a clear, concise overview. Provide details progressively as needed."

**Our implementation**:
- SKILL.md kept <400 lines (proactive threshold)
- Details extracted to `references/` directory when needed
- Main file provides overview + navigation

#### Flat Structure (Max 2 Levels)
> "Keep directory structure shallow to improve discoverability"

**Our implementation**:
- `context/{domain}/{file}.md` (max 2 levels)
- `references/` optional for extracted content
- No deep nesting (no `domain/subdomain/subsubdomain/`)

#### Clear Entry Points
> "Provide index files with clear 'When to Use' guidance"

**Our implementation**:
- Every domain has `_index.md`
- Each index includes "When to Use" section
- Main `context/_index.md` maps tasks to domains

#### Purpose-Based Organization
> "Organize by topic/purpose, not by document type"

**Our implementation**:
- Domains organized by concept (skills, security, python) not type (standards, workflows, preferences)
- `/init-context-system` uses discovery questions to identify user's relevant domains

---

### Supporting Source: Anthropic Prompt Engineering Guide
**URL**: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

**Key principles**:
- **Explicit over implicit** - State preferences clearly
- **Examples grounded in context** - Show, don't just tell
- **Iterative refinement** - Improve based on real use

**Our implementation**:
- Context files capture explicit preferences
- Examples extracted from actual work
- `/context-curator` skill for iterative improvement

---

## 2. Audit Framework

### Primary Source: ISO 19011:2018
**Title**: "Guidelines for auditing management systems"
**Publisher**: International Organization for Standardization

**Key principles from ISO 19011**:

#### Seven Audit Principles
1. **Integrity** - Foundation of professionalism
2. **Fair presentation** - Obligation to report truthfully
3. **Due professional care** - Application of diligence
4. **Confidentiality** - Security of information
5. **Independence** - Basis for impartiality
6. **Evidence-based approach** - Verifiable information
7. **Risk-based approach** - Focus on significant risks

**Our implementation**: `/audit` skill (see plugins/context-system/skills/audit/)

#### Risk-Based Prioritization
> "Audit approach should consider risks and opportunities"

**Our implementation**:
```python
priority_score = (impact * likelihood * change_frequency) / complexity
```

#### Evidence-Based Assessment
> "Audit findings based on verifiable audit evidence"

**Our implementation**:
- Quantitative checks (automated scripts for wikilinks, tags, etc.)
- Qualitative assessment (readability checklists)
- Documented evidence for each finding

---

## 3. Security Standards

### Primary Source: OWASP Top 10 (2025)
**URL**: https://owasp.org/www-project-top-ten/

**Relevant standards**:

- **A02:2025 - Cryptographic Failures**
  - **Requirement**: Protect sensitive data in transit and at rest
  - **Our implementation**: OS keychain storage (AES-256), no plaintext credentials

- **A03:2025 - Supply Chain Vulnerabilities**
  - **Requirement**: Verify dependencies, pin versions
  - **Our implementation**: requirements.txt with SHA256 hashes

- **A04:2025 - Insecure Design**
  - **Requirement**: Fail-closed validation
  - **Our implementation**: Explicit permission checks, hard fail on excess permissions

- **A09:2025 - Security Logging Failures**
  - **Requirement**: SIEM-ready logging
  - **Our implementation**: JSON structured logging with sanitized sensitive data

- **A10:2025 - Server-Side Request Forgery**
  - **Requirement**: Robust error handling
  - **Our implementation**: Exponential backoff retry logic (tenacity)

**Guidance**: Security best practices documented when creating security/ domain via `/init-context-system`

---

### Supporting Source: OAuth 2.1
**RFC**: https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11

**Requirements**:
- PKCE required for all flows
- JWT signature verification mandatory
- Refresh token rotation

**Guidance**: OAuth requirements documented when creating security/ domain

---

## 4. Research Synthesis

### Primary Source: PRISMA 2020
**Title**: "Preferred Reporting Items for Systematic Reviews and Meta-Analyses"
**URL**: http://www.prisma-statement.org/

**Key requirements**:
- Protocol registration (PROSPERO)
- PICO framework (Population, Intervention, Comparator, Outcome)
- Comprehensive search strategy
- Duplicate review process
- Risk of bias assessment
- Transparent reporting (27-item checklist)

**Our implementation**: `/systematic-review` skill

**Supporting source**: AMSTAR-2, ROBIS (quality assessment tools)

---

## 5. Python Conventions

### Primary Source: PEP 8
**Title**: "Style Guide for Python Code"
**URL**: https://peps.python.org/pep-0008/

**Key guidelines**:
- 4 spaces indentation (no tabs)
- Maximum line length: 79 characters (code), 72 (docstrings)
- Imports at top, grouped (standard → third-party → local)
- Naming: snake_case for functions/variables, PascalCase for classes

**Guidance**: Python conventions documented when creating python/ domain via `/init-context-system`

**Supporting sources**:
- PEP 484 (Type Hints)
- PEP 257 (Docstring Conventions)
- PEP 20 (The Zen of Python)

---

## How Standards Are Maintained

### Standards Synchronization Pattern

**Process**:
1. **Monitor** - Track updates to external authorities (quarterly)
2. **Evaluate** - Assess relevance to your context
3. **Update** - Modify internal standards based on external changes
4. **Migrate** - Update implementations to match new standards
5. **Measure** - Track adoption and effectiveness

**Implementation**: `/standards-sync` skill (see plugins/context-system/skills/standards-sync/)

**Registry**: Created in your context/context-system/standards-sync-registry.md when you run the skill

---

## Verification

Anyone can verify our standards by checking the verification URLs in the [Quick Reference](#quick-reference) table above.

**Key insight**: If an external authority changes, we update via `/standards-sync`. This keeps us current without constant manual checking.

---

## Why This Matters

### Without External Grounding
- ❌ Opinions presented as best practices
- ❌ No way to verify correctness
- ❌ Drift over time as standards evolve
- ❌ Difficult to justify to teams

### With External Grounding
- ✅ Credible, verifiable standards
- ✅ Clear rationale for decisions
- ✅ Automatic updates via standards-sync
- ✅ Recognized across organizations

---

## Related Documentation

- **[Plugin README](../plugins/context-system/README.md)** - Overview of all 7 skills
- **[init-context-system Skill](../plugins/context-system/skills/init-context-system/SKILL.md)** - Concept-based setup
- **[audit Skill](../plugins/context-system/skills/audit/SKILL.md)** - ISO 19011 implementation
- **[standards-sync Skill](../plugins/context-system/skills/standards-sync/SKILL.md)** - How to stay current

---

**Last Updated**: February 2026
**Next Review**: Q2 2026 (via `/standards-sync`)
