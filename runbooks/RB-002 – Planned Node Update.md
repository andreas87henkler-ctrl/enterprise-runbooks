# RB-002 – Planned Node Update

**Runbook ID:** RB-002
**Version:** 1.0
**Status:** Approved
**Category:** Infrastructure
**Service:** Proxmox Virtual Environment (PVE)
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                                        |
| ------------------ | -------------------------------------------- |
| Estimated Duration | 30–60 minutes                                |
| Service Impact     | Low (if workloads are migrated successfully) |
| Downtime Required  | No (HA Cluster)                              |
| Change Required    | Yes                                          |
| Skill Level        | Intermediate                                 |

---

# 1. Purpose

This runbook describes the standardized procedure for performing a planned maintenance update on a Proxmox Virtual Environment (PVE) cluster node.

The objective is to update a single cluster node while maintaining service availability whenever possible.

---

# 2. Scope

This runbook applies to:

* Planned operating system updates
* Proxmox VE package updates
* Firmware maintenance (where applicable)
* Cluster nodes participating in a healthy Proxmox cluster

It does not cover emergency maintenance or cluster recovery procedures.

---

# 3. Prerequisites

Before starting:

* Approved maintenance window
* Verified cluster health (RB-001)
* Administrative access to the cluster
* SSH access to the target node
* Current backups verified (if required by organizational policy)

---

# 4. Roles and Responsibilities

| Role                 | Responsibility                         |
| -------------------- | -------------------------------------- |
| System Administrator | Execute the update procedure           |
| Platform Engineer    | Support complex maintenance activities |
| Service Owner        | Approve maintenance window             |

---

# 5. Risks

| Risk                 | Impact                        | Mitigation                         |
| -------------------- | ----------------------------- | ---------------------------------- |
| VM migration failure | Possible service interruption | Verify migration before continuing |
| Node fails to reboot | Reduced cluster capacity      | Investigate before continuing      |
| Update failure       | Maintenance delay             | Follow vendor guidance             |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Verify Cluster Health

Perform the health check described in **RB-001 – Proxmox Cluster Health Check**.

Proceed only if the cluster is healthy.

---

### Step 2 – Verify Target Node

Confirm that the correct node has been selected for maintenance.

---

## Phase 2 – Prepare the Node

### Step 3 – Migrate Virtual Machines

Migrate running virtual machines to other cluster nodes where applicable.

Use either the Proxmox Web UI or the appropriate CLI tools.

Verify that critical workloads have been successfully relocated before continuing.

---

### Step 4 – Stop or Migrate Containers

Migrate or gracefully stop Linux containers according to organizational policy.

---

## Phase 3 – Maintenance Mode

### Step 5 – Place the Node into Maintenance

Prevent new workloads from being scheduled on the target node.

Use the appropriate maintenance procedure for your environment.

---

## Phase 4 – Update the Node

### Step 6 – Refresh Package Information

```bash
apt update
```

---

### Step 7 – Install Updates

```bash
apt full-upgrade
```

Review the output carefully before confirming any package changes.

---

## Phase 5 – Reboot

### Step 8 – Reboot the Node

```bash
reboot
```

Wait until the node has fully rejoined the cluster.

---

## Phase 6 – Validation

### Step 9 – Verify Node Status

Confirm:

* Node is online
* Cluster membership restored
* No update errors reported

---

### Step 10 – Verify Cluster Health

Execute **RB-001 – Proxmox Cluster Health Check** again.

Proceed only if the cluster returns to a healthy operational state.

---

## Phase 7 – Return to Service

### Step 11 – Resume Normal Operations

Allow workloads to return to the updated node according to organizational policy.

Verify that the node is available for normal production use.

---

# 7. Validation

The maintenance is considered successful when:

* The updated node has rejoined the cluster.
* All services are operational.
* No unexpected errors are reported.
* Cluster health has been verified.
* Production workloads are operating normally.

---

# 8. Rollback

If the update cannot be completed successfully:

* Keep workloads on healthy cluster nodes.
* Do not return the affected node to production until the issue has been resolved.
* Follow vendor-specific recovery procedures where necessary.

---

# 9. Escalation

| Condition                        | Action                            |
| -------------------------------- | --------------------------------- |
| Node fails to rejoin the cluster | Escalate to Platform Operations   |
| Cluster health degraded          | Pause maintenance and investigate |
| Critical workload unavailable    | Initiate incident management      |

---

# 10. Documentation

Record:

* Maintenance date
* Updated node
* Installed package updates
* Validation results
* Observed issues
* Related change record

---

# 11. References

* RB-001 – Proxmox Cluster Health Check
* Proxmox VE Administration Guide
* Operating System Update Documentation
