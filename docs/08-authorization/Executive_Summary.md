# Executive Summary — Security Authorization
**System Name:** Bundle EHR
**Document Type:** Executive Summary
**Version:** 1.0
**Status:** Final
**Prepared By:** Edward Chibuzo, ISSO
**Submitted To:** Chief Information Officer (AO)
**Date:** April 28, 2025
**Classification:** Unclassified — For Portfolio Use Only

---

## Overview
Bundle EHR is a hybrid Electronic Health Record Management System
that processes, stores, and transmits Protected Health Information
(PHI) and Personally Identifiable Information (PII) for patients,
clinical staff, and administrative personnel. Following a
comprehensive security assessment conducted in accordance with
the NIST Risk Management Framework (RMF), Bundle EHR is recommended
for Authorization to Operate (ATO) with Conditions.

This document provides a non-technical summary of Bundle's security
posture, key risks, and the conditions required for full
authorization.

---

## What We Did
The Bundle EHR security team completed a full end-to-end RMF
authorization process covering the following activities:

| Activity | Outcome |
|---|---|
| System Categorization | Bundle classified as HIGH impact under FIPS 199 |
| Control Selection | 37 security controls selected from NIST SP 800-53 Rev 5 HIGH baseline |
| Security Plan | Full System Security Plan documented covering all selected controls |
| Risk Assessment | 10 risks identified, rated, and assigned remediation actions |
| Security Assessment | 14 controls tested — 8 fully satisfied, 6 require remediation |
| POA&M | 6 findings tracked with owners, milestones, and target dates |

---

## Where Bundle Stands Today
Bundle EHR has implemented the majority of its required security
controls and has a strong foundation for protecting patient data.
The system enforces multi-factor authentication for clinical and
administrative staff, encrypts all patient data in transit and
at rest, maintains dedicated audit logs for all system activity,
and operates within a defence-in-depth architecture aligned with
NIST and HIPAA requirements.

Six control weaknesses were identified during the assessment.
Two are rated High priority and four are rated Moderate priority.
None of the findings indicate a systemic failure of Bundle's
security program — they reflect gaps in process enforcement and
operational procedures that are actively being addressed.

---

## Key Risks to Be Aware Of

### High Priority — Requires Immediate Action

**1. Patient Account MFA Not Enforced**
Multi-factor authentication is available for patient accounts
but is not currently mandatory. This means a patient whose
password is stolen could have their health records accessed
by an unauthorized person. We are fixing this within 30 days
by making MFA mandatory for all accounts without exception.

**2. Delayed Security Patching on Clinical Devices**
Two clinical workstations received critical security updates
later than our policy requires. Late patching increases the
risk of ransomware and cyberattacks. We are implementing
automated patching tools to ensure all devices are updated
on time going forward.

### Moderate Priority — Being Addressed

- Incident response procedures have not yet been tested through
  a simulated exercise — scheduled within 60 days
- Backup data has not been test-restored to confirm recoverability
  — test scheduled within 60 days
- Audit log reviews are happening but not on a formal documented
  schedule — formal schedule being implemented within 90 days
- User account reviews fell behind schedule — three inactive
  accounts identified and being disabled immediately

---

## What This Means for the Organization

| Area | Status | Notes |
|---|---|---|
| Patient Data Protection | Strong | Encryption, MFA, and access controls in place |
| Regulatory Compliance | On Track | HIPAA controls implemented, gaps being remediated |
| Cyber Threat Readiness | Moderate | Strong perimeter controls, endpoint patching gap being fixed |
| Operational Continuity | Moderate | Backup and recovery procedures being strengthened |
| Audit Readiness | Moderate | Log generation strong, review process being formalized |

---

## Recommendation
Based on the completed assessment, the ISSO recommends the
Authorizing Official grant Bundle EHR an **Authorization to
Operate with Conditions**. The system is sufficiently secure
to begin operations provided the two High priority findings
are remediated within 30 days and all Moderate findings are
resolved within 90 days.

Granting ATO with Conditions is appropriate because:

- The majority of security controls are fully implemented
  and operating as intended
- No evidence of active exploitation or data breach was found
- All findings have clear remediation plans with assigned owners
  and target dates
- Compensating controls are in place that reduce the immediate
  risk of the identified gaps
- Bundle's architecture is well-designed and aligned with
  NIST
