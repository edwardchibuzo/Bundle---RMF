# Continuous Monitoring Strategy
**System Name:** Bundle EHR
**Document Type:** Continuous Monitoring Strategy
**Version:** 1.0
**Status:** Active
**Prepared By:** Edward Chibuzo
**Date:** [04/27/2026]
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. Purpose
This Continuous Monitoring Strategy defines how Bundle EHR will 
maintain ongoing awareness of its security posture following 
Authorization to Operate (ATO). Continuous monitoring ensures 
that security controls remain effective over time, that new 
risks are identified promptly, and that the Authorizing Official 
(AO) receives regular updates on Bundle's security status.

This strategy aligns with NIST SP 800-137 (Information Security 
Continuous Monitoring) and supports Bundle's HIPAA compliance 
obligations.

---

## 2. Continuous Monitoring Objectives

| Objective | Description |
|---|---|
| Control Effectiveness | Verify that implemented controls continue to operate as intended |
| Change Management | Assess security impact of system changes before implementation |
| Vulnerability Management | Identify and remediate new vulnerabilities on a defined schedule |
| Incident Detection | Detect and respond to security incidents in a timely manner |
| POA&M Tracking | Monitor remediation progress and report status to the AO |
| Compliance Maintenance | Ensure ongoing alignment with HIPAA and NIST requirements |

---

## 3. Monitoring Frequency Schedule

### 3.1 Continuous (Automated — Daily)
| Activity | Tool / Method | Responsible Party |
|---|---|---|
| Audit log generation | Audit Logging Server | Automated |
| Malware scanning | EDR on all endpoints | Automated |
| Failed login attempt monitoring | Authentication Service | Automated |
| AWS WAF threat monitoring | AWS WAF Dashboard | Automated |
| Backup job completion verification | AWS Backup | Automated |

### 3.2 Weekly
| Activity | Tool / Method | Responsible Party |
|---|---|---|
| Audit log review | Audit Logging Server | Security Team |
| Failed login report review | Authentication Service | Security Team |
| POA&M status check | POA&M Tracker | ISSO |
| Patch status review | Patch Management Tool | System Administrator |

### 3.3 Monthly
| Activity | Tool / Method | Responsible Party |
|---|---|---|
| Vulnerability scan — all components | Vulnerability Scanner | Security Team |
| Account review — inactive accounts | Authentication Service | System Administrator |
| POA&M status report to AO | POA&M Tracker | ISSO |
| Security metrics report | Power BI Dashboard | ISSO |
| Incident log review | Incident Log | Security Team Lead |

### 3.4 Quarterly
| Activity | Tool / Method | Responsible Party |
|---|---|---|
| Full account access review | Authentication Service | System Administrator |
| Backup restoration test | AWS S3 + Test Environment | System Administrator |
| Control effectiveness review — high priority controls | SSP + Assessment Records | ISSO |
| Configuration baseline review | CM Tool | System Administrator |
| Third party / vendor risk review | Vendor Risk Register | ISSO |

### 3.5 Annually
| Activity | Tool / Method | Responsible Party |
|---|---|---|
| Full security control assessment | NIST SP 800-53A | ISSO + Security Team |
| Incident Response Plan tabletop exercise | IRP | Security Team Lead |
| SSP review and update | SSP Document | ISSO |
| Risk assessment update | Risk Register | ISSO |
| HIPAA Security Rule compliance review | HIPAA Checklist | ISSO |
| Authorization renewal decision | ATO Memo | AO |

---

## 4. Security Metrics

The following metrics will be tracked monthly and reported to 
the AO as part of the ongoing authorization maintenance:

| Metric | Target | Reporting Frequency |
|---|---|---|
| Critical patch compliance rate | 100% within 30 days | Monthly |
| Open High POA&M items | 0 | Monthly |
| Open Moderate POA&M items | Decreasing trend | Monthly |
| Failed login attempts — threshold breaches | 0 unreviewed | Monthly |
| Account review completion | 100% quarterly | Quarterly |
| Backup restoration success rate | 100% | Quarterly |
| Security incidents — mean time to detect | Under 24 hours | Monthly |
| Security incidents — mean time to respond | Under 4 hours | Monthly |

---

## 5. Change Management Process

All changes to Bundle EHR must be assessed for security impact 
before implementation. The following change types require a 
formal security impact analysis:

| Change Type | Security Impact Analysis Required | Approver |
|---|---|---|
| New system component added | Yes | ISSO + AO |
| New user role created | Yes | ISSO |
| Network configuration change | Yes | ISSO + System Admin |
| Third party vendor added | Yes | ISSO + AO |
| Software upgrade — major version | Yes | ISSO |
| Software patch — critical | No — expedited approval | System Admin |
| Policy or procedure update | Yes | ISSO |

Changes that significantly alter the authorization boundary or 
security posture require a formal re-authorization review by 
the AO before implementation.

---

## 6. Incident Response Integration

Continuous monitoring activities feed directly into the incident 
response process. The following thresholds automatically trigger 
incident response procedures:

| Trigger | Threshold | Response |
|---|---|---|
| Failed login attempts | 5 consecutive failures on any account | Account lockou
