# TS-003 – Kubernetes Troubleshooting

**Troubleshooting ID:** TS-003
**Version:** 1.0
**Status:** Approved
**Category:** Kubernetes
**Platform:** Kubernetes
**Related Runbooks:** RB-013, RB-014
**Related Work Instructions:** WI-003
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Troubleshooting Guide provides a structured approach for diagnosing and resolving operational issues affecting Kubernetes clusters.

It supports fault isolation, service recovery, and validation while maintaining cluster availability and workload stability.

---

# 2. Scope

This guide applies to:

* Worker node issues
* Control plane issues
* Pod scheduling failures
* Workload failures
* Network connectivity issues
* Storage-related issues
* Cluster health degradation
* Kubernetes service interruptions

---

# 3. Symptoms

Typical indicators include:

* Node NotReady
* Pods stuck in Pending
* CrashLoopBackOff
* ImagePullBackOff
* Failed scheduling
* Control plane unavailable
* API server unreachable
* Persistent Volume issues
* DNS resolution failures
* High resource utilization

---

# 4. Prerequisites

Before troubleshooting:

* Administrative access to the Kubernetes cluster
* `kubectl` configured
* Monitoring platform available
* Current cluster documentation available
* Recent maintenance activities reviewed

---

# 5. Diagnostic Procedure

## Step 1 – Verify Cluster Health

### Objective

Determine the overall health of the Kubernetes cluster.

### Actions

Review cluster nodes.

```bash
kubectl get nodes
```

Review cluster events.

```bash
kubectl get events -A --sort-by=.lastTimestamp
```

Review system workloads.

```bash
kubectl get pods -A
```

### Expected Result

The overall cluster status is understood.

---

## Step 2 – Identify the Affected Component

### Objective

Determine which component is affected.

### Actions

Identify whether the issue affects:

* Control Plane
* Worker Nodes
* Pods
* Deployments
* Networking
* Storage
* DNS
* Ingress
* Monitoring

### Expected Result

The affected subsystem has been identified.

---

## Step 3 – Determine the Root Cause

### Actions

Investigate possible causes including:

* Node unavailable
* Resource exhaustion
* Failed scheduling
* Container image issues
* Network policies
* Storage availability
* Certificate expiration
* Configuration changes
* Recent deployments

### Expected Result

The probable root cause has been identified.

---

## Step 4 – Perform Recovery

### Actions

Execute the appropriate recovery procedure.

Refer to the corresponding Runbook or Work Instruction.

### Expected Result

The affected Kubernetes component begins returning to normal operation.

---

## Step 5 – Validate Cluster Health

### Actions

Verify:

```bash
kubectl get nodes
```

```bash
kubectl get pods -A
```

Review events.

```bash
kubectl get events -A --sort-by=.lastTimestamp
```

Verify workload availability.

### Expected Result

* Nodes Ready
* Pods Running
* Cluster healthy
* Applications available

---

# 6. Common Issues

| Symptom                       | Possible Cause                                   | Recommended Action                                   |
| ----------------------------- | ------------------------------------------------ | ---------------------------------------------------- |
| Node NotReady                 | Node unavailable or kubelet issue                | Verify node health and kubelet status                |
| Pods Pending                  | Insufficient resources or scheduling constraints | Review scheduler events and node capacity            |
| CrashLoopBackOff              | Application startup failure                      | Review container logs and configuration              |
| ImagePullBackOff              | Registry or authentication issue                 | Verify image availability and registry access        |
| API Server unavailable        | Control plane issue                              | Verify API server availability                       |
| DNS failures                  | CoreDNS or network issue                         | Verify DNS service and cluster networking            |
| Persistent Volume unavailable | Storage backend issue                            | Verify storage class and volume status               |
| High resource utilization     | CPU or memory exhaustion                         | Review node resource usage and workload distribution |
| Network connectivity failure  | CNI or network policy issue                      | Verify CNI status and network configuration          |

---

# 7. Escalation

Escalate when:

* Control plane becomes unavailable.
* Multiple worker nodes are affected.
* Critical workloads remain unavailable.
* Root cause cannot be identified.
* Vendor or platform support is required.

Document all findings before escalation.

---

# 8. Documentation

Record:

* Date and time
* Affected cluster
* Namespace
* Affected workload
* Symptoms observed
* Root cause
* Recovery actions
* Validation results
* Related Incident
* Lessons learned

---

# 9. References

* RB-013 – Replace Kubernetes Worker Node
* RB-014 – Replace Kubernetes Control Plane Node
* WI-003 – Kubernetes Node Management
* Kubernetes Documentation
