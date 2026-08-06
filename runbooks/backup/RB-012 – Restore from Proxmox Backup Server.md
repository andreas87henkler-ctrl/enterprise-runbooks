# RB-012 – Restore from Proxmox Backup Server

**Runbook ID:** RB-012
**Version:** 1.0
**Status:** Approved
**Category:** Backup & Recovery
**Service:** Proxmox Backup Server (PBS)
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                            |
| ------------------ | -------------------------------- |
| Estimated Duration | 30–180 minutes                   |
| Service Impact     | Medium                           |
| Downtime Required  | Depends on the recovery scenario |
| Change Required    | Yes                              |
| Skill Level        | Intermediate                     |

---

# 1. Purpose

This runbook describes the standardized procedure for restoring protected workloads from Proxmox Backup Server (PBS).

The objective is to perform recovery operations in a controlled, repeatable, and verifiable manner while maintaining data integrity.

---

# 2. Scope

This runbook applies to recovery operations performed using Proxmox Backup Server, including:

* Virtual machine recovery
* Linux container recovery
* File-level recovery (where supported)
* Recovery testing
* Disaster recovery scenarios

Detailed recovery procedures are documented in the corresponding Work Instructions.

---

# 3. Prerequisites

Before starting:

* Approved recovery request or incident
* Administrative access to the virtualization platform
* Administrative access to Proxmox Backup Server
* Backup availability verified
* Target recovery destination identified
* Sufficient compute and storage resources available

---

# 4. Roles and Responsibilities

| Role                 | Responsibility                      |
| -------------------- | ----------------------------------- |
| System Administrator | Execute the recovery procedure      |
| Platform Engineer    | Support complex recovery activities |
| Service Owner        | Approve production recovery         |

---

# 5. Risks

| Risk                              | Impact                    | Mitigation                                     |
| --------------------------------- | ------------------------- | ---------------------------------------------- |
| Incorrect recovery point selected | Recovery of outdated data | Verify restore point before starting           |
| Restore interruption              | Recovery delay            | Monitor restore process                        |
| Resource limitations              | Recovery failure          | Verify available storage and compute resources |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Recovery Request

Confirm the recovery scope and identify the required restore point.

---

### Step 2 – Verify Backup Availability

Confirm that the required backup is available and accessible.

---

### Step 3 – Verify Recovery Target

Confirm that the destination environment is ready for recovery.

---

## Phase 2 – Recovery

### Step 4 – Initiate the Restore

Start the restore operation using the approved organizational procedure.

---

### Step 5 – Monitor Recovery

Monitor the restore process until completion.

Verify that no unexpected errors occur.

---

## Phase 3 – Validation

### Step 6 – Verify Restored Workload

Confirm that the restored workload is available.

---

### Step 7 – Validate Functionality

Verify that the operating system, applications, and services are functioning as expected.

---

### Step 8 – Confirm Recovery Completion

Confirm that the recovery objectives have been achieved.

---

# 7. Validation

The recovery is considered successful when:

* The selected workload has been restored successfully.
* Required services are operational.
* Data integrity has been confirmed.
* Recovery objectives have been met.

---

# 8. Rollback

If the recovery cannot be completed successfully:

* Suspend the recovery operation.
* Preserve the current environment.
* Investigate the recovery failure before attempting another restore.

---

# 9. Escalation

| Condition                     | Action                                    |
| ----------------------------- | ----------------------------------------- |
| Backup unavailable            | Escalate to Backup Operations             |
| Recovery process fails        | Investigate backup integrity              |
| Restored workload unavailable | Initiate incident management              |
| Validation unsuccessful       | Escalate to the responsible service owner |

---

# 10. Documentation

Record:

* Recovery date and time
* Restored workload
* Backup restore point
* Validation results
* Observed issues
* Related incident or change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-011 – Restore Virtual Machine from Backup
* Organization Backup Policy
* Organization Disaster Recovery Plan
