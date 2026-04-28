# Risk Register
**System Name:** Bundle EHR
**Document Type:** Risk Register
**Version:** 1.0
**Status:** Active
**Prepared By:** Edward Chibuzo
**Date:** April 28, 2025
**Methodology:** NIST SP 800-30 Rev 1

---

## 1. Purpose
This Risk Register is a standalone reference document extracted
from the Bundle EHR Risk Assessment. It provides a consolidated
view of all identified risks, their ratings, current controls,
and recommended actions for use by the ISSO and Authorizing
Official during authorization and continuous monitoring.

---

## 2. Risk Rating Scale

| Likelihood | Impact | Risk Score | Risk Level |
|---|---|---|---|
| High (3) | High (3) | 9 | High |
| High (3) | Moderate (2) | 6 | Moderate |
| Moderate (2) | High (3) | 6 | Moderate |
| Moderate (2) | Moderate (2) | 4 | Moderate |
| Low (1) | High (3) | 3 | Low |
| Low (1) | Moderate (2) | 2 | Low |
| Low (1) | Low (1) | 1 | Low |

---

## 3. Risk Register

| Risk ID | Risk Title | Threat Source | Likelihood | Impact | Score | Level | Current Controls | Recommended Action | Status |
|---|---|---|---|---|---|---|---|---|---|
| RISK-001 | Ransomware Attack | External attacker | High | High | 9 | High | EDR, AWS WAF, SI-2 | Mandatory phishing training, accelerate patch cycle to 14 days | Open |
| RISK-002 | Unauthorized PHI Access | External attacker | High | High | 9 | High | IA-2 MFA, AC-2, AC-3 RBAC | Continuous authentication monitoring, anomalous access alerting | Open |
| RISK-003 | Insider Threat — Data Theft | Malicious employee | Moderate | High | 6 | Moderate | AU-2 logging, AC-6, AU-9 | Implement DLP tool, block USB storage on endpoints | Open |
| RISK-004 | Database Server Compromise | External attacker | Moderate | High | 6 | Moderate | SC-28 encryption, AC-3, SI-2 | Quarterly database vulnerability scans, database activity monitoring | Open |
| RISK-005 | VPN Tunnel Failure | Technical failure | Moderate | High | 6 | Moderate | SC-8(1) IPSec VPN, CP | Implement redundant VPN tunnel, define RTO/RPO | Open |
| RISK-006 | Phishing Attack | External attacker | High | Moderate | 6 | Moderate | MFA, AWS WAF | Deploy email filtering, quarterly phishing simulations | Open |
| RISK-007 | Accidental PHI Disclosure | Internal — staff error | Moderate | Moderate | 4 | Moderate | AU-2 logging, IR-6 | Outbound email DLP, mandatory annual HIPAA training | Open |
| RISK-008 | Backup Failure | Technical failure | Low | High | 3 | Low | CP, AWS S3 redundancy | Automated backup verification, quarterly restoration tests | Open |
| RISK-009 | Physical Unauthorized Access | External intruder | Low | High | 3 | Low | PE-3, AU-2 logging | Badge access and CCTV at server room, annual physical security audit | Open |
| RISK-010 | Audit Log Tampering | Malicious insider | Low | High | 3 | Low | AU-9 log protection | Immutable log storage, SIEM integration | Open |

---

## 4. Risk Summary

| Risk Level | Count | Response Strategy |
|---|---|---|
| High | 2 | Immediate remediation required before ATO |
| Moderate | 5 | Remediation planned — tracked in POA&M |
| Low | 3 | Accept with monitoring — reviewed annually |
| **Total** | **10** | |

---

## 5. High Risk Items — Priority Action Required

### RISK-001 — Ransomware Attack
Ransomware deployed via phishing to a clinician endpoint
represents the highest operational risk to Bundle. A successful
attack could encrypt PHI stored on-premises, trigger HIPAA
breach notification requirements, and cause extended system
unavailability. Immediate actions include mandatory phishing
awareness training for all clinical staff and reduction of the
critical patch cycle from 30 to 14 days.

### RISK-002 — Unauthorized PHI Access
Compromised credentials remain the most common attack vector
against healthcare systems. While MFA is enforced for most
user roles, the gap in patient account MFA enforcement
(POAM-001) represents a direct pathway to unauthorized PHI
access. This risk drives the High priority rating of POAM-001
in the POA&M.

---

## 6. Risk Register Review Schedule

| Review Frequency | Reviewer | Purpose |
|---|---|---|
| Monthly | ISSO | Review status of High and Moderate risks |
| Quarterly | Security Team | Full risk register review and update |
| Annually | AO | Risk acceptance decisions and re-authorization input |

---

## 7. Risk Acceptance Statement
Risks rated Low (RISK-008, RISK-009, RISK-010) are formally
accepted by the ISSO pending AO review. These risks will be
monitored on a quarterly basis through the continuous monitoring
program and escalated if likelihood or impact ratings change.

---

*This document is part of the Bundle EHR simulated RMF authorization
package. All data and scenarios are fictional and for portfolio use only.*
