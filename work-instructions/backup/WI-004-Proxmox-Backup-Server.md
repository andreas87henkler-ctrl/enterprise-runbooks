# WI-004 – Proxmox Backup Server Management

**Work Instruction ID:** WI-004
**Version:** 1.0
**Status:** Approved
**Category:** Backup & Recovery
**Platform:** Proxmox Backup Server (PBS)
**Related Runbooks:** RB-011, RB-012
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedures for managing Proxmox Backup Server (PBS), including backup verification, datastore management, backup integrity checks, and restore preparation.

---

# 2. Scope

This instruction applies to Proxmox Backup Server environments used for protecting virtual machines, Linux containers, and other supported workloads.

---

# 3. Prerequisites

Before starting:

* Administrative access to Proxmox Backup Server
* Administrative access to the Proxmox VE cluster (if required)
* Backup repository available
* Sufficient storage capacity
* Approved maintenance or recovery activity (if applicable)

---

# 4. Safety Notes

⚠ Verify backup availability before initiating recovery operations.

⚠ Never remove backup snapshots without confirming the applicable retention policy.

⚠ Verify datastore capacity before starting backup or restore operations.

⚠ Ensure backup verification completes successfully before relying on recovery points.

---

# 5. Related Documents

* RB-011 – Restore Virtual Machine from Backup
* RB-012 – Restore from Proxmox Backup Server
* TS-004 – Backup and Recovery Troubleshooting

---

# 6. Procedure

---

## Step 1 – Verify Backup Server Status

### Objective

Confirm that Proxmox Backup Server is operating normally.

### Actions

Review PBS service status.

```bash
systemctl status proxmox-backup
```

Check datastore status.

```bash
proxmox-backup-manager datastore list
```

Review storage usage.

```bash
proxmox-backup-manager datastore status
```

### Expected Result

* PBS services are running.
* Datastores are online.
* No unexpected storage warnings are present.

### Verification

Confirm normal server operation before continuing.

---

## Step 2 – Verify Available Backups

### Objective

Confirm that the required backups are available.

### Actions

List available backup snapshots.

```bash
proxmox-backup-client snapshots
```

Verify datastore contents through the PBS management interface or command-line tools.

### Expected Result

Required backup snapshots are present.

### Verification

Confirm that the desired restore point exists.

---

## Step 3 – Verify Backup Integrity

### Objective

Ensure backup data is usable.

### Actions

Run datastore verification according to organizational procedures.

Review verification results for any reported errors.

### Expected Result

Backup verification completes successfully without integrity issues.

### Verification

Confirm that no backup corruption has been detected.

---

## Step 4 – Perform Backup or Restore Operations

### Objective

Execute the approved backup or restore activity.

### Actions

Perform the required operation using the Proxmox VE or PBS management interface, or the approved command-line tools, in accordance with organizational procedures.

### Expected Result

The requested operation completes successfully.

### Verification

Confirm that the backup or restore finished without errors.

---

## Step 5 – Validate the Operation

### Objective

Confirm that the completed operation meets recovery or backup objectives.

### Actions

Verify:

* Backup completion
* Restore completion (if applicable)
* Datastore availability
* Job status
* System logs

### Expected Result

The backup or restore operation is successful.

### Verification

Confirm that the protected workload or restored system is operational as expected.

---

# 7. Rollback

If the operation cannot be completed successfully:

* Suspend further backup or restore activities.
* Preserve the existing backup data.
* Investigate the cause before repeating the operation.
* Escalate according to organizational procedures if required.

---

# 8. Troubleshooting

If issues occur, refer to:

* TS-004 – Backup and Recovery Troubleshooting

---

# 9. Documentation

Record:

* Date and time
* Datastore
* Backup or restore operation
* Validation results
* Observed issues
* Related Change Request or Incident

---

# 10. References

* RB-011 – Restore Virtual Machine from Backup
* RB-012 – Restore from Proxmox Backup Server
* TS-004 – Backup and Recovery Troubleshooting
* Proxmox Backup Server Documentation
