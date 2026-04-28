# Authorization to Operate (ATO) Memo
**System Name:** Bundle EHR
**Document Type:** Authorization Decision Memo
**Version:** 1.0
**Status:** Draft
**Prepared By:** Edward Chibuzo, ISSO
**Submitted To:** Chief Information Officer (AO)
**Date:** [04/27/2026]
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. Purpose
This memorandum presents the authorization recommendation for 
Bundle EHR to the Authorizing Official (AO). It summarizes the 
system's security posture, outstanding risks, and the ISSO's 
recommendation for authorization based on the completed RMF 
assessment activities.

---

## 2. System Overview

| Field | Detail |
|---|---|
| System Name | Bundle EHR |
| System Type | Major Application |
| Operating Environment | Hybrid (AWS Cloud + On-Premises) |
| Data Processed | PHI, PII, Billing Data, Clinical Notes |
| FIPS 199 Categorization | High |
| Control Baseline | NIST SP 800-53 Rev 5 — HIGH |
| HIPAA Applicability | Yes |

---

## 3. Authorization Package Summary

The following documents comprise the complete Bundle EHR 
authorization package submitted for AO review:

| Document | Status |
|---|---|
| System Security Plan (SSP) | Complete |
| FIPS 199 Categorization | Complete |
| Control Selection & Tailoring | Complete |
| Risk Assessment & Risk Register | Complete |
| Security Assessment Plan (SAP) | Complete |
| Security Assessment Report (SAR) | Complete |
| Plan of Action & Milestones (POA&M) | Active |

---

## 4. Assessment Results Summary

Bundle EHR's security controls were assessed against the NIST SP 
800-53 Rev 5 HIGH baseline. The following results were recorded:

| Result | Count |
|---|---|
| Controls Satisfied | 8 |
| Controls Other Than Satisfied (OTS) | 6 |
| Total Controls Assessed | 14 |

| Finding Risk Level | Count |
|---|---|
| High | 2 |
| Moderate | 4 |
| Low | 0 |

---

## 5. Outstanding Risks

### High Risk Findings

**POAM-001 — MFA Not Enforced for Patient Accounts**
MFA is configured but not enforced as mandatory for the Patient 
user role. This represents a direct risk to PHI confidentiality. 
Remediation is in progress with a target completion date of 
[Date + 30 days].

**POAM-002 — Patch Management Cycle Exceeds Policy**
Two clinician endpoints received critical patches outside the 
30-day policy window. Automated patch deployment is being 
implemented with a target completion date of [Date + 30 days].

### Moderate Risk Findings
Four moderate findings related to IRP testing, backup restoration 
verification, audit log review formalization, and account review 
scheduling are documented in the POA&M with target completion 
dates ranging from 30 to 90 days.

---

## 6. Residual Risk Statement
After applying all implemented security controls, the residual 
risk to Bundle EHR is assessed as **Moderate**. The two High 
findings are actively being remediated and compensating controls 
are in place. The four Moderate findings represent procedural 
gaps rather than technical vulnerabilities and do not present 
immediate risk to PHI confidentiality or system availability.

---

## 7. ISSO Recommendation

Based on the completed assessment activities, implemented controls, 
and active remediation of identified weaknesses, the ISSO recommends 
an **Authorization to Operate with Conditions** for Bundle EHR.

**Conditions of Authorization:**

| Condition | Requirement | Deadline |
|---|---|---|
| Condition 1 | Remediate POAM-001 — enforce MFA for all patient accounts | [Date + 30 days] |
| Condition 2 | Remediate POAM-002 — implement automated patch management | [Date + 30 days] |
| Condition 3 | Complete all Moderate POA&M items | [Date + 90 days] |
| Condition 4 | Submit monthly POA&M status reports to AO | Ongoing |
| Condition 5 | Conduct annual security assessment | [Date + 1 year] |

---

## 8. Authorization Decision

*To be completed by the Authorizing Official*

| Field | Detail |
|---|---|
| **Authorization Decision** | ☐ Full ATO &nbsp;&nbsp; ☑ ATO with Conditions &nbsp;&nbsp; ☐ Denial |
| **Authorization Date** | [Date] |
| **Authorization Expiration** | [Date + 3 years] |
| **Authorizing Official** | Chief Information Officer |
| **AO Signature** | [Signature] |
| **Comments** | Authorization granted contingent on remediation of all conditions outlined above. Monthly POA&M reports required. |

---

## 9. Authorization Boundary Confirmation
The authorization boundary for Bundle EHR is defined in the 
Architecture Diagram and System Security Plan. This authorization 
covers all components within the defined boundary including AWS 
cloud components and on-premises infrastructure. AWS physical 
infrastructure remains outside the authorization boundary per 
the AWS Shared Responsibility Model.

---

## 10. Next Step
Following ATO issuance, Bundle EHR will transition to the 
Continuous Monitoring phase. The ISSO will maintain the POA&M, 
conduct ongoing control assessments, and report security status 
to the AO on a monthly basis.

---

*This document is part of the Bundle EHR simulated RMF authorization 
package. All data and scenarios are fictional and for portfolio use only.*
