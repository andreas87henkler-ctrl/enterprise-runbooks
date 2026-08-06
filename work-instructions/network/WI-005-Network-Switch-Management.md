# WI-005 – Network Switch Management

**Work Instruction ID:** WI-005
**Version:** 1.0
**Status:** Approved
**Category:** Network
**Platform:** Managed Ethernet Switches
**Related Runbook:** RB-016 – Network Switch Failure Response
**Owner:** Network Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedures for managing enterprise network switches, including health verification, configuration validation, maintenance activities, and service restoration.

---

# 2. Scope

This instruction applies to managed Layer 2 and Layer 3 network switches operated within the organization's infrastructure.

Vendor-specific implementation details shall be documented separately where required.

---

# 3. Prerequisites

Before starting:

* Administrative access to the network device
* Administrative access to the network management platform
* Current network documentation available
* Approved maintenance window (if applicable)
* Current configuration backup available

---

# 4. Safety Notes

⚠ Verify the correct target device before making configuration changes.

⚠ Ensure that a current configuration backup is available.

⚠ Validate network redundancy before performing maintenance.

⚠ Avoid changes during critical business operations unless responding to an incident.

---

# 5. Related Documents

* RB-016 – Network Switch Failure Response
* TS-005 – Network Troubleshooting

---

# 6. Procedure

---

## Step 1 – Verify Device Health

### Objective

Confirm that the switch is operating normally.

### Actions

Review:

* Device status
* CPU utilization
* Memory utilization
* Interface status
* System logs
* Environmental status (temperature, fans, power supplies)

### Expected Result

The switch reports normal operational status with no critical alarms.

### Verification

Confirm that monitoring systems report the device as healthy.

---

## Step 2 – Verify Network Connectivity

### Objective

Confirm that network connectivity is functioning correctly.

### Actions

Review:

* Uplink status
* VLAN configuration
* Trunk links
* Link aggregation groups (LAG/LACP)
* Routing status (if applicable)

### Expected Result

All required network connections are operational.

### Verification

Confirm expected connectivity between dependent systems.

---

## Step 3 – Perform Maintenance

### Objective

Execute the approved maintenance activity.

### Actions

Examples include:

* Apply configuration changes
* Update firmware
* Replace hardware components
* Modify VLAN configuration
* Restart management services (if applicable)

Follow the organization's approved maintenance procedure.

### Expected Result

The planned maintenance has been completed successfully.

### Verification

Confirm that the maintenance activity completed without errors.

---

## Step 4 – Validate Network Services

### Objective

Verify that network services are operating correctly.

### Actions

Confirm:

* Interface status
* Uplink redundancy
* Network connectivity
* Client communication
* Infrastructure communication

### Expected Result

Network communication has been restored without unexpected issues.

### Verification

Validate connectivity using monitoring systems and operational testing.

---

## Step 5 – Final Health Check

### Objective

Confirm that the switch has returned to normal operation.

### Actions

Review:

* System status
* Event logs
* Monitoring alerts
* Network topology status

### Expected Result

The switch is fully operational and no active alerts remain.

### Verification

Confirm successful completion of the maintenance activity.

---

# 7. Rollback

If maintenance cannot be completed successfully:

* Restore the previous device configuration.
* Revert configuration changes where applicable.
* Validate connectivity after rollback.
* Escalate according to organizational procedures if required.

---

# 8. Troubleshooting

If issues occur during maintenance, refer to:

* TS-005 – Network Troubleshooting

---

# 9. Documentation

Record:

* Maintenance date
* Device name
* Maintenance activity
* Configuration changes
* Validation results
* Observed issues
* Related Change Request

---

# 10. References

* RB-016 – Network Switch Failure Response
* TS-005 – Network Troubleshooting
* Vendor Documentation
