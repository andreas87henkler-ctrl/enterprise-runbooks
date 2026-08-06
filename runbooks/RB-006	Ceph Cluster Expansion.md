# RB-006 – Ceph Cluster Expansion

**Runbook ID:** RB-006
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

| Field              | Value     |
| ------------------ | --------- |
| Estimated Duration | 2–6 hours |
| Service Impact     | Low       |
| Downtime Required  | No        |
| Change Required    | Yes       |
| Skill Level        | Advanced  |

---

# 1. Purpose

This runbook describes the standardized procedure for expanding the capacity of an existing Ceph storage cluster.

The objective is to increase available storage resources while maintaining cluster availability, redundancy, and operational stability.

---

# 2. Scope

This runbook applies to:

* Capacity expansion
* Addition of storage nodes
* Addition of storage devices
* Planned infrastructure growth

It does not describe the detailed deployment of individual OSDs. Refer to **RB-004 – Add New Ceph OSD** for the OSD deployment procedure.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Capacity planning completed
* Cluster health verified
* New hardware installed and operational
* Required network connectivity available
* Administrative access to the Ceph cluster

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                        |
| --------------------- | ------------------------------------- |
| Storage Administrator | Execute the expansion procedure       |
| Platform Engineer     | Coordinate infrastructure integration |
| Service Owner         | Approve capacity expansion            |

---

# 5. Risks

| Risk                        | Impact                            | Mitigation                                        |
| --------------------------- | --------------------------------- | ------------------------------------------------- |
| Incorrect capacity planning | Future resource shortage          | Validate capacity requirements before expansion   |
| Cluster rebalance           | Temporary performance degradation | Schedule expansion during low utilization         |
| Hardware incompatibility    | Deployment failure                | Verify hardware compatibility before installation |

---

# 6. Procedure

## Phase 1 – Planning

### Step 1 – Review Capacity Requirements

Confirm that storage expansion is required based on current utilization and projected growth.

---

### Step 2 – Verify Cluster Health

Perform a complete storage health verification before introducing additional resources.

---

## Phase 2 – Infrastructure Preparation

### Step 3 – Install New Hardware

Install and verify all required storage hardware according to organizational procedures.

---

### Step 4 – Verify Network Connectivity

Confirm that all new nodes and storage interfaces are operational and properly connected.

---

## Phase 3 – Cluster Expansion

### Step 5 – Add New OSDs

Deploy the required Object Storage Daemons.

Refer to:

**RB-004 – Add New Ceph OSD**

Repeat the procedure as necessary for each storage device.

---

### Step 6 – Verify Cluster Integration

Confirm that all newly deployed OSDs have successfully joined the cluster.

---

## Phase 4 – Recovery

### Step 7 – Monitor Data Rebalancing

Allow the cluster to redistribute placement groups until the storage cluster reaches a stable operational state.

---

## Phase 5 – Final Validation

### Step 8 – Verify Cluster Capacity

Confirm that the expected storage capacity is available and correctly reported.

---

# 7. Validation

The expansion is considered successful when:

* New storage capacity is available.
* All deployed OSDs are operational.
* Data rebalancing has completed.
* Cluster health is normal.
* Client access is unaffected.

---

# 8. Rollback

If expansion cannot be completed successfully:

* Suspend additional deployment activities.
* Stabilize the existing cluster configuration.
* Follow vendor-specific recovery procedures before continuing.

---

# 9. Escalation

| Condition                             | Action                                   |
| ------------------------------------- | ---------------------------------------- |
| Cluster health degrades               | Pause expansion immediately              |
| Hardware integration fails            | Investigate infrastructure configuration |
| Data redistribution does not complete | Escalate to Storage Operations           |

---

# 10. Documentation

Record:

* Expansion date
* Added storage capacity
* Added storage nodes (if applicable)
* Number of deployed OSDs
* Validation results
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-004 – Add New Ceph OSD
* RB-010 – Ceph Health Validation
