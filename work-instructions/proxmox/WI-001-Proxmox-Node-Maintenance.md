# WI-001 – Proxmox Node Maintenance

**Work Instruction ID:** WI-001
**Version:** 1.0
**Status:** Approved
**Category:** Infrastructure
**Platform:** Proxmox VE
**Related Runbook:** RB-002 – Planned Node Update
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedure for placing a Proxmox VE node into maintenance, migrating workloads, performing maintenance activities, and returning the node to production.

---

# 2. Scope

This instruction applies to Proxmox VE cluster nodes participating in planned maintenance activities.

---

# 3. Prerequisites

Before starting:

* Administrative access to the Proxmox VE cluster
* Planned maintenance window
* Cluster health verified
* Backup completed (if required)
* Sufficient cluster capacity available for workload migration

---

# 4. Related Documents

* RB-002 – Planned Node Update
* TS-001 – Infrastructure Troubleshooting
* Proxmox VE Administration Guide

---

# 5. Procedure

---

## Step 1 – Verify Cluster Health

### Objective

Ensure the cluster is healthy before starting maintenance.

### Actions

Verify cluster status.

```bash
pvecm status
```

Check node status.

```bash
pvesh get /nodes
```

### Expected Result

* Cluster quorum established
* All nodes online
* No unexpected cluster warnings

### Verification

Confirm that all cluster members report a healthy status.

---

## Step 2 – Verify Running Workloads

### Objective

Identify workloads running on the maintenance node.

### Actions

List virtual machines.

```bash
qm list
```

List Linux containers.

```bash
pct list
```

### Expected Result

All workloads scheduled for migration are identified.

### Verification

Compare running workloads with the maintenance plan.

---

## Step 3 – Migrate Workloads

### Objective

Move workloads to remaining cluster nodes.

### Actions

Live migrate virtual machines.

```bash
qm migrate <VMID> <TARGET_NODE>
```

Move Linux containers.

```bash
pct migrate <CTID> <TARGET_NODE>
```

### Expected Result

No production workload remains on the maintenance node.

### Verification

Verify that all workloads are running on the target nodes.

---

## Step 4 – Perform Maintenance

### Objective

Execute the approved maintenance activity.

### Actions

Examples include:

* Install updates
* Replace hardware
* Restart services
* Perform firmware updates

Follow the approved maintenance plan.

### Expected Result

Maintenance activity completed successfully.

### Verification

Confirm that no maintenance errors occurred.

---

## Step 5 – Return the Node to Service

### Objective

Return the node to normal cluster operation.

### Actions

Verify cluster membership.

```bash
pvecm status
```

Verify node health.

```bash
pvesh get /nodes
```

If required, migrate workloads back to the node.

### Expected Result

The node is operational and available for workload scheduling.

### Verification

Confirm that:

* Cluster health is normal
* Node status is healthy
* Workloads operate normally

---

# 6. Rollback

If maintenance cannot be completed:

* Suspend maintenance activities.
* Restore the previous operational state where possible.
* Return workloads to healthy cluster nodes.
* Escalate according to organizational procedures if required.

---

# 7. Troubleshooting

If issues occur during maintenance:

Refer to:

* TS-001 – Infrastructure Troubleshooting

---

# 8. Documentation

Record:

* Maintenance date
* Node name
* Executed maintenance
* Validation results
* Observed issues
* Related Change Request

---

# 9. References

* RB-002 – Planned Node Update
* TS-001 – Infrastructure Troubleshooting
* Proxmox VE Administration Guide
