# WI-006 – Certificate Management

**Work Instruction ID:** WI-006
**Version:** 1.0
**Status:** Approved
**Category:** Security
**Platform:** Public Key Infrastructure (PKI)
**Related Runbook:** RB-015 – Renew Certificates
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Work Instruction describes the technical procedures for managing digital certificates used within enterprise infrastructure.

It includes certificate verification, renewal, deployment, validation, and lifecycle management.

---

# 2. Scope

This instruction applies to X.509 certificates used by infrastructure services, including:

* Kubernetes
* Virtualization platforms
* Storage platforms
* Backup systems
* Web services
* APIs
* Internal services

Platform-specific implementation details shall be documented in separate Work Instructions where applicable.

---

# 3. Prerequisites

Before starting:

* Administrative access to the affected system
* Administrative access to the Certificate Authority (CA) or certificate management platform
* Current certificate information available
* Maintenance window approved (if applicable)
* Backup of the current configuration completed where appropriate

---

# 4. Safety Notes

⚠ Verify the certificate subject and issuer before deployment.

⚠ Ensure that the complete certificate chain is available.

⚠ Never overwrite production certificates without a verified rollback plan.

⚠ Confirm that the renewed certificate has been successfully deployed before removing the previous certificate.

---

# 5. Related Documents

* RB-015 – Renew Certificates
* TS-006 – Certificate Troubleshooting

---

# 6. Procedure

---

## Step 1 – Verify Certificate Status

### Objective

Identify certificates requiring renewal or replacement.

### Actions

Review:

* Certificate validity period
* Expiration date
* Subject information
* Issuer
* Subject Alternative Names (SAN)
* Certificate chain

### Expected Result

Certificates requiring action have been identified.

### Verification

Confirm the certificate details match the affected service.

---

## Step 2 – Obtain the Replacement Certificate

### Objective

Generate or request a replacement certificate.

### Actions

Use the organization's approved Certificate Authority or certificate management process to:

* Generate a new certificate signing request (CSR), where required
* Request or issue the replacement certificate
* Obtain the complete certificate chain

### Expected Result

A valid replacement certificate has been issued.

### Verification

Confirm that the certificate matches the requested subject, SAN entries, and intended usage.

---

## Step 3 – Deploy the Certificate

### Objective

Install the renewed certificate.

### Actions

Deploy the certificate and associated certificate chain to the target system.

Update the service configuration where required.

Restart or reload services if necessary.

### Expected Result

The new certificate has been installed successfully.

### Verification

Confirm that the service presents the new certificate.

---

## Step 4 – Validate Secure Communication

### Objective

Verify that secure communication is functioning correctly.

### Actions

Confirm:

* TLS/SSL connectivity
* Certificate chain validation
* Trust relationship
* Client connectivity
* Service availability

### Expected Result

Secure connections are established successfully without certificate-related errors.

### Verification

Validate connectivity using approved testing tools or monitoring systems.

---

## Step 5 – Final Validation

### Objective

Confirm successful completion of the certificate renewal process.

### Actions

Review:

* Certificate details
* Service status
* Monitoring alerts
* System logs

### Expected Result

The renewed certificate is active and all affected services are operating normally.

### Verification

Confirm that no certificate-related warnings or errors remain.

---

# 7. Rollback

If certificate deployment cannot be completed successfully:

* Restore the previous certificate, provided it is still valid.
* Revert any related configuration changes.
* Restart or reload services as required.
* Verify service availability after rollback.
* Escalate according to organizational procedures if necessary.

---

# 8. Troubleshooting

If issues occur during certificate management, refer to:

* TS-006 – Certificate Troubleshooting

---

# 9. Documentation

Record:

* Date and time
* Affected system or service
* Certificate subject
* Certificate issuer
* Expiration date
* Validation results
* Observed issues
* Related Change Request

---

# 10. References

* RB-015 – Renew Certificates
* TS-006 – Certificate Troubleshooting
* Organization Certificate Management Policy
* Vendor Documentation
