# EDS-005 – Writing Guidelines

**Document ID:** EDS-005
**Version:** 1.0
**Status:** Approved
**Owner:** Enterprise Runbooks Project
**Last Updated:** 2026-08-06

---

# 1. Purpose

The Writing Guidelines define the editorial principles for all documentation within the Enterprise Runbooks repository.

The objective is to ensure that documentation is clear, consistent, easy to understand, and suitable for operational use.

---

# 2. Scope

These guidelines apply to all documentation contained in this repository, including:

* Framework documents (EDF)
* Documentation standards (EDS)
* Templates (TMP)
* Runbooks (RB)
* Supporting documentation

---

# 3. General Principles

Documentation should be:

* Clear
* Concise
* Accurate
* Consistent
* Action-oriented
* Easy to maintain

Avoid unnecessary complexity and ambiguous wording.

---

# 4. Language

All documentation shall be written in English.

Use internationally recognized technical terminology.

Avoid regional expressions, slang, or informal language.

---

# 5. Writing Style

Use a professional and neutral tone.

Preferred:

> Restart the service.

Avoid:

> You should restart the service.

Use direct instructions whenever operational actions are required.

---

# 6. Step-by-Step Procedures

Operational procedures should consist of sequential, numbered steps.

Each step should describe exactly one action.

Preferred:

1. Verify the cluster status.
2. Drain the node.
3. Install the updates.
4. Reboot the server.

Avoid combining multiple actions into a single step.

---

# 7. Expected Results

Critical operational steps should include the expected outcome.

Example:

**Expected Result**

The cluster reports **HEALTH_OK**.

This enables operators to verify successful execution.

---

# 8. Warnings and Notes

Important information should be clearly identified.

Use the following conventions.

> **Note**
>
> Provides additional information or recommendations.

> **Warning**
>
> Highlights potential operational risks or service impacts.

> **Important**
>
> Identifies mandatory actions or critical requirements.

---

# 9. Technical Content

Commands shall be presented in fenced code blocks.

Example:

````markdown
```bash
ceph -s
```
````

Configuration files should include the appropriate language identifier whenever possible.

Examples:

* `yaml`
* `json`
* `bash`
* `powershell`
* `ini`

---

# 10. Lists and Tables

Use:

* Bullet lists for unordered information.
* Numbered lists for procedures.
* Tables for structured reference information.

Avoid long paragraphs where a list improves readability.

---

# 11. Terminology

Use consistent terminology throughout the repository.

Preferred terms:

* Runbook
* Node
* Cluster
* Service
* Storage
* Validation
* Rollback

Avoid using multiple terms for the same concept.

---

# 12. Abbreviations

Define uncommon abbreviations on first use.

Example:

> Enterprise Documentation Standard (EDS)

After the initial definition, the abbreviation may be used throughout the document.

---

# 13. Examples

Examples should:

* Support understanding.
* Be technically correct.
* Remain vendor-neutral whenever possible.
* Avoid production-specific values.

Use placeholders instead of confidential information.

Example:

```text
<HOSTNAME>
<IP_ADDRESS>
<CLUSTER_NAME>
```

---

# 14. Document Consistency

All documents should:

* Follow the applicable documentation standards.
* Use consistent section headings.
* Apply consistent formatting.
* Maintain a logical flow from purpose to execution.

---

# 15. Accessibility

Documentation should be easy to read.

Recommendations:

* Keep paragraphs short.
* Use descriptive headings.
* Prefer tables over dense text where appropriate.
* Avoid excessive formatting.

The primary goal is readability.

---

# 16. Related Standards

This standard should be used together with:

* EDF-000 – Enterprise Documentation Framework
* EDS-001 – Enterprise Runbook Standard
* EDS-004 – Naming Convention Standard
