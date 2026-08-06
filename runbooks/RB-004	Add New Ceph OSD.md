# RB-004 – Add New Ceph OSD

**Runbook ID:** RB-004
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

| Field              | Value                          |
| ------------------ | ------------------------------ |
| Estimated Duration | 30–90 minutes                  |
| Service Impact     | None (under normal conditions) |
| Downtime Required  | No                             |
| Change Required    | Yes                            |
| Skill Level        | Advanced                       |

---

# 1. Purpose

This runbook describes the standardized procedure for adding a new Object Storage Daemon (OSD) to an existing Ceph storage cluster.

The objective is to increase storage capacity while maintaining cluster availability and data integrity.

---

# 2. Scope

This runbook applies to:

* Capacity expansion
* Addition of new storage devices
* Expansion of existing Ceph clusters

It does not cover replacing existing OSDs or recovering failed storage devices.

---

# 3. Prerequisites

Before starting:

* Approved change request
* Administrative access to the Ceph cluster
* Administrative access to the target storage node
* New storage device installed and detected
* Cluster health verified

---

# 4. Roles and Responsibilities

| Role                  | Responsibility             |
| --------------------- | -------------------------- |
| Storage Administrator | Execute the procedure      |
| Platform Engineer     | Support deployment         |
| Service Owner         | Approve capacity expansion |

---

# 5. Risks

| Risk                       | Impact                          | Mitigation                                  |
| -------------------------- | ------------------------------- | ------------------------------------------- |
| Incorrect device selection | Data loss                       | Verify storage device before deployment     |
| Cluster rebalance          | Temporary performance reduction | Schedule maintenance during low utilization |
| Deployment failure         | Expansion delayed               | Validate hardware and deployment steps      |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the cluster is operating normally before adding new storage.

---

### Step 2 – Verify the New Storage Device

Confirm that the operating system detects the new storage device and that it is not currently in use.

---

## Phase 2 – Deploy the OSD

### Step 3 – Prepare the Storage Device

Prepare the storage device according to the organization's deployment procedure.

---

### Step 4 – Create the New OSD

Deploy the new OSD using the organization's preferred deployment method.

Verify that the deployment completes successfully.

---

## Phase 3 – Cluster Integration

### Step 5 – Verify Cluster Membership

Confirm that the new OSD has successfully joined the cluster.

---

### Step 6 – Monitor Data Rebalancing

Monitor the redistribution of placement groups until the cluster reaches a stable operational state.

---

# 7. Validation

The deployment is successful when:

* The new OSD is operational.
* The cluster recognizes the new capacity.
* Data rebalancing has completed.
* Cluster health is normal.
* No storage warnings are present.

---

# 8. Rollback

If deployment cannot be completed:

* Stop the deployment procedure.
* Remove incomplete configuration if required.
* Return the storage device to an unused state according to organizational procedures.

---

# 9. Escalation

| Condition                          | Action                         |
| ---------------------------------- | ------------------------------ |
| OSD deployment fails               | Investigate deployment logs    |
| Cluster health degrades            | Pause the expansion process    |
| Data rebalancing does not complete | Escalate to Storage Operations |

---

# 10. Documentation

Record:

* Date and time
* Storage node
* New OSD identifier
* Storage device information
* Validation results
* Related change reference

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* RB-010 – Ceph Health Validation
* Ceph Documentation
