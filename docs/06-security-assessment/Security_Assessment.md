# Security Assessment Plan (SAP) & Security Assessment Report (SAR)
**System Name:** Bundle EHR
**Document Type:** Security Assessment Plan & Report
**Version:** 1.0
**Status:** Draft
**Prepared By:** Edward Chibuzo
**Date:** [04/27/2026]
**Classification:** Unclassified — For Portfolio Use Only

---

# PART 1 — SECURITY ASSESSMENT PLAN (SAP)

## 1. Purpose
This Security Assessment Plan defines the scope, methodology, 
schedule, and procedures for assessing the security controls 
implemented in Bundle EHR. The assessment determines whether 
controls are implemented correctly, operating as intended, and 
producing the desired security outcome.

---

## 2. Assessment Scope

| Item | Detail |
|---|---|
| System | Bundle EHR |
| Assessment Type | Initial Authorization Assessment |
| Control Baseline | NIST SP 800-53 Rev 5 — HIGH |
| Controls to Assess | 13 controls selected from SSP |
| Assessment Period | [Start Date] — [End Date] |
| Assessor | Edward Chibuzo (ISSO) |

---

## 3. Assessment Methods

Each control will be assessed using one or more of the following 
methods as defined in NIST SP 800-53A:

| Method | Description |
|---|---|
| Examine | Review documentation, policies, configurations, and logs |
| Interview | Discuss control implementation with system owners and staff |
| Test | Directly test the control through technical means |

---

## 4. Controls to Be Assessed

| Control | Title | Assessment Method |
|---|---|---|
| AC-2 | Account Management | Examine, Interview |
| AC-3 | Access Enforcement | Examine, Test |
| AC-6 | Least Privilege | Examine, Interview |
| AU-2 | Event Logging | Examine, Test |
| AU-9 | Protection of Audit Information | Examine, Test |
| IA-2 | Identification & Authentication | Examine, Test |
| IA-2(1) | MFA — Privileged Accounts | Test |
| IA-2(2) | MFA — Non-Privileged Accounts | Test |
| SC-8 | Transmission Confidentiality | Examine, Test |
| SC-28 | Protection of Information at Rest | Examine |
| IR-4 | Incident Handling | Examine, Interview |
| IR-6 | Incident Reporting | Examine, Interview |
| SI-2 | Flaw Remediation | Examine, Interview |
| SI-3 | Malware Protection | Examine, Test |

---

## 5. Assessment Schedule

| Phase | Activity | Target Date |
|---|---|---|
| Preparation | Review SSP and control documentation | Week 1 |
| Assessment | Examine, interview, and test controls | Week 2-3 |
| Analysis | Analyze findings and assign risk ratings | Week 4 |
| Reporting | Draft and finalize SAR | Week 5 |
| Remediation | Hand off findings to POA&M | Week 6 |

---

## 6. Rules of Engagement

- Assessment is conducted in a simulated environment only
- No real PHI or PII will be accessed or tested
- Testing will not disrupt system availability
- All findings are treated as confidential

---

# PART 2 — SECURITY ASSESSMENT REPORT (SAR)

## 1. Purpose
This Security Assessment Report documents the findings from the 
Bundle EHR security control assessment. Each control is rated as 
Satisfied, Other Than Satisfied (OTS), or Not Applicable (NA). 
All OTS findings are forwarded to the POA&M for remediation tracking.

---

## 2. Finding Risk Ratings

| Rating | Description |
|---|---|
| High | Control failure could directly result in serious harm to PHI/PII |
| Moderate | Control weakness exists but compensating controls reduce impact |
| Low | Minor gap with negligible impact on overall security posture |

---

## 3. Assessment Findings

### FINDING-001 — MFA Not Enforced for All Non-Privileged Accounts
| Field | Detail |
|---|---|
| **Control** | IA-2(2) |
| **Status** | Other Than Satisfied (OTS) |
| **Finding** | MFA is configured in the Authentication Service but is not enforced as mandatory for patient accounts. Patients can bypass MFA setup during registration. |
| **Risk Rating** | High |
| **Evidence** | Authentication Service configuration review showed MFA set to optional for the Patient user role |
| **Recommendation** | Update Authentication Service configuration to enforce MFA for all user roles without exception |
| **POA&M Item** | Yes — POAM-001 |

---

### FINDING-002 — Patch Management Cycle Exceeds Policy
| Field | Detail |
|---|---|
| **Control** | SI-2 |
| **Status** | Other Than Satisfied (OTS) |
| **Finding** | SSP states critical vulnerabilities must be patched within 30 days. Review of patch logs shows two critical patches on clinician endpoints were applied 47 and 52 days after release respectively. |
| **Risk Rating** | High |
| **Evidence** | Patch log review — endpoints EP-004 and EP-007 show delayed patching dates |
| **Recommendation** | Implement automated patch deployment for critical patches, set alerting for patches approaching the 30-day deadline |
| **POA&M Item** | Yes — POAM-002 |

---

### FINDING-003 — Incident Response Plan Not Tested
| Field | Detail |
|---|---|
| **Control** | IR-4 |
| **Status** | Other Than Satisfied (OTS) |
| **Finding** | Bundle has a documented Incident Response Plan, however no tabletop exercise or test has been conducted since the plan was created. SSP states the IRP is tested annually. |
| **Risk Rating** | Moderate |
| **Evidence** | Interview with Security Team lead confirmed no IRP test has been conducted |
| **Recommendation** | Schedule and conduct a tabletop exercise within 60 days, document results and update IRP based on lessons learned |
| **POA&M Item** | Yes — POAM-003 |

---

### FINDING-004 — Backup Restoration Not Verified
| Field | Detail |
|---|---|
| **Control** | CP-9 |
| **Status** | Other Than Satisfied (OTS) |
| **Finding** | AWS S3 backups are running successfully however no restoration test has been performed to verify that backups are complete and recoverable. |
| **Risk Rating** | Moderate |
| **Evidence** | Interview with System Administrator confirmed backups have never been test-restored |
| **Recommendation** | Conduct quarterly backup restoration tests, document results and store in the contingency planning file |
| **POA&M Item** | Yes — POAM-004 |

---

### FINDING-005 — Audit Log Review Not Formalized
| Field | Detail |
|---|---|
| **Control** | AU-2 |
| **Status** | Other Than Satisfied (OTS) |
| **Finding** | Audit logs are being generated and
