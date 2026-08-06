# TS-006 – Certificate Troubleshooting

**Troubleshooting ID:** TS-006
**Version:** 1.0
**Status:** Approved
**Category:** Security
**Platform:** Public Key Infrastructure (PKI)
**Related Runbook:** RB-015 – Renew Certificates
**Related Work Instruction:** WI-006 – Certificate Management
**Owner:** Platform Operations
**Reviewer:** *To be assigned*
**Last Updated:** 2026-08-06
**Next Review:** 2027-08-06
**Classification:** Public

---

# 1. Purpose

This Troubleshooting Guide provides a structured approach for diagnosing and resolving certificate-related issues affecting enterprise infrastructure and services.

It supports fault isolation, secure service recovery, and validation while maintaining trusted communications.

---

# 2. Scope

This guide applies to:

* Expired certificates
* Invalid certificate chains
* TLS/SSL communication failures
* Certificate deployment issues
* Trust relationship failures
* Certificate validation errors
* Mutual TLS (mTLS) authentication issues
* PKI-related operational incidents

---

# 3. Symptoms

Typical indicators include:

* Certificate expired
* TLS/SSL handshake failure
* Certificate not trusted
* Invalid certificate chain
* Hostname mismatch
* Mutual TLS authentication failure
* Browser or client certificate warnings
* Service unavailable after certificate renewal

---

# 4. Prerequisites

Before troubleshooting:

* Administrative access to the affected system
* Administrative access to the Certificate Authority (CA), if applicable
* Current certificate information available
* Monitoring platform available
* Recent certificate changes reviewed

---

# 5. Diagnostic Procedure

## Step 1 – Verify the Certificate

### Objective

Confirm that the reported certificate issue exists.

### Actions

Review:

* Certificate validity period
* Subject
* Subject Alternative Names (SAN)
* Issuer
* Key usage
* Extended Key Usage (EKU)

### Expected Result

The certificate details have been verified.

---

## Step 2 – Verify the Trust Chain

### Objective

Determine whether the certificate chain is valid.

### Actions

Review:

* Root CA
* Intermediate CA certificates
* Certificate chain completeness
* Trusted certificate store

### Expected Result

The certificate chain has been validated.

---

## Step 3 – Determine the Root Cause

### Actions

Investigate possible causes including:

* Expired certificate
* Incorrect certificate deployment
* Missing intermediate certificate
* Incorrect hostname or SAN
* Certificate authority issues
* Configuration changes
* Client trust configuration
* Recent certificate renewal

### Expected Result

The probable root cause has been identified.

---

## Step 4 – Perform Recovery

### Actions

Execute the appropriate recovery procedure.

Refer to the corresponding Runbook or Work Instruction where applicable.

### Expected Result

Secure communication is restored successfully.

---

## Step 5 – Validate Secure Communication

### Actions

Verify:

* Certificate validity
* Certificate chain
* TLS/SSL communication
* Client connectivity
* Monitoring alerts
* Service availability

### Expected Result

Certificate validation succeeds and secure communication operates normally.

---

# 6. Common Issues

| Symptom                           | Possible Cause                          | Recommended Action                                        |
| --------------------------------- | --------------------------------------- | --------------------------------------------------------- |
| Certificate expired               | Renewal not completed                   | Renew and deploy the certificate                          |
| TLS handshake failure             | Invalid or incomplete certificate chain | Verify the full certificate chain                         |
| Certificate not trusted           | Missing trusted CA                      | Install or update the trusted CA certificates             |
| Hostname mismatch                 | Incorrect Common Name or SAN            | Verify certificate subject information                    |
| Service unavailable after renewal | Configuration or deployment issue       | Review deployment and service configuration               |
| Mutual TLS failure                | Client or server certificate issue      | Validate both certificate chains and trust relationships  |
| Browser security warning          | Untrusted certificate                   | Verify the issuing CA and trust configuration             |
| Authentication failure            | Certificate validation failed           | Review authentication configuration and certificate usage |

---

# 7. Escalation

Escalate when:

* Secure communication cannot be restored.
* Certificate trust cannot be established.
* PKI services are unavailable.
* Multiple critical services are affected.
* Root cause cannot be identified.
* Certificate Authority or vendor support is required.

Document all findings before escalation.

---

# 8. Documentation

Record:

* Date and time
* Affected service
* Certificate subject
* Certificate issuer
* Symptoms observed
* Root cause
* Recovery actions
* Validation results
* Related Incident
* Lessons learned

---

# 9. References

* RB-015 – Renew Certificates
* WI-006 – Certificate Management
* Organization Certificate Management Policy
* Vendor Documentation
