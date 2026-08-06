# RB-015 – Renew Certificates

**Runbook ID:** RB-015
**Version:** 1.0
**Status:** Approved
**Category:** Security
**Service:** Certificate Management
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# Operational Summary

| Field              | Value                           |
| ------------------ | ------------------------------- |
| Estimated Duration | 30–90 minutes                   |
| Service Impact     | Low to Medium                   |
| Downtime Required  | Depends on the affected service |
| Change Required    | Yes                             |
| Skill Level        | Intermediate                    |

---

# 1. Purpose

This runbook describes the standardized procedure for renewing digital certificates used by infrastructure services.

The objective is to renew certificates before expiration while maintaining service availability, secure communications, and operational continuity.

---

# 2. Scope

This runbook applies to certificates used by infrastructure components, including but not limited to:

* Kubernetes
* Virtualization platforms
* Storage platforms
* Backup systems
* Web services
* APIs
* Internal PKI services

The specific renewal method depends on the platform and is documented in the corresponding Work Instruction.

---

# 3. Prerequisites

Before starting:

* Approved change request (if required)
* Administrative access to the affected system
* Certificate expiration verified
* Certificate Authority (CA) available
* Required maintenance window confirmed (if applicable)
* Backup of current configuration completed where appropriate

---

# 4. Roles and Responsibilities

| Role                 | Responsibility                                |
| -------------------- | --------------------------------------------- |
| System Administrator | Execute the certificate renewal               |
| Platform Engineer    | Validate service functionality after renewal  |
| Service Owner        | Approve maintenance activities where required |

---

# 5. Risks

| Risk                             | Impact                         | Mitigation                                   |
| -------------------------------- | ------------------------------ | -------------------------------------------- |
| Expired certificate              | Service interruption           | Renew certificates before expiration         |
| Incorrect certificate deployment | Authentication or TLS failures | Verify certificate details before deployment |
| Service restart required         | Temporary service interruption | Schedule maintenance appropriately           |

---

# 6. Procedure

## Phase 1 – Preparation

### Step 1 – Identify Certificates

Identify the certificate(s) requiring renewal.

Confirm the associated service, expiration date, and issuing Certificate Authority.

---

### Step 2 – Verify Dependencies

Identify any dependent systems, clients, or applications that may be affected.

---

## Phase 2 – Renewal

### Step 3 – Generate or Request the New Certificate

Obtain a replacement certificate using the approved organizational procedure.

---

### Step 4 – Deploy the Certificate

Install the renewed certificate and any required certificate chain.

---

### Step 5 – Apply Configuration Changes

Update the affected service configuration where required.

Restart or reload services only if necessary.

---

## Phase 3 – Validation

### Step 6 – Verify Certificate Installation

Confirm that the new certificate is active and correctly presented by the service.

---

### Step 7 – Verify Service Availability

Confirm that the affected service is operating normally and that secure connections can be established.

---

### Step 8 – Verify Certificate Validity

Confirm the certificate validity period, subject information, issuer, and trust chain.

---

# 7. Validation

The renewal is considered successful when:

* The new certificate is active.
* The previous certificate has been replaced.
* Secure connections are established successfully.
* The affected service is fully operational.
* No certificate-related warnings or errors are reported.

---

# 8. Rollback

If the certificate renewal cannot be completed successfully:

* Restore the previous certificate if it remains valid.
* Revert configuration changes where necessary.
* Investigate the cause before attempting another renewal.

---

# 9. Escalation

| Condition                           | Action                                              |
| ----------------------------------- | --------------------------------------------------- |
| Certificate deployment fails        | Escalate to Platform Operations                     |
| Service unavailable after renewal   | Initiate incident management                        |
| Certificate validation unsuccessful | Investigate the certificate chain and configuration |

---

# 10. Documentation

Record:

* Renewal date and time
* Affected service
* Certificate issuer
* Certificate expiration date
* Validation results
* Related change reference

---

# 11. References

* Organization Certificate Management Policy
* Organization Public Key Infrastructure (PKI) Documentation
* Related Work Instructions for platform-specific certificate renewal
