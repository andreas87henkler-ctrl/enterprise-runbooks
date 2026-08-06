# TMP-003 – Enterprise Troubleshooting Guide Template

**Template ID:** TMP-003
**Document Type:** Troubleshooting Guide
**Version:** 1.0
**Status:** Approved
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Troubleshooting Guide Information

| Field                    | Value                         |
| ------------------------ | ----------------------------- |
| Troubleshooting ID       | TS-XXX                        |
| Title                    | Example Troubleshooting Guide |
| Platform                 | Example Platform              |
| Related Runbook          | RB-XXX                        |
| Related Work Instruction | WI-XXX                        |
| Skill Level              | Intermediate / Advanced       |

---

# 1. Purpose

This Troubleshooting Guide provides a structured approach for diagnosing, isolating, and resolving operational issues related to the associated service or platform.

It complements the related Runbook and Work Instruction by focusing on fault analysis and recovery.

---

# 2. Scope

This guide applies to operational incidents affecting the specified platform or service.

It covers common failure scenarios, diagnostic procedures, possible causes, and recommended recovery actions.

---

# 3. Symptoms

Typical indicators include:

* Service unavailable
* Unexpected error messages
* Performance degradation
* Failed health checks
* Monitoring alerts
* Timeout or connection failures
* Configuration inconsistencies

---

# 4. Prerequisites

Before troubleshooting:

* Verify administrative access.
* Confirm the affected system or service.
* Review monitoring and alerting information.
* Ensure relevant logs are available.
* Confirm the current maintenance status.

---

# 5. Diagnostic Procedure

## Step 1 – Verify the Issue

### Objective

Confirm that the reported issue is reproducible.

### Actions

* Review monitoring alerts.
* Verify service status.
* Identify affected systems.
* Determine the scope of the incident.

### Expected Result

The issue has been confirmed and its impact is understood.

---

## Step 2 – Collect Diagnostic Information

### Actions

Collect relevant information, such as:

* System logs
* Application logs
* Event logs
* Monitoring data
* Configuration status
* Recent changes
* Related incidents

### Expected Result

Sufficient diagnostic data is available for analysis.

---

## Step 3 – Identify the Root Cause

### Actions

Analyze the collected information.

Determine whether the issue is related to:

* Hardware
* Network
* Storage
* Configuration
* Software
* External dependencies

### Expected Result

The most probable root cause has been identified.

---

## Step 4 – Perform Recovery

Execute the appropriate recovery procedure.

If available, refer to the corresponding Work Instruction.

---

## Step 5 – Validate Recovery

Verify:

* Service availability
* Monitoring status
* Application functionality
* User connectivity
* System stability

---

# 6. Common Issues

| Symptom                 | Possible Cause                  | Recommended Action                               |
| ----------------------- | ------------------------------- | ------------------------------------------------ |
| Service unavailable     | Service stopped                 | Verify service status and restart if appropriate |
| Authentication failure  | Certificate or credential issue | Validate certificates and credentials            |
| Performance degradation | Resource exhaustion             | Review resource utilization                      |
| Connectivity failure    | Network issue                   | Verify network connectivity and dependencies     |

---

# 7. Escalation

Escalate when:

* Root cause cannot be identified.
* Recovery attempts are unsuccessful.
* Business-critical services remain unavailable.
* Multiple systems are affected.
* Vendor support is required.

Record all findings before escalation.

---

# 8. Documentation

Record:

* Date and time
* Affected system
* Symptoms
* Root cause
* Recovery actions
* Validation results
* Related Incident
* Related Change (if applicable)
* Lessons learned

---

# 9. References

* Related Runbook
* Related Work Instruction
* Vendor Documentation
* Internal Standards
* Knowledge Base Articles

---

# Template Notes

This template shall be used for all Troubleshooting Guides within the Enterprise Runbook Framework.

A Troubleshooting Guide describes **how to diagnose and resolve operational issues**.

It complements the related Runbook, which defines **what operational process shall be performed**, and the related Work Instruction, which defines **how the process is technically implemented**.

Troubleshooting Guides should remain vendor-neutral whenever possible. Platform-specific diagnostics, log examples, command outputs, and recovery procedures may be documented in associated Work Instructions or platform-specific troubleshooting guides.
