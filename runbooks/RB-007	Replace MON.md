# RB-007 – Replace Ceph Monitor

**Runbook ID:** RB-007
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

This runbook describes the standardized procedure for replacing a Ceph Monitor (MON).

The objective is to restore or replace a monitor while maintaining cluster quorum and operational stability.

---

# 2. Scope

This runbook applies to:

* Planned monitor replacement
* Failed monitor replacement
* Hardware replacement affecting monitor services

It assumes that sufficient monitor quorum is maintained throughout the procedure.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Ceph cluster
* Cluster health verified
* Replacement host prepared (if applicable)
* Monitor quorum confirmed

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                  |
| --------------------- | ------------------------------- |
| Storage Administrator | Execute the monitor replacement |
| Platform Engineer     | Support infrastructure changes  |
| Service Owner         | Approve maintenance             |

---

# 5. Risks

| Risk                        | Impact                         | Mitigation                                 |
| --------------------------- | ------------------------------ | ------------------------------------------ |
| Loss of monitor quorum      | Cluster management unavailable | Verify quorum before maintenance           |
| Incorrect monitor selection | Service disruption             | Validate target monitor before replacement |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the storage cluster is operating normally.

---

### Step 2 – Verify Monitor Quorum

Confirm that sufficient monitor quorum exists before removing a monitor.

---

## Phase 2 – Replacement

### Step 3 – Remove the Target Monitor

Remove the monitor according to the approved maintenance procedure.

---

### Step 4 – Deploy the Replacement Monitor

Deploy the replacement monitor.

Confirm successful cluster integration.

---

## Phase 3 – Validation

### Step 5 – Verify Monitor Quorum

Confirm that monitor quorum has been restored.

---

### Step 6 – Verify Cluster Health

Verify that the cluster has returned to normal operation.

---

# 7. Validation

The replacement is successful when:

* Monitor quorum is healthy.
* The replacement monitor is operational.
* Cluster health is normal.
* No monitor-related warnings are present.

---

# 8. Rollback

If replacement cannot be completed:

* Suspend additional maintenance activities.
* Restore monitor availability where possible.
* Follow vendor recovery guidance if required.

---

# 9. Escalation

| Condition                       | Action                 |
| ------------------------------- | ---------------------- |
| Monitor quorum lost             | Escalate immediately   |
| Replacement monitor unavailable | Investigate deployment |
| Cluster health degrades         | Pause maintenance      |

---

# 10. Documentation

Record:

* Maintenance date
* Replaced monitor
* Validation results
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-010 – Ceph Health Validation
