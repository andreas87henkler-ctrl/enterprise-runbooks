# RB-014 – Replace Kubernetes Control Plane Node

**Runbook ID:** RB-014
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
| Estimated Duration | 60–120 minutes                           |
| Service Impact     | Medium                                   |
| Downtime Required  | No (for highly available control planes) |
| Change Required    | Yes                                      |
| Skill Level        | Advanced                                 |

---

# 1. Purpose

This runbook describes the standardized procedure for replacing a Kubernetes control plane node.

The objective is to restore or replace a control plane node while maintaining cluster availability, control plane functionality, and operational stability.

---

# 2. Scope

This runbook applies to:

* Planned control plane node replacement
* Hardware replacement
* Operating system replacement
* Infrastructure refresh
* Failed control plane node recovery

This runbook assumes a highly available Kubernetes control plane with multiple control plane nodes.

Single-node clusters require a separate maintenance and recovery procedure.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Kubernetes cluster
* Replacement control plane node prepared
* Cluster health verified
* Control plane quorum confirmed
* Current cluster backup available according to organizational policy

---

# 4. Roles and Responsibilities

| Role                     | Responsibility                    |
| ------------------------ | --------------------------------- |
| Platform Engineer        | Execute the replacement procedure |
| Kubernetes Administrator | Validate cluster functionality    |
| Service Owner            | Approve maintenance activities    |

---

# 5. Risks

| Risk                         | Impact                         | Mitigation                                      |
| ---------------------------- | ------------------------------ | ----------------------------------------------- |
| Loss of control plane quorum | Cluster management unavailable | Verify quorum before maintenance                |
| Replacement failure          | Reduced cluster resilience     | Validate replacement node before deployment     |
| Control plane instability    | Management functions affected  | Monitor cluster status throughout the procedure |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the Kubernetes cluster is operating normally.

---

### Step 2 – Verify Control Plane Status

Confirm that the control plane is healthy and identify the node scheduled for replacement.

Verify that sufficient control plane capacity remains during maintenance.

---

## Phase 2 – Replacement

### Step 3 – Prepare the Control Plane Node

Prepare the selected node for replacement according to the approved maintenance procedure.

---

### Step 4 – Remove the Control Plane Node

Remove the control plane node from the cluster following organizational procedures.

---

### Step 5 – Deploy the Replacement Control Plane Node

Deploy the replacement node and verify that it successfully joins the control plane.

---

## Phase 3 – Validation

### Step 6 – Verify Control Plane Health

Confirm that all required control plane services are operational.

---

### Step 7 – Verify Cluster Functionality

Confirm that the cluster is capable of scheduling workloads and responding to administrative requests.

---

### Step 8 – Verify Node Status

Confirm that all control plane nodes report a healthy operational state.

---

# 7. Validation

The replacement is considered successful when:

* The replacement control plane node is operational.
* Control plane quorum is maintained.
* Cluster management functions are available.
* Workloads continue to operate normally.
* Cluster health is normal.

---

# 8. Rollback

If the replacement cannot be completed successfully:

* Suspend further maintenance activities.
* Restore control plane availability where possible.
* Investigate the failure before attempting another replacement.

---

# 9. Escalation

| Condition                      | Action                                      |
| ------------------------------ | ------------------------------------------- |
| Control plane quorum lost      | Escalate immediately to Platform Operations |
| Cluster management unavailable | Initiate incident management                |
| Replacement node unavailable   | Investigate deployment and recovery options |

---

# 10. Documentation

Record:

* Maintenance date
* Replaced control plane node
* Validation results
* Observed issues
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-013 – Replace Kubernetes Worker Node
* Organization Kubernetes Operations Guide
