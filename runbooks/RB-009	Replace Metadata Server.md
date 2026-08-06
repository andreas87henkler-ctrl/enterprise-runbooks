# RB-009 – Replace Ceph Metadata Server

**Runbook ID:** RB-009
**Version:** 1.0
**Status:** Approved
**Category:** Storage
**Service:** CephFS Metadata Server (MDS)
**Owner:** Storage Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                              |
| ------------------ | ---------------------------------- |
| Estimated Duration | 30–60 minutes                      |
| Service Impact     | Low to Medium                      |
| Downtime Required  | No (if redundant MDS is available) |
| Change Required    | Yes                                |
| Skill Level        | Advanced                           |

---

# 1. Purpose

This runbook describes the standardized procedure for replacing a Ceph Metadata Server (MDS).

The objective is to restore or replace an MDS while maintaining the availability and integrity of the CephFS service.

---

# 2. Scope

This runbook applies to environments using **CephFS**.

Typical use cases include:

* Planned MDS replacement
* Failed MDS replacement
* Hardware replacement affecting MDS services
* Migration of MDS services

This runbook does not apply to clusters that exclusively use RADOS Block Device (RBD) or Object Gateway (RGW).

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Ceph cluster
* Cluster health verified
* Replacement host prepared (if applicable)
* CephFS operational status verified

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                     |
| --------------------- | ---------------------------------- |
| Storage Administrator | Execute the replacement procedure  |
| Platform Engineer     | Support infrastructure maintenance |
| Service Owner         | Approve maintenance activities     |

---

# 5. Risks

| Risk                          | Impact                               | Mitigation                                         |
| ----------------------------- | ------------------------------------ | -------------------------------------------------- |
| Metadata service interruption | Temporary loss of file system access | Verify standby MDS availability where applicable   |
| Deployment failure            | Delayed maintenance                  | Validate replacement environment before deployment |
| Client reconnect delays       | Temporary access interruption        | Monitor client recovery during validation          |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the Ceph cluster is operating normally.

---

### Step 2 – Verify CephFS Status

Confirm that the file system is healthy and identify the Metadata Server scheduled for replacement.

---

## Phase 2 – Replacement

### Step 3 – Remove the Target Metadata Server

Remove the Metadata Server according to the approved maintenance procedure.

---

### Step 4 – Deploy the Replacement Metadata Server

Deploy the replacement Metadata Server and verify that it successfully joins the CephFS environment.

---

## Phase 3 – Validation

### Step 5 – Verify Metadata Services

Confirm that metadata services are available and operating normally.

---

### Step 6 – Verify Client Access

Confirm that clients can access the file system without unexpected errors.

---

### Step 7 – Verify Cluster Health

Confirm that the storage cluster has returned to a healthy operational state.

---

# 7. Validation

The replacement is considered successful when:

* The replacement Metadata Server is operational.
* CephFS is available.
* Client access is functioning normally.
* Cluster health is normal.
* No metadata-related warnings are present.

---

# 8. Rollback

If the replacement cannot be completed successfully:

* Suspend further maintenance activities.
* Restore metadata service availability where possible.
* Follow vendor-specific recovery procedures if required.

---

# 9. Escalation

| Condition                    | Action                            |
| ---------------------------- | --------------------------------- |
| Metadata service unavailable | Escalate to Storage Operations    |
| Client access interrupted    | Pause maintenance and investigate |
| Cluster health degrades      | Suspend maintenance immediately   |

---

# 10. Documentation

Record:

* Maintenance date
* Replaced Metadata Server
* Validation results
* Observed issues
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-010 – Ceph Health Validation
