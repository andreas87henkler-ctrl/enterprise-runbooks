# EDS-002 – Document Lifecycle Standard

**Document ID:** EDS-002
**Version:** 1.0
**Status:** Approved
**Owner:** Enterprise Runbooks Project
**Last Updated:** 2026-08-06

---

# 1. Purpose

The Document Lifecycle Standard defines the lifecycle of documentation within the Enterprise Runbooks repository.

Its purpose is to ensure that all documents are created, reviewed, approved, maintained, and retired in a consistent and controlled manner.

A defined lifecycle improves documentation quality, traceability, and long-term maintainability.

---

# 2. Scope

This standard applies to all documentation contained within the repository, including:

* Framework documents (EDF)
* Documentation standards (EDS)
* Templates (TMP)
* Runbooks (RB)
* Supporting documentation

---

# 3. Document Lifecycle

Every document follows the same lifecycle.

```text
Draft
   │
   ▼
Review
   │
   ▼
Approved
   │
   ▼
Deprecated
   │
   ▼
Retired
```

Each document shall exist in exactly one lifecycle state.

---

# 4. Lifecycle States

## Draft

The document is under development.

Characteristics:

* Initial creation
* Content may change significantly
* Not approved for operational use

---

## Review

The document is considered technically complete and is under review.

Typical review activities include:

* Technical validation
* Editorial review
* Consistency check
* Standards compliance

Operational use is not recommended during this stage.

---

## Approved

The document has successfully completed the review process.

Characteristics:

* Approved for operational use
* Considered the current authoritative version
* Subject to periodic review

Only documents in the **Approved** state should be used in production environments.

---

## Deprecated

The document remains available but has been superseded or is scheduled for replacement.

Characteristics:

* May still be referenced
* Replacement document should be identified
* New implementations should avoid using deprecated documents

---

## Retired

The document is no longer valid.

Characteristics:

* Preserved for historical reference
* Not maintained
* Shall not be used operationally

---

# 5. Lifecycle Transitions

The following transitions are supported.

| From       | To         |
| ---------- | ---------- |
| Draft      | Review     |
| Review     | Approved   |
| Approved   | Deprecated |
| Deprecated | Retired    |

Returning a document to a previous state should only occur under exceptional circumstances and should be documented.

---

# 6. Responsibilities

The document owner is responsible for managing the lifecycle of a document.

Typical responsibilities include:

* Maintaining document accuracy
* Coordinating reviews
* Scheduling periodic updates
* Initiating retirement when appropriate

---

# 7. Review Requirements

Approved documents should be reviewed regularly.

Recommended review intervals:

| Document Type           | Review Cycle                                            |
| ----------------------- | ------------------------------------------------------- |
| Framework Documents     | Every 12 months                                         |
| Documentation Standards | Every 12 months                                         |
| Templates               | Every 12 months                                         |
| Runbooks                | Every 6–12 months, depending on operational criticality |

A review should also be performed after:

* Major infrastructure changes
* Significant incidents
* Disaster recovery exercises
* Architectural redesigns

---

# 8. Retirement

A document should be retired when:

* It is no longer applicable.
* The related technology has been removed.
* It has been replaced by a newer document.
* The operational process no longer exists.

Retired documents should remain accessible for historical and audit purposes where appropriate.

---

# 9. Related Standards

This standard should be used together with:

* EDF-000 – Enterprise Documentation Framework
* EDS-001 – Enterprise Runbook Standard
* EDS-003 – Versioning Standard
