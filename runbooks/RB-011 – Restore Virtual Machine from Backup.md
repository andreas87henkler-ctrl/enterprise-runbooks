# RB-011 – Restore Virtual Machine from Backup

**Runbook ID:** RB-011
**Version:** 1.0
**Status:** Approved
**Category:** Backup & Recovery
**Service:** Virtual Machine Backup and Restore
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                                  |
| ------------------ | -------------------------------------- |
| Estimated Duration | 30–120 minutes                         |
| Service Impact     | Medium                                 |
| Downtime Required  | Yes (for the restored virtual machine) |
| Change Required    | Yes                                    |
| Skill Level        | Intermediate                           |

---

# 1. Purpose

This runbook describes the standardized procedure for restoring a virtual machine from a backup.

The objective is to recover a virtual machine in a controlled and verifiable manner while minimizing service disruption.

---

# 2. Scope

This runbook applies to:

* Accidental virtual machine deletion
* Virtual machine corruption
* Planned recovery testing
* Disaster recovery scenarios
* Operational recovery requests

This runbook does not cover storage-level recovery or host recovery procedures.

---

# 3. Prerequisites

Before starting:

* Approved recovery request or incident
* Administrative access to the virtualization platform
* Access to the backup repository
* Target restore location identified
* Backup availability verified
* Sufficient storage capacity available

---

# 4. Roles and Responsibilities

| Role                 | Responsibility                      |
| -------------------- | ----------------------------------- |
| System Administrator | Perform the restore procedure       |
| Platform Engineer    | Support complex recovery activities |
| Service Owner        | Approve production recovery         |

---

# 5. Risks

| Risk                      | Impact                            | Mitigation                                            |
| ------------------------- | --------------------------------- | ----------------------------------------------------- |
| Incorrect backup selected | Outdated system state             | Verify backup date and restore point                  |
| Insufficient storage      | Restore failure                   | Confirm available storage before starting             |
| Configuration mismatch    | Application issues after recovery | Validate restored configuration before production use |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify the Restore Request

Confirm the reason for the restore and identify the required recovery point.

---

### Step 2 – Verify Backup Availability

Confirm that the required backup is available and suitable for restoration.

---

### Step 3 – Verify Target Environment

Confirm that sufficient compute, network, and storage resources are available for the restored virtual machine.

---

## Phase 2 – Restore

### Step 4 – Start the Restore Procedure

Restore the selected virtual machine from the chosen backup.

Follow the organization's approved restore procedure.

---

### Step 5 – Monitor Restore Progress

Monitor the restore operation until completion.

Verify that no unexpected errors occur during the process.

---

## Phase 3 – Post-Restore Validation

### Step 6 – Verify Virtual Machine

Confirm that the restored virtual machine is available.

---

### Step 7 – Verify Operating System

Confirm that the operating system starts successfully.

---

### Step 8 – Verify Application Services

Confirm that required services and applications operate as expected.

---

### Step 9 – Verify Network Connectivity

Confirm that network communication is functioning correctly.

---

# 7. Validation

The restore is considered successful when:

* The virtual machine has been restored successfully.
* The operating system starts normally.
* Required applications are operational.
* Network connectivity has been verified.
* The restored workload is available to users where applicable.

---

# 8. Rollback

If the restore cannot be completed successfully:

* Stop the recovery procedure.
* Preserve the current environment.
* Investigate the restore failure before attempting another recovery.

---

# 9. Escalation

| Condition                      | Action                            |
| ------------------------------ | --------------------------------- |
| Backup unavailable             | Escalate to Backup Operations     |
| Restore process fails          | Investigate backup integrity      |
| Virtual machine does not start | Initiate incident management      |
| Application validation fails   | Escalate to the application owner |

---

# 10. Documentation

Record:

* Restore date and time
* Virtual machine restored
* Backup restore point
* Validation results
* Observed issues
* Related incident or change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* Organization Backup Policy
* Organization Disaster Recovery Plan
