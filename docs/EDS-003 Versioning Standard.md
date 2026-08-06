# EDS-003 – Versioning Standard

**Document ID:** EDS-003
**Version:** 1.0
**Status:** Approved
**Owner:** Enterprise Runbooks Project
**Last Updated:** 2026-08-06

---

# 1. Purpose

The Versioning Standard defines how document versions are assigned and maintained within the Enterprise Runbooks repository.

A standardized versioning approach ensures consistency, traceability, and transparency throughout the documentation lifecycle.

---

# 2. Scope

This standard applies to all documentation within the repository, including:

* Framework documents (EDF)
* Documentation standards (EDS)
* Templates (TMP)
* Runbooks (RB)
* Supporting documentation

---

# 3. Version Format

All documents shall follow the version format:

```text
MAJOR.MINOR
```

Examples:

```text
1.0
1.1
1.2
2.0
```

Patch versions (e.g. **1.0.1**) are intentionally not used to keep document versioning simple and easy to understand.

---

# 4. Version Definitions

## Major Version

A new major version shall be assigned when significant changes affect the structure, purpose, or operational content of a document.

Examples:

* Major restructuring
* Significant process changes
* New mandatory sections
* Breaking changes to document structure

Example:

```text
1.0 → 2.0
```

---

## Minor Version

A new minor version shall be assigned for improvements that do not fundamentally change the document.

Examples:

* Clarifications
* Additional examples
* Updated screenshots
* Improved wording
* Editorial improvements
* Additional references

Example:

```text
1.1 → 1.2
```

---

# 5. Initial Version

Every newly approved document shall begin with version:

```text
1.0
```

Draft versions may internally use:

```text
0.1
0.2
0.3
```

Once approved, the version becomes **1.0**.

---

# 6. Change History

Every document shall include a change history.

Example:

| Version | Date       | Author          | Description                |
| ------- | ---------- | --------------- | -------------------------- |
| 1.0     | 2026-08-06 | Andreas Henkler | Initial release            |
| 1.1     | 2026-09-12 | Andreas Henkler | Updated validation section |
| 2.0     | 2027-01-15 | Andreas Henkler | Major restructuring        |

The change history should summarize meaningful changes rather than every editorial correction.

---

# 7. Versioning Principles

The following principles apply:

* Version numbers shall increase sequentially.
* Every approved release shall receive a new version number.
* Version numbers shall never be reused.
* Historical versions should remain traceable through Git history.
* Version numbers should reflect the significance of changes.

---

# 8. Git Integration

Git serves as the authoritative version control system for this repository.

Document versions provide human-readable release information, while Git maintains the complete revision history.

Git commit messages should clearly describe the purpose of each change.

Examples:

* Add initial runbook template
* Update rollback procedure
* Improve validation guidance
* Restructure metadata section

---

# 9. Release Recommendations

The following release strategy is recommended.

| Change Type               | Version |
| ------------------------- | ------- |
| Initial approval          | 1.0     |
| Documentation improvement | Minor   |
| New operational guidance  | Minor   |
| Structural redesign       | Major   |
| Complete rewrite          | Major   |

---

# 10. Related Standards

This standard should be used together with:

* EDF-000 – Enterprise Documentation Framework
* EDS-001 – Enterprise Runbook Standard
* EDS-002 – Document Lifecycle Standard
