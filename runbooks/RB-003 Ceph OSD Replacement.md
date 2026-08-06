# RB-003 – Ceph OSD Replacement

**Runbook ID:** RB-003
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

| Field              | Value                             |
| ------------------ | --------------------------------- |
| Estimated Duration | 60–120 minutes                    |
| Service Impact     | Low (depending on cluster health) |
| Downtime Required  | No                                |
| Change Required    | Yes                               |
| Skill Level        | Advanced                          |

---

# 1. Purpose

This runbook describes the standardized procedure for replacing a failed or planned-to-be-replaced Ceph Object Storage Daemon (OSD).

The objective is to safely replace an OSD while maintaining cluster integrity and data availability.

---

# 2. Scope

This runbook applies to:

* Planned OSD replacement
* Failed OSD replacement
* Hardware replacement involving storage devices

It assumes that the Ceph cluster is operational before maintenance begins.

---

# 3. Prerequisites

Before starting:

* Approved maintenance window
* Administrative access to the Ceph cluster
* Administrative access to the storage node
* Replacement storage device available
* Cluster health verified (RB-001 or equivalent)

---

# 4. Roles and Responsibilities

| Role                  | Responsibility                    |
| --------------------- | --------------------------------- |
| Storage Administrator | Execute the replacement procedure |
| Platform Engineer     | Support storage maintenance       |
| Service Owner         | Approve maintenance activities    |

---

# 5. Risks

| Risk                   | Impact                      | Mitigation                                     |
| ---------------------- | --------------------------- | ---------------------------------------------- |
| Additional OSD failure | Reduced redundancy          | Verify cluster health before maintenance       |
| Incorrect OSD removal  | Data availability risk      | Verify OSD identity before proceeding          |
| Extended recovery time | Reduced cluster performance | Monitor recovery before completing maintenance |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Confirm that the storage cluster is healthy before replacing an OSD.

---

### Step 2 – Identify the Target OSD

Identify the correct OSD and verify that the replacement device matches the intended hardware.

---

## Phase 2 – Prepare the OSD

### Step 3 – Mark the OSD for Maintenance

Prepare the OSD for removal according to the official Ceph maintenance procedure.

---

### Step 4 – Remove the OSD

Remove the OSD from active service following the vendor-recommended procedure.

---

## Phase 3 – Hardware Replacement

### Step 5 – Replace the Storage Device

Replace the failed or planned storage device.

Verify that the replacement hardware is correctly detected by the operating system.

---

## Phase 4 – Deploy the New OSD

### Step 6 – Create the Replacement OSD

Deploy a new OSD using the organization's preferred deployment method.

Verify that the new OSD successfully joins the cluster.

---

## Phase 5 – Recovery

### Step 7 – Monitor Cluster Recovery

Monitor the recovery process until data rebalancing has completed.

Wait until the cluster reports a healthy operational state.

---

# 7. Validation

The replacement is considered successful when:

* The new OSD is operational.
* Data recovery has completed.
* Cluster health is normal.
* No storage warnings remain.
* Client access is unaffected.

---

# 8. Rollback

If replacement cannot be completed:

* Do not introduce additional storage changes.
* Keep the cluster in a stable configuration.
* Follow vendor-specific recovery guidance before attempting another replacement.

---

# 9. Escalation

| Condition                            | Action                        |
| ------------------------------------ | ----------------------------- |
| Additional OSD failure               | Escalate immediately          |
| Cluster enters critical health state | Pause maintenance             |
| Recovery does not complete           | Investigate storage subsystem |

---

# 10. Documentation

Record:

* Maintenance date
* Storage node
* OSD identifier
* Replacement device
* Recovery completion time
* Validation results
* Related change record

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* Ceph Documentation
* Storage Vendor Documentation
