# RB-008 – Replace Ceph Manager

**Runbook ID:** RB-008
**Version:** 1.0
**Status:** Approved
**Category:** Storage
**Service:** Ceph Storage Cluster
**Owner:** Storage Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value         |
| ------------------ | ------------- |
| Estimated Duration | 30–60 minutes |
| Service Impact     | Low           |
| Downtime Required  | No            |
| Change Required    | Yes           |
| Skill Level        | Advanced      |

---

# 1. Purpose

This runbook describes the standardized procedure for replacing a Ceph Manager (MGR).

The objective is to restore or replace a manager daemon while maintaining normal cluster operations and management functionality.

---

# 2. Scope

This runbook applies to:

* Planned manager replacement
* Failed manager replacement
* Migration of manager services
* Hardware replacement affecting manager services

This runbook assumes that the Ceph cluster remains operational throughout the maintenance activity.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Ceph cluster
* Cluster health verified
* Replacement host prepared (if applicable)
* Manager service status verified

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                     |
| --------------------- | ---------------------------------- |
| Storage Administrator | Execute the manager replacement    |
| Platform Engineer     | Support infrastructure maintenance |
| Service Owner         | Approve maintenance activities     |

---

# 5. Risks

| Risk                            | Impact                                 | Mitigation                                           |
| ------------------------------- | -------------------------------------- | ---------------------------------------------------- |
| Management service interruption | Temporary loss of management functions | Verify standby manager availability where applicable |
| Deployment failure              | Delayed maintenance                    | Validate replacement environment before deployment   |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the storage cluster is operating normally.

---

### Step 2 – Verify Manager Status

Confirm the active manager instance and identify the manager scheduled for replacement.

---

## Phase 2 – Replacement

### Step 3 – Remove the Target Manager

Remove the manager according to the approved maintenance procedure.

---

### Step 4 – Deploy the Replacement Manager

Deploy the replacement manager and confirm that it successfully joins the cluster.

---

## Phase 3 – Validation

### Step 5 – Verify Manager Services

Confirm that manager services are available and operating normally.

---

### Step 6 – Verify Cluster Health

Confirm that the storage cluster has returned to a healthy operational state.

---

# 7. Validation

The replacement is considered successful when:

* The replacement manager is operational.
* Management services are available.
* Cluster health is normal.
* No manager-related warnings are present.

---

# 8. Rollback

If the replacement cannot be completed successfully:

* Suspend further maintenance activities.
* Restore manager availability where possible.
* Follow vendor-specific recovery procedures if required.

---

# 9. Escalation

| Condition                    | Action                                      |
| ---------------------------- | ------------------------------------------- |
| Manager service unavailable  | Escalate to Storage Operations              |
| Cluster health degrades      | Pause maintenance immediately               |
| Replacement deployment fails | Investigate deployment and recovery options |

---

# 10. Documentation

Record:

* Maintenance date
* Replaced manager instance
* Validation results
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-010 – Ceph Health Validation
