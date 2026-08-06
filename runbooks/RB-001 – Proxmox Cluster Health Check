# RB-001 – Proxmox Cluster Health Check

**Runbook ID:** RB-001
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

| Field              | Value         |
| ------------------ | ------------- |
| Estimated Duration | 10–15 minutes |
| Service Impact     | None          |
| Downtime Required  | No            |
| Change Required    | No            |
| Skill Level        | Intermediate  |

---

# 1. Purpose

This runbook provides a standardized procedure for verifying the operational health of a Proxmox Virtual Environment (PVE) cluster.

The health check should be performed before planned maintenance, after infrastructure changes, following unexpected events, or as part of routine operational activities.

---

# 2. Scope

This runbook covers the verification of:

* Cluster health
* Cluster quorum
* Cluster nodes
* Storage availability
* Ceph cluster health (if applicable)
* Virtual machines
* Linux containers
* Network interfaces
* Time synchronization

---

# 3. Prerequisites

Ensure the following prerequisites are met before starting:

* Administrative access to the Proxmox cluster
* SSH access to at least one cluster node
* Access to the Proxmox CLI
* Sufficient privileges to execute diagnostic commands

---

# 4. Roles and Responsibilities

| Role                 | Responsibility                          |
| -------------------- | --------------------------------------- |
| System Administrator | Perform the health check                |
| Platform Engineer    | Investigate and resolve detected issues |
| Service Owner        | Review operational impact if required   |

---

# 5. Risks

This is a read-only procedure.

No configuration changes are performed and no service interruption is expected.

---

# 6. Procedure

## Phase 1 – Cluster Verification

### Step 1 – Verify Cluster Status

**Objective**

Confirm that the cluster is operational and quorum has been established.

**Command**

```bash
pvecm status
```

**Expected Result**

* Quorum established
* All cluster nodes listed
* No communication errors reported

---

### Step 2 – Verify Cluster Nodes

**Command**

```bash
pvesh get /nodes
```

**Expected Result**

* All expected nodes are online
* No node reports an unexpected offline state

---

## Phase 2 – Storage Verification

### Step 3 – Verify Storage Status

**Command**

```bash
pvesm status
```

**Expected Result**

* All configured storage resources are available
* No storage reports an inactive or unavailable state

---

### Step 4 – Verify Ceph Health *(if applicable)*

**Command**

```bash
ceph -s
```

**Expected Result**

* HEALTH_OK
* All OSDs are up and in
* No degraded placement groups
* No recovery or rebalance operations in progress

> **Note**
>
> Skip this step if the cluster does not use Ceph.

---

## Phase 3 – Workload Verification

### Step 5 – Verify Virtual Machines

**Command**

```bash
qm list
```

**Expected Result**

* Critical virtual machines are running
* No unexpected stopped virtual machines

---

### Step 6 – Verify Linux Containers

**Command**

```bash
pct list
```

**Expected Result**

* Required containers are running
* No unexpected stopped containers

---

## Phase 4 – Network Verification

### Step 7 – Verify Network Interfaces

**Command**

```bash
ip address
```

**Expected Result**

* All required interfaces are available
* IP configuration appears correct
* No missing interfaces

---

## Phase 5 – Time Synchronization

### Step 8 – Verify Time Synchronization

**Command**

```bash
timedatectl
```

**Expected Result**

* System clock synchronized
* NTP service active

---

# 7. Validation

The health check is successful when all of the following conditions are met:

* Cluster quorum established
* All nodes online
* Storage available
* Ceph reports `HEALTH_OK` (if applicable)
* Critical virtual machines operational
* Required containers operational
* Network interfaces available
* System time synchronized

---

# 8. Rollback

Not applicable.

This procedure performs validation only and does not modify the environment.

---

# 9. Escalation

| Condition                     | Action                                      |
| ----------------------------- | ------------------------------------------- |
| Cluster quorum unavailable    | Escalate immediately to Platform Operations |
| Storage unavailable           | Investigate storage subsystem               |
| Ceph reports `HEALTH_ERR`     | Initiate storage incident                   |
| Critical workload unavailable | Open an incident and begin troubleshooting  |

---

# 10. Documentation

Record the following information after completing the health check:

* Date and time
* Operator
* Cluster status
* Findings
* Corrective actions (if applicable)
* Related incident or change reference

---

# 11. References

* EDF-000 – Enterprise Documentation Framework
* EDS-001 – Enterprise Runbook Standard
* Proxmox VE Administration Guide
* Ceph Documentation (if applicable)
