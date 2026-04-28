# Plan of Action & Milestones (POA&M)
**System Name:** Bundle EHR
**Document Type:** Plan of Action & Milestones
**Version:** 1.0
**Status:** Active
**Prepared By:** Edward Chibuzo
**Date:** [02/22/2026]
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. Purpose
This Plan of Action and Milestones (POA&M) documents all security 
control weaknesses and deficiencies identified during the Bundle EHR 
security assessment. Each item includes a remediation plan, responsible 
party, required resources, and target completion date. The POA&M is 
reviewed monthly by the ISSO and reported to the Authorizing Official 
(AO) as part of ongoing authorization maintenance.

---

## 2. POA&M Item Status Definitions

| Status | Description |
|---|---|
| Open | Weakness identified, remediation not yet started |
| In Progress | Remediation actively underway |
| Completed | Remediation fully implemented and verified |
| Accepted Risk | AO has formally accepted the risk without remediation |
| Delayed | Remediation behind schedule — escalation required |

---

## 3. POA&M Summary Dashboard

| Item ID | Weakness | Risk Level | Status | Target Date |
|---|---|---|---|---|
| POAM-001 | MFA not enforced for patient accounts | High | Open | [Date + 30 days] |
| POAM-002 | Patch management cycle exceeds policy | High | In Progress | [Date + 30 days] |
| POAM-003 | Incident Response Plan not tested | Moderate | Open | [Date + 60 days] |
| POAM-004 | Backup restoration not verified | Moderate | Open | [Date + 60 days] |
| POAM-005 | Audit log review not formalized | Moderate | Open | [Date + 90 days] |
| POAM-006 | Account review not completed on schedule | Moderate | In Progress | [Date + 30 days] |

---

## 4. Detailed POA&M Items

---

### POAM-001 — MFA Not Enforced for Patient Accounts

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-001 |
| **Control** | IA-2(2) |
| **Source** | SAR Finding FINDING-001 |
| **Risk Level** | High |
| **Weakness Description** | MFA is configured in the AWS Authentication Service but is set to optional for the Patient user role. Patients can bypass MFA setup during registration, leaving patient accounts vulnerable to credential-based attacks. |
| **Impact if Not Remediated** | Unauthorized access to patient PHI through compromised credentials, HIPAA violation, potential breach notification requirement |
| **Responsible Party** | System Administrator |
| **Milestone 1** | Update Authentication Service configuration to enforce MFA for Patient role — Target: [Date + 7 days] |
| **Milestone 2** | Notify all existing patients of mandatory MFA enrollment — Target: [Date + 14 days] |
| **Milestone 3** | Verify MFA enforcement through test account — Target: [Date + 21 days] |
| **Milestone 4** | Document completion and notify ISSO — Target: [Date + 30 days] |
| **Required Resources** | System Administrator time — estimated 4 hours |
| **Status** | Open |
| **Target Completion Date** | [Date + 30 days] |
| **Completion Date** | Pending |

---

### POAM-002 — Patch Management Cycle Exceeds Policy

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-002 |
| **Control** | SI-2 |
| **Source** | SAR Finding FINDING-002 |
| **Risk Level** | High |
| **Weakness Description** | Two clinician endpoints (EP-004 and EP-007) received critical patches 47 and 52 days after release respectively, exceeding the 30-day policy requirement. The current manual patch process does not include alerting when patches approach the deadline. |
| **Impact if Not Remediated** | Unpatched critical vulnerabilities on clinical endpoints increase risk of exploitation, ransomware, and unauthorized PHI access |
| **Responsible Party** | System Administrator |
| **Milestone 1** | Apply all outstanding critical patches to EP-004 and EP-007 immediately — Target: [Date + 3 days] |
| **Milestone 2** | Implement automated patch deployment tool for all endpoints — Target: [Date + 14 days] |
| **Milestone 3** | Configure alerting for patches approaching 20-day mark — Target: [Date + 21 days] |
| **Milestone 4** | Verify patch compliance across all endpoints and document — Target: [Date + 30 days] |
| **Required Resources** | System Administrator time — estimated 8 hours, patch management tooling |
| **Status** | In Progress |
| **Target Completion Date** | [Date + 30 days] |
| **Completion Date** | Pending |

---

### POAM-003 — Incident Response Plan Not Tested

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-003 |
| **Control** | IR-4 |
| **Source** | SAR Finding FINDING-003 |
| **Risk Level** | Moderate |
| **Weakness Description** | Bundle has a documented Incident Response Plan however no tabletop exercise or functional test has been conducted since the plan was created. The SSP commits to annual IRP testing. |
| **Impact if Not Remediated** | Untested IRP may contain gaps that only surface during a real incident, increasing response time and potential harm to patients and the organization |
| **Responsible Party** | Security Team Lead |
| **Milestone 1** | Schedule tabletop exercise with Security Team and key stakeholders — Target: [Date + 14 days] |
| **Milestone 2** | Conduct tabletop exercise simulating ransomware incident scenario — Target: [Date + 45 days] |
| **Milestone 3** | Document lessons learned and update IRP accordingly — Target: [Date + 55 days] |
| **Milestone 4** | Submit updated IRP to ISSO for review and approval — Target: [Date + 60 days] |
| **Required Resources** | Security Team time — estimated 6 hours for exercise and documentation |
| **Status** | Open |
| **Target Completion Date** | [Date + 60 days] |
| **Completion Date** | Pending |

