# WI-003 – Kubernetes Node Management

**Work Instruction ID:** WI-003
**Version:** 1.0
**Status:** Approved
**Category:** Kubernetes
**Platform:** Kubernetes
**Related Runbooks:** RB-013, RB-014
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedures for managing Kubernetes cluster nodes, including worker node maintenance, control plane maintenance, workload migration, and node validation.

---

# 2. Scope

This instruction applies to Kubernetes clusters operated according to organizational standards.

It supports both worker node and control plane maintenance activities.

---

# 3. Prerequisites

Before starting:

* Administrative access to the Kubernetes cluster
* `kubectl` configured
* Cluster health verified
* Approved maintenance window
* Replacement node available (if applicable)

---

# 4. Safety Notes

⚠ Verify cluster health before starting maintenance.

⚠ Ensure sufficient cluster capacity exists before draining workloads.

⚠ Never perform maintenance on multiple control plane nodes simultaneously.

⚠ Verify workload redundancy before draining production nodes.

---

# 5. Related Documents

* RB-013 – Replace Kubernetes Worker Node
* RB-014 – Replace Kubernetes Control Plane Node
* TS-003 – Kubernetes Troubleshooting

---

# 6. Procedure

---

## Step 1 – Verify Cluster Health

### Objective

Confirm that the cluster is operating normally before maintenance.

### Actions

Review node status.

```bash
kubectl get nodes
```

Review cluster events.

```bash
kubectl get events -A --sort-by=.lastTimestamp
```

Review system pods.

```bash
kubectl get pods -A
```

### Expected Result

* All required nodes are Ready.
* Critical system pods are operational.
* No unexpected cluster-wide issues are present.

### Verification

Confirm the cluster is healthy before proceeding.

---

## Step 2 – Prepare the Node

### Objective

Prevent new workloads from being scheduled to the target node.

### Actions

Mark the node as unschedulable.

```bash
kubectl cordon <NODE_NAME>
```

Verify node status.

```bash
kubectl get nodes
```

### Expected Result

The node is marked as **SchedulingDisabled**.

### Verification

Confirm that no new workloads are scheduled to the node.

---

## Step 3 – Drain the Node

### Objective

Safely migrate workloads from the target node.

### Actions

Drain the node.

```bash
kubectl drain <NODE_NAME> \
  --ignore-daemonsets \
  --delete-emptydir-data
```

Monitor workload migration.

```bash
kubectl get pods -A -o wide
```

### Expected Result

All evictable workloads have been relocated successfully.

### Verification

Confirm that no application workloads remain on the node.

---

## Step 4 – Perform Maintenance

### Objective

Execute the approved maintenance activity.

### Actions

Examples include:

* Operating system updates
* Hardware replacement
* Kubernetes upgrades
* Security patching
* Node replacement

Follow the approved maintenance plan.

### Expected Result

Maintenance completed successfully.

### Verification

Confirm that the maintenance activity completed without errors.

---

## Step 5 – Return the Node to Service

### Objective

Allow the node to receive workloads again.

### Actions

Mark the node as schedulable.

```bash
kubectl uncordon <NODE_NAME>
```

Verify node status.

```bash
kubectl get nodes
```

Monitor workload scheduling.

```bash
kubectl get pods -A -o wide
```

### Expected Result

The node reports **Ready** and is available for scheduling.

### Verification

Confirm that workloads are successfully scheduled to the node.

---

## Step 6 – Final Validation

### Objective

Confirm normal cluster operation.

### Actions

Verify workloads.

```bash
kubectl get pods -A
```

Verify node health.

```bash
kubectl describe node <NODE_NAME>
```

### Expected Result

* Cluster healthy
* Node Ready
* Workloads operational
* No scheduling issues

### Verification

Confirm successful completion of the maintenance.

---

# 7. Rollback

If maintenance cannot be completed:

* Keep the node cordoned if it is not ready for production.
* Restore the previous operational state where possible.
* Reintegrate the original node if applicable.
* Escalate according to organizational procedures.

---

# 8. Troubleshooting

If issues occur during maintenance, refer to:

* TS-003 – Kubernetes Troubleshooting

---

# 9. Documentation

Record:

* Maintenance date
* Node name
* Maintenance activity
* Validation results
* Observed issues
* Related Change Request

---

# 10. References

* RB-013 – Replace Kubernetes Worker Node
* RB-014 – Replace Kubernetes Control Plane Node
* TS-003 – Kubernetes Troubleshooting
* Kubernetes Documentation
