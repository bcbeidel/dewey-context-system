## Domain Discovery Algorithm

**How to discover user's domains dynamically**:

```python
def discover_domains():
    """Discover user's domains from context/_index.md"""

    # Read main index
    index_content = read_file("context/_index.md")

    # Extract domain references
    # Look for: - **[[context/domain/_index|Domain]]**
    domains = extract_domain_links(index_content)

    # For each domain, read _index.md to understand:
    for domain in domains:
        domain_index = read_file(f"context/{domain}/_index.md")

        # Extract:
        # - Domain purpose (from "When to Use" section)
        # - Existing files (from "Files" section)
        # - External authorities (from "External Authorities" section)

        store_domain_metadata(domain, metadata)

    return domains_with_metadata
```

**Why this works**:
- No hardcoded domain names
- Works with ANY structure from init-context-system
- Adapts to user's actual work domains

---