---

### POAM-004 — Backup Restoration Not Verified

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-004 |
| **Control** | CP-9 |
| **Source** | SAR Finding FINDING-004 |
| **Risk Level** | Moderate |
| **Weakness Description** | AWS S3 backups are running on schedule however no restoration test has been performed to verify that backup data is complete, uncorrupted, and recoverable within the required timeframe. |
| **Impact if Not Remediated** | In the event of a system failure or ransomware attack, backups may be unrecoverable or incomplete, resulting in permanent loss of PHI and operational disruption |
| **Responsible Party** | System Administrator |
| **Milestone 1** | Define restoration test procedure and success criteria — Target: [Date + 14 days] |
| **Milestone 2** | Conduct full restoration test in isolated environment — Target: [Date + 45 days] |
| **Milestone 3** | Document test results including RTO achieved — Target: [Date + 50 days] |
| **Milestone 4** | Schedule quarterly restoration tests going forward — Target: [Date + 60 days] |
| **Required Resources** | System Administrator time — estimated 6 hours, isolated test environment |
| **Status** | Open |
| **Target Completion Date** | [Date + 60 days] |
| **Completion Date** | Pending |

---

### POAM-005 — Audit Log Review Not Formalized

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-005 |
| **Control** | AU-2 |
| **Source** | SAR Finding FINDING-005 |
| **Risk Level** | Moderate |
| **Weakness Description** | Audit logs are being generated and stored correctly on the dedicated Audit Logging Server however there is no documented schedule, procedure, or assigned responsibility for regular log review. Reviews are currently conducted ad hoc. |
| **Impact if Not Remediated** | Security incidents and anomalous activity may go undetected for extended periods due to lack of regular log review, increasing dwell time of potential threats |
| **Responsible Party** | Security Team Lead |
| **Milestone 1** | Draft formal audit log review procedure — Target: [Date + 14 days] |
| **Milestone 2** | Assign log review responsibility to named Security Team member — Target: [Date + 21 days] |
| **Milestone 3** | Implement weekly log review schedule and tracking log — Target: [Date + 30 days] |
| **Milestone 4** | Complete first four weeks of scheduled reviews and verify compliance — Target: [Date + 90 days] |
| **Required Resources** | Security Team time — estimated 2 hours per week |
| **Status** | Open |
| **Target Completion Date** | [Date + 90 days] |
| **Completion Date** | Pending |

---

### POAM-006 — Account Review Not Completed on Schedule

| Field | Detail |
|---|---|
| **POA&M ID** | POAM-006 |
| **Control** | AC-2 |
| **Source** | SAR Finding FINDING-006 |
| **Risk Level** | Moderate |
| **Weakness Description** | The last account review was conducted 5 months ago, exceeding the quarterly review requirement. Three inactive accounts were identified that should have been disabled per policy but remain active. |
| **Impact if Not Remediated** | Inactive accounts represent an attack surface — compromised dormant credentials could provide unauthorized access to Bundle and PHI without triggering normal usage alerts |
| **Responsible Party** | System Administrator |
| **Milestone 1** | Immediately disable the three identified inactive accounts — Target: [Date + 2 days] |
| **Milestone 2** | Conduct full account review across all user roles — Target: [Date + 7 days] |
| **Milestone 3** | Implement automated alerting for accounts inactive over 45 days — Target: [Date + 21 days] |
| **Milestone 4** | Schedule and conduct next quarterly account review — Target: [Date + 30 days] |
| **Required Resources** | System Administrator time — estimated 3 hours |
| **Status** | In Progress |
| **Target Completion Date** | [Date + 30 days] |
| **Completion Date** | Pending |

---

## 5. Remediation Priority Matrix

| Priority | POA&M Items | Rationale |
|---|---|---|
| Immediate — within 7 days | POAM-006 (disable inactive accounts) | Active accounts represent live attack surface |
| High — within 30 days | POAM-001, POAM-002 | High risk findings — required before ATO |
| Moderate — within 60 days | POAM-003, POAM-004 | Moderate risk — tracked post-authorization |
| Standard — within 90 days | POAM-005 | Procedural gap — low immediate threat |

---

## 6. POA&M Review Schedule

| Review Frequency | Reviewer | Purpose |
|---|---|---|
| Monthly | ISSO | Review status updates and milestone progress |
| Quarterly | AO | Review overall risk posture and accept/reject delays |
| Annually | Security Team | Full POA&M audit and closure verification |

---

## 7. Next Step
Upon remediation of High findings POAM-001 and POAM-002, the 
Authorization package will be compiled and submitted to the 
Authorizing Official for review and ATO decision.

---

*This document is part of the Bundle EHR simulated RMF authorization 
package. All data and scenarios are fictional and for portfolio use only.*
