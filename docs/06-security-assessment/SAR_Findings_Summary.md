# Security Assessment Report — Findings Summary
**System Name:** Bundle EHR
**Document Type:** SAR Findings Summary
**Version:** 1.0
**Status:** Final
**Prepared By:** Edward Chibuzo
**Date:** April 28, 2025
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. Purpose
This document provides a standalone summary of all findings
from the Bundle EHR Security Assessment Report (SAR). It is
intended for use by the Authorizing Official (AO) and ISSO
as a quick reference during the authorization decision and
ongoing POA&M reviews.

---

## 2. Assessment Overview

| Field | Detail |
|---|---|
| System | Bundle EHR |
| Assessment Type | Initial Authorization Assessment |
| Control Baseline | NIST SP 800-53 Rev 5 — HIGH |
| Total Controls Assessed | 14 |
| Assessment Date | April 28, 2025 |
| Assessor | Edward Chibuzo |

---

## 3. Results Summary

| Result | Count |
|---|---|
| Satisfied | 8 |
| Other Than Satisfied (OTS) | 6 |
| Not Applicable | 0 |
| **Total** | **14** |

| Finding Risk Level | Count |
|---|---|
| High | 2 |
| Moderate | 4 |
| Low | 0 |
| **Total Findings** | **6** |

---

## 4. Findings — Other Than Satisfied (OTS)

| Finding ID | Control | Title | Risk Level | POA&M Item |
|---|---|---|---|---|
| FINDING-001 | IA-2(2) | MFA not enforced for patient accounts | High | POAM-001 |
| FINDING-002 | SI-2 | Patch management cycle exceeds policy | High | POAM-002 |
| FINDING-003 | IR-4 | Incident Response Plan not tested | Moderate | POAM-003 |
| FINDING-004 | CP-9 | Backup restoration not verified | Moderate | POAM-004 |
| FINDING-005 | AU-2 | Audit log review not formalized | Moderate | POAM-005 |
| FINDING-006 | AC-2 | Account review not completed on schedule | Moderate | POAM-006 |

---

## 5. Finding Details

### FINDING-001 — MFA Not Enforced for Patient Accounts
| Field | Detail |
|---|---|
| **Control** | IA-2(2) |
| **Risk Level** | High |
| **Status** | Other Than Satisfied |
| **Finding** | MFA is configured but set to optional for the Patient user role. Patients can bypass MFA setup during registration leaving patient PHI accounts vulnerable to credential-based attacks. |
| **Evidence** | Authentication Service configuration review showed MFA set to optional for Patient role |
| **Recommendation** | Update Authentication Service to enforce mandatory MFA for all user roles without exception |
| **POA&M** | POAM-001 — Target completion May 28, 2025 |

---

### FINDING-002 — Patch Management Cycle Exceeds Policy
| Field | Detail |
|---|---|
| **Control** | SI-2 |
| **Risk Level** | High |
| **Status** | Other Than Satisfied |
| **Finding** | Two clinician endpoints received critical patches 47 and 52 days after release, exceeding the 30-day policy requirement. No automated alerting exists for patches approaching the deadline. |
| **Evidence** | Patch log review — endpoints EP-004 and EP-007 show delayed patching |
| **Recommendation** | Implement automated patch deployment and configure alerting for patches approaching the 20-day mark |
| **POA&M** | POAM-002 — Target completion May 28, 2025 |

---

### FINDING-003 — Incident Response Plan Not Tested
| Field | Detail |
|---|---|
| **Control** | IR-4 |
| **Risk Level** | Moderate |
| **Status** | Other Than Satisfied |
| **Finding** | Bundle has a documented IRP however no tabletop exercise or functional test has been conducted since the plan was created despite SSP committing to annual testing. |
| **Evidence** | Interview with Security Team lead confirmed no IRP test has been conducted |
| **Recommendation** | Schedule and conduct tabletop exercise within 60 days, update IRP based on lessons learned |
| **POA&M** | POAM-003 — Target completion June 27, 2025 |

---

### FINDING-004 — Backup Restoration Not Verified
| Field | Detail |
|---|---|
| **Control** | CP-9 |
| **Risk Level** | Moderate |
| **Status** | Other Than Satisfied |
| **Finding** | AWS S3 backups are running on schedule however no restoration test has been performed to verify that backup data is complete, uncorrupted, and recoverable within the required timeframe. |
| **Evidence** | Interview with System Administrator confirmed backups have never been test-restored |
| **Recommendation** | Conduct full restoration test in isolated environment, schedule quarterly restoration tests |
| **POA&M** | POAM-004 — Target completion June 27, 2025 |

---

### FINDING-005 — Audit Log Review Not Formalized
| Field | Detail |
|---|---|
| **Control** | AU-2 |
| **Risk Level** | Moderate |
| **Status** | Other Than Satisfied |
| **Finding** | Audit logs are generated and stored correctly however there is no documented schedule, procedure, or assigned responsibility for regular log review. Reviews are conducted ad hoc. |
| **Evidence** | Interview with Security Team — no formal log review schedule exists |
| **Recommendation** | Establish weekly log review schedule, assign responsibility to named Security Team member |
| **POA&M** | POAM-005 — Target completion July 27, 2025 |

---

### FINDING-006 — Account Review Not Completed on Schedule
| Field | Detail |
|---|---|
| **Control** | AC-2 |
| **Risk Level** | Moderate |
| **Status** | Other Than Satisfied |
| **Finding** | Last account review was conducted 5 months ago exceeding the quarterly requirement. Three inactive accounts were identified that should have been disabled per policy. |
| **Evidence** | Account management log review — three accounts show last login over 90 days with no disable action |
| **Recommendation** | Immediately disable inactive accounts, implement automated alerting for accounts inactive over 45 days |
| **POA&M** | POAM-006 — Target completion May 28, 2025 |

---

## 6. Satisfied Controls Summary

| Control | Title | Assessment Result |
|---|---|---|
| AC-3 | Access Enforcement | Satisfied —
