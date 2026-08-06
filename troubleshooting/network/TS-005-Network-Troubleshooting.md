# TS-005 – Network Troubleshooting

**Troubleshooting ID:** TS-005
**Version:** 1.0
**Status:** Approved
**Category:** Network
**Platform:** Enterprise Network Infrastructure
**Related Runbook:** RB-016 – Network Switch Failure Response
**Related Work Instruction:** WI-005 – Network Switch Management
**Owner:** Network Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Troubleshooting Guide provides a structured approach for diagnosing and resolving network connectivity and infrastructure issues affecting enterprise environments.

It supports fault isolation, service recovery, and validation while minimizing operational disruption.

---

# 2. Scope

This guide applies to:

* Network switch issues
* VLAN connectivity
* Layer 2 issues
* Layer 3 routing issues
* Link failures
* Redundant network path failures
* Performance degradation
* Network service interruptions

---

# 3. Symptoms

Typical indicators include:

* Device unreachable
* Link down
* Packet loss
* High latency
* VLAN communication failure
* Routing failure
* DNS resolution failure
* Gateway unreachable
* Network monitoring alerts

---

# 4. Prerequisites

Before troubleshooting:

* Administrative access to the affected network devices
* Administrative access to the monitoring platform
* Current network topology available
* Recent maintenance activities reviewed
* Physical access available if required

---

# 5. Diagnostic Procedure

## Step 1 – Verify Physical Connectivity

### Objective

Confirm that the physical network infrastructure is operational.

### Actions

Review:

* Power status
* Interface status
* Link LEDs
* Cabling
* Optical transceivers (if applicable)

### Expected Result

Physical connectivity has been verified.

---

## Step 2 – Verify Network Device Health

### Objective

Confirm that the affected device is operating normally.

### Actions

Review:

* Device status
* CPU utilization
* Memory utilization
* Environmental status
* System logs
* Monitoring alerts

### Expected Result

The operational state of the network device is understood.

---

## Step 3 – Identify the Affected Layer

### Objective

Determine the scope of the connectivity issue.

### Actions

Investigate:

* Layer 2 switching
* VLAN configuration
* Trunk links
* Link aggregation
* Layer 3 routing
* Gateway availability
* DNS services
* External connectivity

### Expected Result

The affected network layer has been identified.

---

## Step 4 – Perform Recovery

### Actions

Execute the approved recovery procedure.

Refer to the corresponding Runbook or Work Instruction where applicable.

### Expected Result

Network services begin returning to normal operation.

---

## Step 5 – Validate Network Operation

### Actions

Verify:

* Device availability
* Interface status
* Network connectivity
* Client communication
* Infrastructure communication
* Monitoring status

### Expected Result

Network services are fully operational.

---

# 6. Common Issues

| Symptom                    | Possible Cause               | Recommended Action                                              |
| -------------------------- | ---------------------------- | --------------------------------------------------------------- |
| Device unreachable         | Power or hardware failure    | Verify device power, hardware status, and physical connectivity |
| Link down                  | Cable or interface failure   | Verify cabling, optics, and interface status                    |
| VLAN communication failure | VLAN or trunk configuration  | Validate VLAN assignments and trunk configuration               |
| Gateway unreachable        | Routing issue                | Verify routing configuration and gateway availability           |
| High latency               | Congestion or hardware issue | Review interface utilization and hardware health                |
| Packet loss                | Network instability          | Verify interface errors and physical connectivity               |
| DNS resolution failure     | DNS service unavailable      | Verify DNS service availability and client configuration        |
| Monitoring alert           | Infrastructure event         | Review logs and correlate with recent changes                   |

---

# 7. Escalation

Escalate when:

* Multiple network segments are affected.
* Core network services remain unavailable.
* Hardware replacement is required.
* Root cause cannot be identified.
* Vendor support is required.

Document all findings before escalation.

---

# 8. Documentation

Record:

* Date and time
* Affected network device
* Symptoms observed
* Root cause
* Recovery actions
* Validation results
* Related Incident
* Lessons learned

---

# 9. References

* RB-016 – Network Switch Failure Response
* WI-005 – Network Switch Management
* Vendor Documentation
