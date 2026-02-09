---
tags:
- context
---
# Security: Validation & Audit

## Summary

Permission validation with fail-closed design, audit logging for SIEM integration, and multi-account isolation patterns.

**See also**: [[security/practices]] (overview)

---

## Permission Validation

### Fail-Closed Validation (REQUIRED)

**Rule**: HARD FAIL if token has excess permissions.

**Why**: Prevents privilege escalation and accidental data writes.

**Implementation**:
```python
class PermissionValidator:
    """Validate token permissions with fail-closed design."""

    def validate_scopes(
        self,
        token: str,
        required_scopes: set[str],
        forbidden_scopes: set[str]
    ):
        """
        Validate token has exactly required scopes (no more, no less).

        Args:
            token: Access token to validate
            required_scopes: Scopes that MUST be present
            forbidden_scopes: Scopes that MUST NOT be present

        Raises:
            PermissionError: If validation fails
        """
        granted_scopes = self._extract_scopes(token)

        # Check required scopes present
        missing = required_scopes - granted_scopes
        if missing:
            raise PermissionError(
                f"Token missing required scopes: {missing}\n"
                f"Required: {required_scopes}\n"
                f"Granted: {granted_scopes}"
            )

        # Check forbidden scopes absent (FAIL-CLOSED)
        excess = granted_scopes & forbidden_scopes
        if excess:
            raise PermissionError(
                f"Token has excess permissions: {excess}\n"
                f"Required: {required_scopes}\n"
                f"Granted: {granted_scopes}\n"
                f"Refusing to proceed. Generate token with correct scopes."
            )

        # Log successful validation
        audit_logger.log_security_event('PERMISSION_VALIDATED', {
            'required_scopes': list(required_scopes),
            'granted_scopes': list(granted_scopes)
        })
```

**Example usage**:
```python
# SharePoint read operation
validator.validate_scopes(
    token=sharepoint_token,
    required_scopes={'Files.Read'},
    forbidden_scopes={'Files.ReadWrite', 'Files.ReadWrite.All', 'Sites.FullControl.All'}
)
```

---

### Principle of Least Privilege

**Rule**: Request minimal permissions needed for operation.

**Read operations**:
```
✅ Files.Read (SharePoint)
❌ Files.ReadWrite
❌ Files.ReadWrite.All
```

**Suggest operations** (comments only):
```
✅ Files.ReadWrite (single file)
❌ Files.ReadWrite.All (all files)
```

---

## Audit Logging

### SIEM-Ready Structured Logging

**Format**: Newline-delimited JSON (JSONL)

**Implementation**:
```python
import logging
import json
from datetime import datetime

class AuditLogger:
    """SIEM-ready audit logging."""

    def __init__(self, log_dir='logs/audit'):
        self.log_dir = Path(log_dir)
        self.log_dir.mkdir(parents=True, exist_ok=True)

    def log_event(
        self,
        event_type: str,
        account: str,
        operation: str,
        status: str,
        **kwargs
    ):
        """
        Log security event in JSONL format.

        Args:
            event_type: API_CALL, API_ERROR, SECURITY_*, etc.
            account: Account name (not email/PII)
            operation: Operation performed
            status: success, failure, error
            **kwargs: Additional context (sanitized)
        """
        log_entry = {
            'timestamp': datetime.utcnow().isoformat(),
            'event_type': event_type,
            'account': account,
            'operation': operation,
            'status': status,
            **self._sanitize_context(kwargs)
        }

        # Write to daily log file
        log_file = self.log_dir / f"{operation}-{datetime.now().date()}.jsonl"

        with open(log_file, 'a') as f:
            f.write(json.dumps(log_entry) + '\n')

    def _sanitize_context(self, context: dict) -> dict:
        """Remove sensitive data from log context."""
        sensitive_keys = {'token', 'password', 'secret', 'api_key', 'access_token'}

        sanitized = {}
        for key, value in context.items():
            if any(s in key.lower() for s in sensitive_keys):
                sanitized[key] = '***REDACTED***'
            else:
                sanitized[key] = value

        return sanitized
```

**What to log**:
- ✅ Authentication attempts (success/failure)
- ✅ Authorization failures (permission denied)
- ✅ Resource access (read/write/delete)
- ✅ Security violations (excess permissions, tenant mismatch)
- ✅ Rate limit hits
- ✅ Error conditions

**What NOT to log**:
- ❌ Tokens (even partial)
- ❌ Passwords (even hashed)
- ❌ PII (emails, names, addresses)
- ❌ Full API responses (may contain sensitive data)

---

## Multi-Account Isolation

### Tenant ID Validation

**Rule**: Validate token tenant matches account configuration.

**Why**: Prevents cross-account data exfiltration.

**Implementation**:
```python
from dataclasses import dataclass

@dataclass(frozen=True)
class AccountContext:
    """Immutable account context."""
    account_name: str
    display_name: str
    tenant_id: str | None
    platform: str

def validate_tenant_id(token: str, context: AccountContext):
    """
    Validate token tenant ID matches account configuration.

    Raises:
        CrossAccountError: If tenant mismatch detected
    """
    # Extract tenant ID from token
    decoded = jwt.decode(token, options={"verify_signature": False})
    token_tenant = decoded.get('tid')  # Microsoft tokens

    if context.tenant_id and token_tenant != context.tenant_id:
        audit_logger.log_security_event('SECURITY_CROSS_ACCOUNT', {
            'account': context.account_name,
            'token_tenant': token_tenant,
            'expected_tenant': context.tenant_id
        })

        raise CrossAccountError(
            f"Tenant ID mismatch detected.\n"
            f"Token tenant: {token_tenant}\n"
            f"Expected: {context.tenant_id}\n"
            f"This indicates a cross-account operation attempt."
        )
```

**Immutable context** (prevents state mutation):
```python
# ✅ CORRECT - frozen dataclass
context = AccountContext(
    account_name='professional',
    display_name='Work Account',
    tenant_id='tenant-id-123',
    platform='sharepoint'
)

# This raises FrozenInstanceError
context.tenant_id = 'malicious-tenant'  # ❌ Cannot mutate
```

---

## Related Context

- [[security/practices]] - Security overview
- [[security/auth-and-credentials]] - Authentication and tokens
- [[security/errors-and-limits]] - Error handling
- [[python/conventions]] - Python coding standards

---

*Last updated: 2026-02-06*
