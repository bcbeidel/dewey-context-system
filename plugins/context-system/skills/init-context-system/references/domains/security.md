
**Create `context/security/_index.md`**:
```markdown
---
title: Security Standards
type: index
created: [YYYY-MM-DD]
---

# Security Domain

Security best practices grounded in OWASP and OAuth 2.1 standards.

## When to Use

Load this domain when:
- Developing production applications
- Handling credentials or sensitive data
- Implementing authentication/authorization
- Reviewing code for security issues

## Files

- best-practices.md - OWASP Top 10 compliance

## External Authorities

Grounded in:
- OWASP Top 10 (2025): https://owasp.org/www-project-top-ten/
- OAuth 2.1: https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-11

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#3-security-standards) for complete mapping.

---

*Created: [YYYY-MM-DD]*
```

**Create `context/security/best-practices.md`**:
```markdown
---
title: Security Best Practices
created: [YYYY-MM-DD]
keywords: [security, owasp, credentials, authentication]
applies-to: [development, code-review, production]
tags: [context, security]
---

# Security Best Practices

## Summary

Security practices grounded in OWASP Top 10 (2025) standards.

## Standards Source

**Authority**: [OWASP Top 10](https://owasp.org/www-project-top-ten/)

## Key Principles

### A02: Cryptographic Failures
**Requirement**: Protect sensitive data in transit and at rest

**In practice**:
- Store credentials in OS keychain (never plaintext)
- Use HTTPS for all API calls
- Encrypt sensitive data at rest

**Example**:
```python
# ✓ Good: OS keychain
import keyring
token = keyring.get_password("app", "api_token")

# ✗ Bad: Plaintext .env
token = os.getenv("API_TOKEN")  # Avoid
```

### A04: Insecure Design
**Requirement**: Fail-closed validation

**In practice**:
- Explicit permission checks (hard fail if unclear)
- Validate all inputs
- Secure defaults

### A09: Security Logging Failures
**Requirement**: SIEM-ready logging

**In practice**:
- JSON structured logs
- Sanitize sensitive data from logs
- Include context (timestamp, user, action)

## Related Context
