# Audit Types Reference

This document details the five audit types supported by the audit skill, based on ISO 19011:2018 and ISO 25010:2023 standards.

**Quick selection**:
- Quality issues? → Quality Audit (ISO 25010)
- Standards adherence? → Compliance Audit
- Security concerns? → Security Audit (OWASP)
- Performance degradation? → Performance Audit
- Regular review? → Comprehensive Audit

---

## 1. Quality Audit (ISO 25010)

**Purpose**: Assess quality dimensions defined by ISO/IEC 25010:2023 Software Quality Model.

**Standards basis**: [ISO/IEC 25010:2023](https://www.iso.org/standard/35733.html) - Software Product Quality Requirements and Evaluation

### Dimensions Assessed

Eight quality characteristics from ISO 25010:

1. **Functional Suitability** - Does it do what it should?
   - Functional completeness
   - Functional correctness
   - Functional appropriateness

2. **Performance Efficiency** - How well does it use resources?
   - Time behavior (response time, throughput)
   - Resource utilization (memory, CPU, storage)
   - Capacity (maximum limits)

3. **Compatibility** - Works with other components?
   - Co-existence with other systems
   - Interoperability between systems

4. **Usability** - Easy to use and understand?
   - Appropriateness recognizability
   - Learnability
   - Operability
   - User error protection
   - User interface aesthetics
   - Accessibility

5. **Reliability** - Works consistently without failure?
   - Maturity (frequency of failure)
   - Availability (operational when needed)
   - Fault tolerance (operates despite faults)
   - Recoverability (recovers data after failure)

6. **Security** - Protects information and data?
   - Confidentiality
   - Integrity
   - Non-repudiation
   - Accountability
   - Authenticity

7. **Maintainability** - Easy to modify and extend?
   - Modularity
   - Reusability
   - Analyzability
   - Modifiability
   - Testability

8. **Portability** - Can be transferred to different contexts?
   - Adaptability
   - Installability
   - Replaceability

### When to Use

- **Quarterly**: Routine quality drift detection
- **After major refactoring**: Validate quality improvements
- **When usability complaints increase**: Targeted assessment
- **Before releases**: Quality gate check

### Assessment Method

**Rating scale**: 1-5 for each dimension
- 5: Excellent (exceeds requirements)
- 4: Good (meets requirements with margin)
- 3: Acceptable (meets minimum requirements)
- 2: Poor (gaps in requirements)
- 1: Critical (does not meet requirements)

**Example quality audit checklist**: `context/workflows/standards/[artifact]-quality-checklist.md`

### Quality Audit Output

```markdown
## Quality Audit: [Artifact Name]

### ISO 25010 Assessment (1-5 scale)
- Functional Suitability: [rating] - [notes]
- Performance Efficiency: [rating] - [notes]
- Compatibility: [rating] - [notes]
- Usability: [rating] - [notes]
- Reliability: [rating] - [notes]
- Security: [rating] - [notes]
- Maintainability: [rating] - [notes]
- Portability: [rating] - [notes]

### Overall Quality Score: [average]

### Strengths: [list]
### Weaknesses: [list]
### Recommendations: [prioritized actions]
```

---

## 2. Compliance Audit

**Purpose**: Verify adherence to internal standards, external regulations, and format requirements.

**Standards basis**: Internal skill-structure-standard, vault-conventions, domain-specific standards

### Dimensions Assessed

1. **Standards Adherence**
   - Follows documented internal standards
   - Complies with external regulations (if applicable)
   - Meets quality thresholds

2. **Required Fields Present**
   - Frontmatter complete (name, description, tools)
   - Mandatory sections present
   - Metadata populated

3. **Format Validation**
   - Structure matches template
   - Syntax correct (YAML, markdown)
   - Consistent formatting

4. **Naming Conventions**
   - File names follow kebab-case
   - Tags lowercase
   - Directories organized correctly

5. **Documentation Completeness**
   - All required documentation present
   - Cross-references complete
   - No orphaned files

### When to Use

- **Before releases**: Compliance gate check
- **Quarterly reviews**: Systematic compliance assessment
- **After standards updates**: Validate adoption
- **Onboarding new artifacts**: Baseline compliance

### Assessment Method

**Binary check**: PASS/FAIL for each criterion
- PASS: Meets requirement
- FAIL: Does not meet requirement (document specifics)

**Compliance percentage**: (Passed checks / Total checks) × 100%

**Target**: >90% compliance for most artifact types

**Example compliance checklist**: `context/workflows/standards/[artifact]-compliance-checklist.md`

### Compliance Audit Output

```markdown
## Compliance Audit: [Artifact Name]

### Compliance Score: [X]% ([passed]/[total] checks)

### Passed Checks ✓
[List compliant areas]

### Failed Checks ✗
1. [Check name] - [Specific issue] - [Priority: HIGH/MEDIUM/LOW]
2. [Check name] - [Specific issue] - [Priority]

### Recommendations
[Prioritized remediation actions]

### Compliance Trend
[Compared to previous audit - improving/stable/declining]
```

---

## 3. Security Audit (OWASP)

**Purpose**: Identify vulnerabilities, assess risks, verify security best practices following OWASP Top 10:2025.

**Standards basis**: [OWASP Top 10:2025](https://owasp.org/Top10/), CVE database, security best practices

### Dimensions Assessed

Based on OWASP Top 10:2025:

1. **Vulnerability Scanning**
   - Known CVEs in dependencies
   - Outdated packages with security issues
   - Common vulnerability patterns (XSS, SQL injection, etc.)

2. **Dependency Security**
   - Outdated dependencies
   - Vulnerable package versions
   - Supply chain integrity (SBOM, hashes)
   - License compliance

3. **Access Control**
   - Authentication mechanisms
   - Authorization checks
   - Principle of least privilege
   - Session management

4. **Data Protection**
   - Encryption at rest and in transit
   - Input sanitization
   - Output encoding
   - Sensitive data handling

5. **Supply Chain Security** (OWASP A03:2025)
   - Software Bill of Materials (SBOM)
   - Dependency integrity verification (SHA256 hashes)
   - Trusted sources only
   - Regular dependency updates

6. **Configuration Security** (OWASP A02:2025)
   - Secure defaults
   - No hardcoded credentials
   - Error messages sanitized
   - Security logging enabled

### When to Use

- **After dependency updates**: Verify no new vulnerabilities
- **Quarterly security reviews**: Comprehensive security posture
- **Before production deployment**: Security gate check
- **After security incidents**: Root cause analysis

### Assessment Method

**Risk rating**: Critical / High / Medium / Low
- **Critical**: Immediate exploitation possible, high impact
- **High**: Exploitation likely, significant impact
- **Medium**: Exploitation possible, moderate impact
- **Low**: Exploitation unlikely or low impact

**Tools**:
- `pip-audit` for Python dependencies
- `npm audit` for JavaScript dependencies
- OWASP ZAP for web vulnerabilities
- Manual code review for logic flaws

**Example security checklist**: `context/workflows/standards/[artifact]-security-checklist.md`

### Security Audit Output

```markdown
## Security Audit: [Artifact Name]

### Risk Summary
- Critical: [count]
- High: [count]
- Medium: [count]
- Low: [count]

### Vulnerabilities Found

#### Critical
1. [CVE-YYYY-XXXXX] - [Package] [Version] - [Description]
   - Impact: [description]
   - Remediation: Upgrade to [version]

#### High
[List]

#### Medium
[List]

### OWASP Top 10:2025 Compliance
- A01 (Broken Access Control): [PASS/FAIL/N/A]
- A02 (Cryptographic Failures): [PASS/FAIL/N/A]
- A03 (Injection): [PASS/FAIL/N/A]
[...]

### Recommendations
[Prioritized security improvements]
```

---

## 4. Performance Audit

**Purpose**: Assess efficiency, resource usage, and performance characteristics to identify optimization opportunities.

### Dimensions Assessed

1. **Size Efficiency**
   - File size (bytes, lines of code)
   - Asset sizes (images, bundles)
   - Payload sizes (API responses)

2. **Speed/Latency**
   - Execution time
   - Response time
   - Load time
   - Time to interactive

3. **Resource Usage**
   - Memory consumption
   - CPU utilization
   - Network bandwidth
   - Token usage (for AI/LLM tools)
   - Storage requirements

4. **Scalability**
   - Performance under load
   - Concurrent user support
   - Data volume limits
   - Growth trajectory

### When to Use

- **When performance degrades**: Identify bottlenecks
- **Quarterly performance reviews**: Track performance trends
- **Before scaling operations**: Validate capacity
- **After optimization efforts**: Measure improvements

### Assessment Method

**Quantitative metrics**: Measure actual performance
- Baseline: First measurement
- Target: Desired performance
- Current: Latest measurement
- Trend: Improving/stable/degrading

**Benchmarking**: Compare against:
- Historical performance (trend analysis)
- Similar artifacts (peer comparison)
- Industry standards (external benchmarks)
- Performance budgets (defined limits)

**Example performance checklist**: `context/workflows/standards/[artifact]-performance-checklist.md`

### Performance Audit Output

```markdown
## Performance Audit: [Artifact Name]

### Performance Metrics

| Metric | Target | Current | Status | Trend |
|--------|--------|---------|--------|-------|
| File Size | <500 lines | 450 lines | ✓ | Stable |
| Response Time | <100ms | 85ms | ✓ | Improving |
| Memory Usage | <100MB | 75MB | ✓ | Stable |
| Token Usage | <10k | 8.5k | ✓ | Increasing |

### Bottlenecks Identified
[List performance issues]

### Optimization Opportunities
[Prioritized improvements with estimated impact]

### Performance Trend
[Historical comparison - improving/stable/degrading]
```

---

## 5. Comprehensive Audit

**Purpose**: Assess all dimensions (quality, compliance, security, performance) in single audit cycle for holistic view.

**Recommended frequency**: Quarterly

**Combines**: All four audit types above

### When to Use

- **Regular quarterly audits**: Comprehensive health check
- **Annual deep reviews**: Complete assessment
- **Before major releases**: All-dimensions gate check
- **After significant changes**: Validate impact across dimensions

### Assessment Method

1. **Run all four audits** (quality, compliance, security, performance)
2. **Aggregate findings** by priority
3. **Identify cross-cutting issues** (problems affecting multiple dimensions)
4. **Create unified action plan** (prioritized across all dimensions)

### Comprehensive Audit Output

```markdown
## Comprehensive Audit: [Artifact Name]

### Executive Summary
- Quality: [score]/5 - [status]
- Compliance: [X]% - [status]
- Security: [risk level] - [status]
- Performance: [status]

### Overall Health: [Excellent/Good/Acceptable/Poor/Critical]

### Critical Issues (All Dimensions)
[Prioritized list combining all audits]

### Action Plan
#### Immediate (Do Now)
[Critical items from all dimensions]

#### This Cycle (Next 2 Weeks)
[High priority items]

#### Next Cycle (Q[N] 202X)
[Medium priority items]

### Trends
[Historical comparison across all dimensions]

### Next Audit: [Date]
```

---

## Audit Type Selection Guide

**Decision tree**:

```
Is this a regular review?
├─ Yes, quarterly → Comprehensive Audit
└─ No, specific concern
   ├─ Usability/maintainability issues? → Quality Audit
   ├─ Standards not followed? → Compliance Audit
   ├─ Security vulnerability? → Security Audit
   └─ Performance degraded? → Performance Audit
```

**Frequency recommendations**:

| Audit Type | Frequency | Effort | Output |
|------------|-----------|--------|--------|
| Quality | Quarterly | 2-3h | ISO 25010 ratings |
| Compliance | Quarterly / Before releases | 1-2h | Pass/Fail with % |
| Security | Quarterly / After deps update | 1-3h | Risk levels, CVEs |
| Performance | As needed / Quarterly | 1-2h | Metrics, trends |
| Comprehensive | Quarterly | 4-6h | All dimensions |

---

## Related Documentation

- [[SKILL]] - Main audit skill orchestration
- [[patterns/audit-pattern]] - Generic audit pattern (ISO 19011-based)
- [[skills/audit-checklist]] - Skills-specific checklist
- [[context/workflows/patterns/implementations/skill-audit-implementation]] - Skills audit implementation

---

## Standards References

**ISO 25010**: [ISO/IEC 25010:2023](https://www.iso.org/standard/35733.html) - Software Product Quality
**ISO 19011**: [ISO 19011:2018](https://www.iso.org/standard/70017.html) - Auditing Management Systems
**OWASP Top 10**: [OWASP Top 10:2025](https://owasp.org/Top10/) - Web Application Security Risks
**CVE Database**: [cve.mitre.org](https://cve.mitre.org/) - Common Vulnerabilities and Exposures
