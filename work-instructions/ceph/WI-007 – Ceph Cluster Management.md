# WI-007 – Ceph Cluster Management

**Work Instruction ID:** WI-007
**Version:** 1.0
**Status:** Approved
**Category:** Storage
**Platform:** Ceph
**Related Runbooks:** RB-006, RB-007, RB-008, RB-009, RB-010
**Owner:** Storage Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedures for managing a Ceph cluster, including cluster health verification, monitor and manager administration, cluster maintenance, and upgrade preparation.

---

# 2. Scope

This instruction applies to administrative operations performed on a Ceph storage cluster.

It complements OSD-specific procedures documented in **WI-002 – Ceph OSD Management**.

---

# 3. Prerequisites

Before starting:

* Administrative access to the Ceph cluster
* Administrative access to cluster nodes
* Approved maintenance window (if applicable)
* Cluster documentation available
* Current cluster health verified

---

# 4. Safety Notes

⚠ Verify cluster health before performing administrative operations.

⚠ Maintain monitor quorum during maintenance.

⚠ Perform upgrades only using supported upgrade paths.

⚠ Avoid concurrent maintenance on multiple critical cluster services.

---

# 5. Related Documents

* RB-006 – Ceph Cluster Expansion
* RB-007 – Replace Ceph Monitor
* RB-008 – Replace Ceph Manager
* RB-009 – Replace Ceph Metadata Server
* RB-010 – Ceph Upgrade
* WI-002 – Ceph OSD Management
* TS-002 – Ceph Troubleshooting

---

# 6. Procedure

---

## Step 1 – Verify Cluster Health

### Objective

Confirm that the cluster is healthy before administrative maintenance.

### Actions

Review cluster status.

```bash
ceph -s
```

Review detailed health information.

```bash
ceph health detail
```

### Expected Result

The cluster is operational and ready for maintenance.

### Verification

Confirm that no unexpected critical health issues exist.

---

## Step 2 – Review Cluster Topology

### Objective

Verify the current cluster configuration.

### Actions

Display monitor status.

```bash
ceph mon stat
```

Display manager status.

```bash
ceph mgr stat
```

Display cluster topology.

```bash
ceph osd tree
```

### Expected Result

Cluster services report the expected topology.

### Verification

Confirm that monitors, managers, and OSDs are operational.

---

## Step 3 – Perform Administrative Maintenance

### Objective

Execute the approved maintenance activity.

### Actions

Examples include:

* Monitor maintenance
* Manager maintenance
* Metadata Server maintenance
* Cluster expansion
* Cluster upgrade

Follow the approved organizational procedure.

### Expected Result

The planned maintenance activity has been completed successfully.

### Verification

Confirm successful completion before proceeding.

---

## Step 4 – Validate Cluster Operation

### Objective

Verify that the cluster operates normally after maintenance.

### Actions

Review:

```bash
ceph -s
```

Check placement groups.

```bash
ceph pg stat
```

Review cluster services.

```bash
ceph orch ps
```

### Expected Result

All required cluster services are operational.

### Verification

Confirm that the cluster reports normal operational status.

---

## Step 5 – Final Validation

### Objective

Confirm successful completion of maintenance.

### Actions

Review:

* Cluster health
* Recovery status
* Service availability
* Monitoring alerts

### Expected Result

The cluster is healthy and fully operational.

### Verification

Confirm that all validation checks have completed successfully.

---

# 7. Rollback

If maintenance cannot be completed successfully:

* Suspend further administrative changes.
* Restore the previous operational state where possible.
* Investigate the cause before continuing.

---

# 8. Troubleshooting

If issues occur during cluster administration, refer to:

* TS-002 – Ceph Troubleshooting

---

# 9. Documentation

Record:

* Maintenance date
* Cluster name
* Administrative activity performed
* Validation results
* Observed issues
* Related Change Request

---

# 10. References

* RB-006 – Ceph Cluster Expansion
* RB-007 – Replace Ceph Monitor
* RB-008 – Replace Ceph Manager
* RB-009 – Replace Ceph Metadata Server
* RB-010 – Ceph Upgrade
* WI-002 – Ceph OSD Management
* TS-002 – Ceph Troubleshooting
* Ceph Documentation
