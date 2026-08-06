# RB-005 – Remove Ceph OSD

**Runbook ID:** RB-005
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

| Field              | Value                                  |
| ------------------ | -------------------------------------- |
| Estimated Duration | 30–90 minutes                          |
| Service Impact     | Low (depending on cluster utilization) |
| Downtime Required  | No                                     |
| Change Required    | Yes                                    |
| Skill Level        | Advanced                               |

---

# 1. Purpose

This runbook describes the standardized procedure for permanently removing an Object Storage Daemon (OSD) from a Ceph storage cluster.

The objective is to safely remove storage capacity while maintaining cluster integrity and data availability.

---

# 2. Scope

This runbook applies to:

* Planned capacity reduction
* Hardware decommissioning
* Storage reconfiguration
* Permanent OSD removal

It does not cover replacing failed OSDs or adding new storage devices.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Ceph cluster
* Administrative access to the target storage node
* Cluster health verified
* Sufficient remaining storage capacity
* Confirmation that removing the OSD will not violate the desired replication policy

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                     |
| --------------------- | ---------------------------------- |
| Storage Administrator | Execute the removal procedure      |
| Platform Engineer     | Support storage operations         |
| Service Owner         | Approve planned capacity reduction |

---

# 5. Risks

| Risk                          | Impact                       | Mitigation                                  |
| ----------------------------- | ---------------------------- | ------------------------------------------- |
| Insufficient cluster capacity | Reduced storage availability | Verify available capacity before removal    |
| Extended data migration       | Reduced cluster performance  | Schedule maintenance during low utilization |
| Incorrect OSD selection       | Data availability risk       | Verify OSD identity before removal          |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the cluster is operating normally before removing an OSD.

---

### Step 2 – Verify Cluster Capacity

Ensure that sufficient storage capacity and redundancy remain after the planned removal.

---

### Step 3 – Identify the Target OSD

Verify the identity of the OSD scheduled for removal.

Confirm that the selected OSD matches the approved maintenance plan.

---

## Phase 2 – OSD Removal

### Step 4 – Prepare the OSD for Removal

Prepare the OSD for removal using the organization's approved Ceph maintenance procedure.

---

### Step 5 – Remove the OSD

Remove the OSD from the cluster following the vendor-recommended procedure.

---

## Phase 3 – Cluster Recovery

### Step 6 – Monitor Data Migration

Monitor data redistribution until all placement groups have completed migration.

---

### Step 7 – Verify Cluster Health

Confirm that the cluster has returned to a healthy operational state.

---

# 7. Validation

The removal is considered successful when:

* The OSD has been removed from the cluster.
* Data migration has completed successfully.
* Storage capacity reflects the planned configuration.
* Cluster health is normal.
* No storage-related warnings remain.

---

# 8. Rollback

If removal cannot be completed successfully:

* Stop further storage modifications.
* Stabilize the cluster before additional maintenance.
* Follow vendor-specific recovery procedures where necessary.

---

# 9. Escalation

| Condition                   | Action                         |
| --------------------------- | ------------------------------ |
| Cluster health degrades     | Pause maintenance immediately  |
| Data migration fails        | Investigate cluster status     |
| Unexpected storage warnings | Escalate to Storage Operations |

---

# 10. Documentation

Record:

* Date and time
* Storage node
* Removed OSD identifier
* Remaining cluster capacity
* Validation results
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-010 – Ceph Health Validation
* Ceph Documentation
