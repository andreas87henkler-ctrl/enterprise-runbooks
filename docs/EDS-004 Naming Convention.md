# EDS-004 – Naming Convention Standard

**Document ID:** EDS-004
**Version:** 1.0
**Status:** Approved
**Owner:** Enterprise Runbooks Project
**Last Updated:** 2026-08-06

---

# 1. Purpose

The Naming Convention Standard defines consistent naming rules for all documentation, templates, runbooks, directories, scripts, diagrams, and supporting resources within the Enterprise Runbooks repository.

Consistent naming improves readability, discoverability, navigation, and long-term maintainability.

---

# 2. Scope

This standard applies to all repository content, including:

* Documentation
* Standards
* Templates
* Runbooks
* Scripts
* Images
* Diagrams
* Supporting resources

---

# 3. General Naming Principles

The following principles apply throughout the repository.

* Names shall be descriptive.
* Names shall remain stable over time.
* Abbreviations should be avoided unless commonly accepted.
* Use English for all names.
* Avoid spaces in filenames.
* Separate words using hyphens (`-`).
* Use lowercase names for directories.
* Use uppercase prefixes for document identifiers.

---

# 4. Document Naming

All controlled documents shall follow the format:

```text
<ID>-<Short-Description>.md
```

Examples:

```text
EDF-000-Enterprise-Documentation-Framework.md
EDS-001-Enterprise-Runbook-Standard.md
EDS-003-Versioning-Standard.md
RB-001-Proxmox-Cluster-Health-Check.md
TMP-001-Runbook-Template.md
```

Document version numbers shall **not** be included in filenames.

---

# 5. Document Prefixes

The following prefixes are reserved.

| Prefix | Description                               |
| ------ | ----------------------------------------- |
| EDF    | Enterprise Documentation Framework        |
| EDS    | Enterprise Documentation Standard         |
| TMP    | Documentation Template                    |
| RB     | Runbook                                   |
| SOP    | Standard Operating Procedure *(optional)* |
| WI     | Work Instruction *(optional)*             |

Additional prefixes may be introduced if new document types are added.

---

# 6. Directory Naming

Directories shall:

* use lowercase letters;
* avoid spaces;
* use hyphens only where necessary.

Examples:

```text
docs/
framework/
standards/
templates/
runbooks/
scripts/
diagrams/
images/
examples/
```

Technology-specific folders should also use lowercase names.

Examples:

```text
infrastructure/
storage/
virtualization/
network/
security/
backup/
kubernetes/
```

---

# 7. Script Naming

Scripts should use descriptive lowercase names.

Examples:

```text
cluster-health-check.sh
backup-validation.sh
ceph-osd-status.sh
```

Script names should describe the performed task.

---

# 8. Diagram Naming

Architecture diagrams should follow a consistent naming format.

Examples:

```text
cluster-architecture.drawio
network-topology.drawio
storage-layout.drawio
backup-workflow.drawio
```

Exported images should use the same base name.

Examples:

```text
cluster-architecture.png
network-topology.svg
```

---

# 9. Image Naming

Images should have meaningful names.

Preferred:

```text
ceph-dashboard-overview.png
proxmox-cluster-status.png
```

Avoid:

```text
image1.png
screenshot-final-v3.png
new-image.png
```

---

# 10. Identifier Stability

Document identifiers are permanent.

Examples:

```text
EDS-001
RB-004
TMP-001
```

Identifiers shall never be reused, even if a document is retired.

---

# 11. Reserved Characters

Avoid the following characters in filenames:

```text
\ / : * ? " < > |
```

Use only characters that are supported across common operating systems and version control systems.

---

# 12. Related Standards

This standard should be used together with:

* EDF-000 – Enterprise Documentation Framework
* EDS-001 – Enterprise Runbook Standard
* EDS-003 – Versioning Standard
