# RB-013 – Replace Kubernetes Worker Node

**Runbook ID:** RB-013
**Version:** 1.0
**Status:** Approved
**Category:** Kubernetes
**Service:** Kubernetes Cluster
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                                    |
| ------------------ | ---------------------------------------- |
| Estimated Duration | 45–90 minutes                            |
| Service Impact     | Low                                      |
| Downtime Required  | No (if workload redundancy is available) |
| Change Required    | Yes                                      |
| Skill Level        | Advanced                                 |

---

# 1. Purpose

This runbook describes the standardized procedure for replacing a Kubernetes worker node.

The objective is to safely replace a worker node while maintaining application availability and cluster stability.

---

# 2. Scope

This runbook applies to:

* Planned worker node replacement
* Hardware replacement
* Operating system replacement
* Infrastructure refresh
* Failed worker node recovery

It does not apply to replacing control plane nodes.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Kubernetes cluster
* Replacement worker node prepared
* Cluster health verified
* Sufficient cluster capacity available
* Workload redundancy confirmed where applicable

---

# 4. Roles and Responsibilities

| Role                     | Responsibility                    |
| ------------------------ | --------------------------------- |
| Platform Engineer        | Execute the replacement procedure |
| Kubernetes Administrator | Validate cluster functionality    |
| Service Owner            | Approve maintenance activities    |

---

# 5. Risks

| Risk                     | Impact                            | Mitigation                                        |
| ------------------------ | --------------------------------- | ------------------------------------------------- |
| Workload disruption      | Temporary service degradation     | Verify workload redundancy before maintenance     |
| Node replacement failure | Reduced cluster capacity          | Validate replacement node before deployment       |
| Scheduling issues        | Application availability affected | Confirm workload redistribution during validation |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the Kubernetes cluster is operating normally.

---

### Step 2 – Verify Target Node

Identify the worker node scheduled for replacement.

Confirm that the correct node has been selected.

---

## Phase 2 – Workload Migration

### Step 3 – Prepare the Worker Node

Prepare the worker node for maintenance according to organizational procedures.

---

### Step 4 – Relocate Workloads

Allow workloads to migrate to the remaining worker nodes.

Confirm that application availability is maintained.

---

## Phase 3 – Node Replacement

### Step 5 – Remove the Worker Node

Remove the worker node from cluster service.

---

### Step 6 – Deploy the Replacement Node

Deploy the replacement worker node.

Verify successful cluster registration.

---

## Phase 4 – Validation

### Step 7 – Verify Node Status

Confirm that the replacement node is available and ready to accept workloads.

---

### Step 8 – Verify Workload Distribution

Confirm that workloads are scheduled and operating normally.

---

### Step 9 – Verify Cluster Health

Confirm that the Kubernetes cluster has returned to a healthy operational state.

---

# 7. Validation

The replacement is considered successful when:

* The replacement worker node is operational.
* Workloads are running normally.
* Cluster health is normal.
* No scheduling issues are present.
* Application availability has been maintained.

---

# 8. Rollback

If the replacement cannot be completed successfully:

* Suspend further maintenance.
* Restore workload availability using existing cluster resources.
* Investigate the replacement failure before attempting another deployment.

---

# 9. Escalation

| Condition                    | Action                          |
| ---------------------------- | ------------------------------- |
| Replacement node unavailable | Escalate to Platform Operations |
| Workloads fail to schedule   | Investigate cluster scheduling  |
| Cluster health degrades      | Pause maintenance immediately   |

---

# 10. Documentation

Record:

* Maintenance date
* Replaced worker node
* Validation results
* Observed issues
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* Organization Kubernetes Operations Guide
