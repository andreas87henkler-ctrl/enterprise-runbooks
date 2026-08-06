# TS-002 – Ceph Troubleshooting

**Troubleshooting ID:** TS-002
**Version:** 1.0
**Status:** Approved
**Category:** Storage
**Platform:** Ceph
**Related Runbooks:** RB-003, RB-004, RB-005, RB-006, RB-007, RB-008, RB-009, RB-010
**Related Work Instructions:** WI-002, WI-007
**Owner:** Storage Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Troubleshooting Guide provides a structured approach for diagnosing and resolving operational issues affecting a Ceph storage cluster.

It supports fault isolation, service recovery, and validation while maintaining data integrity and cluster stability.

---

# 2. Scope

This guide applies to:

* Ceph cluster health issues
* OSD failures
* Monitor issues
* Manager issues
* Metadata Server issues
* Placement Group (PG) issues
* Cluster recovery operations
* Performance degradation

---

# 3. Symptoms

Typical indicators include:

* HEALTH_WARN
* HEALTH_ERR
* OSD down
* OSD out
* Placement Groups degraded
* Recovery or backfill taking longer than expected
* Monitor quorum warnings
* Manager unavailable
* Client I/O latency
* Storage performance degradation

---

# 4. Prerequisites

Before troubleshooting:

* Administrative access to the Ceph cluster
* Administrative access to affected hosts
* Monitoring platform available
* Current cluster topology available
* Recent maintenance activities reviewed

---

# 5. Diagnostic Procedure

## Step 1 – Verify Cluster Health

### Objective

Determine the overall operational status of the Ceph cluster.

### Actions

Review cluster health.

```bash
ceph -s
```

Review detailed health information.

```bash
ceph health detail
```

### Expected Result

The current health status and active warnings are clearly identified.

---

## Step 2 – Identify the Affected Component

### Objective

Determine which cluster component is affected.

### Actions

Review:

* OSD status
* Monitor status
* Manager status
* Metadata Server status
* Placement Groups
* Recovery status

### Expected Result

The affected component has been identified.

---

## Step 3 – Determine the Root Cause

### Actions

Investigate possible causes including:

* Hardware failure
* Storage device failure
* Network interruption
* Cluster quorum issues
* Configuration changes
* Capacity exhaustion
* Upgrade-related issues

### Expected Result

The probable root cause has been identified.

---

## Step 4 – Perform Recovery

### Actions

Execute the appropriate recovery procedure.

Refer to the corresponding Work Instruction or Runbook as applicable.

### Expected Result

The affected component begins returning to normal operation.

---

## Step 5 – Validate Cluster Health

### Actions

Verify:

* Cluster health
* OSD status
* Monitor quorum
* Manager status
* Placement Groups
* Client access
* Recovery completion

### Expected Result

The cluster reports normal operational status and all required services are available.

---

# 6. Common Issues

| Symptom             | Possible Cause                | Recommended Action                                             |
| ------------------- | ----------------------------- | -------------------------------------------------------------- |
| HEALTH_WARN         | Cluster warning               | Review detailed health information and resolve reported issues |
| HEALTH_ERR          | Critical cluster issue        | Investigate immediately and prioritize recovery                |
| OSD down            | Hardware or service failure   | Verify host, storage device, and OSD status                    |
| OSD out             | Cluster removed OSD           | Verify maintenance activities or failure conditions            |
| Monitor quorum lost | Monitor unavailable           | Verify monitor availability and cluster quorum                 |
| Manager unavailable | Manager service failure       | Verify manager status and failover                             |
| PG degraded         | Data redundancy reduced       | Monitor recovery and investigate failed OSDs                   |
| Recovery slow       | Heavy cluster activity        | Review cluster load and recovery progress                      |
| Client I/O latency  | Storage or network bottleneck | Verify storage performance and network connectivity            |

---

# 7. Escalation

Escalate when:

* Cluster health remains in **HEALTH_ERR**.
* Multiple OSDs fail simultaneously.
* Monitor quorum cannot be restored.
* Client access is unavailable.
* Root cause cannot be identified.
* Vendor support is required.

Document all findings before escalation.

---

# 8. Documentation

Record:

* Date and time
* Affected cluster
* Symptoms observed
* Root cause
* Recovery actions
* Validation results
* Related Incident
* Lessons learned

---

# 9. References

* RB-003 – Replace Ceph OSD
* RB-004 – Add New Ceph OSD
* RB-005 – Remove Ceph OSD
* RB-006 – Ceph Cluster Expansion
* RB-007 – Replace Ceph Monitor
* RB-008 – Replace Ceph Manager
* RB-009 – Replace Ceph Metadata Server
* RB-010 – Ceph Upgrade
* WI-002 – Ceph OSD Management
* WI-007 – Ceph Cluster Management
* Ceph Documentation
