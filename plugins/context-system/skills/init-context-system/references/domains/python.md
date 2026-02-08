
**Create `context/python/_index.md`**:
```markdown
---
title: Python Standards
type: index
created: [YYYY-MM-DD]
---

# Python Domain

Python coding conventions and best practices.

## When to Use

Load this domain when:
- Writing Python code
- Developing Python-based Claude Code skills
- Reviewing Python code

## Files

- coding-conventions.md - PEP 8 compliance, style guide

## External Authorities

Grounded in:
- PEP 8: https://peps.python.org/pep-0008/
- PEP 484 (Type Hints): https://peps.python.org/pep-0484/

See [Standards & Sources](https://github.com/bcbeidel/context-system/blob/main/docs/standards-sources.md#5-python-conventions) for complete mapping.

---

*Created: [YYYY-MM-DD]*
```

**Create `context/python/coding-conventions.md`**:
```markdown
---
title: Python Coding Conventions
created: [YYYY-MM-DD]
keywords: [python, pep8, style, conventions]
applies-to: [python-development, code-review]
tags: [context, python]
---

# Python Coding Conventions

## Summary

Python code follows PEP 8 style guide with type hints (PEP 484).

## Standards Source

**Authority**: [PEP 8](https://peps.python.org/pep-0008/)

## Key Conventions

### Code Layout
- 4 spaces per indentation level (no tabs)
- Maximum line length: 79 characters (code), 72 (docstrings)
- 2 blank lines between top-level functions/classes
- 1 blank line between methods

### Naming
- `snake_case` for functions and variables
- `PascalCase` for classes
- `UPPER_CASE` for constants
- Private: prefix with `_` (single underscore)

### Imports
```python
# Standard library
import os
import sys

# Third-party
import requests
import numpy as np

# Local
from myproject import module
```

### Type Hints (PEP 484)
```python
def greeting(name: str) -> str:
    return f"Hello, {name}"
```

## Related Context

- [[context/python/_index]]
- [[context/security/best-practices]] (if security domain exists)
