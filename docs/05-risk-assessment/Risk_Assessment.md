# Risk Assessment & Risk Register
**System Name:** Bundle EHR  
**Document Type:** Risk Assessment  
**Version:** 1.0  
**Status:** Draft  
**Prepared By:** Edward Chibuzo  
**Date:** [04/27/2026]  
**Methodology:** NIST SP 800-30 Rev 1

---

## 1. Purpose
This document identifies, analyzes, and prioritizes risks to Bundle 
EHR based on NIST SP 800-30 Rev 1 (Guide for Conducting Risk 
Assessments). The goal is to provide the Authorizing Official (AO) 
with a clear picture of Bundle's threat landscape and the residual 
risk after controls are applied.

---

## 2. Risk Assessment Methodology

### 2.1 Likelihood Ratings
| Rating | Score | Description |
|---|---|---|
| High | 3 | Threat is likely to occur within the next 12 months |
| Moderate | 2 | Threat may occur within the next 12 months |
| Low | 1 | Threat is unlikely to occur within the next 12 months |

### 2.2 Impact Ratings
| Rating | Score | Description |
|---|---|---|
| High | 3 | Severe harm to individuals, operations, or organization |
| Moderate | 2 | Significant harm but recoverable with effort |
| Low | 1 | Minor harm with minimal operational disruption |

### 2.3 Risk Score Calculation
Risk Score = Likelihood Score × Impact Score

| Risk Score | Risk Level |
|---|---|
| 7 — 9 | High |
| 4 — 6 | Moderate |
| 1 — 3 | Low |

---

## 3. Threat Identification

Bundle EHR faces threats across four categories based on its 
hybrid healthcare environment:

| Threat Category | Examples |
|---|---|
| Cyber Threats | Ransomware, phishing, unauthorized access |
| Insider Threats | Data theft, accidental disclosure, privilege abuse |
| Physical Threats | Unauthorized physical access, hardware theft |
| Environmental Threats | Power failure, natural disaster, hardware failure |

---

## 4. Risk Register

### RISK-001 — Ransomware Attack
| Field | Detail |
|---|---|
| **Threat Source** | External malicious actor |
| **Threat Event** | Ransomware deployed via phishing email to clinician endpoint |
| **Vulnerability** | Clinician endpoints may have unpatched software |
| **Likelihood** | High (3) |
| **Impact** | High (3) |
| **Risk Score** | 9 — High |
| **Current Controls** | EDR on endpoints, AWS WAF, SI-2 patch management |
| **Residual Risk** | Moderate — controls reduce but do not eliminate risk |
| **Recommended Action** | Enforce mandatory phishing awareness training, accelerate patch cycle to 14 days for critical patches |

---

### RISK-002 — Unauthorized PHI Access
| Field | Detail |
|---|---|
| **Threat Source** | External attacker or unauthorized internal user |
| **Threat Event** | Attacker gains access to patient records through compromised credentials |
| **Vulnerability** | Weak or reused passwords, lack of MFA enforcement |
| **Likelihood** | High (3) |
| **Impact** | High (3) |
| **Risk Score** | 9 — High |
| **Current Controls** | IA-2 MFA enforcement, AC-2 account management, AC-3 RBAC |
| **Residual Risk** | Moderate — MFA significantly reduces risk |
| **Recommended Action** | Implement continuous authentication monitoring, alert on anomalous access patterns |

---

### RISK-003 — Insider Threat — Data Theft
| Field | Detail |
|---|---|
| **Threat Source** | Malicious or disgruntled employee |
| **Threat Event** | Privileged user exfiltrates PHI records to external storage |
| **Vulnerability** | Excessive access privileges, lack of data loss prevention controls |
| **Likelihood** | Moderate (2) |
| **Impact** | High (3) |
| **Risk Score** | 6 — Moderate |
| **Current Controls** | AU-2 event logging, AC-6 least privilege, AU-9 log protection |
| **Residual Risk** | Moderate — logging detects but does not prevent exfiltration |
| **Recommended Action** | Implement Data Loss Prevention (DLP) tool, block USB storage on clinical endpoints |

---

### RISK-004 — Database Server Compromise
| Field | Detail |
|---|---|
| **Threat Source** | External attacker |
| **Threat Event** | Attacker exploits vulnerability in on-premises database to extract PHI |
| **Vulnerability** | Unpatched database software, misconfigured access controls |
| **Likelihood** | Moderate (2) |
| **Impact** | High (3) |
| **Risk Score** | 6 — Moderate |
| **Current Controls** | SC-28 encryption at rest, AC-3 access enforcement, SI-2 flaw remediation |
| **Residual Risk** | Low-Moderate — encryption limits impact even if access is gained |
| **Recommended Action** | Conduct quarterly database vulnerability scans, enforce database activity monitoring |

---

### RISK-005 — VPN Tunnel Failure
| Field | Detail |
|---|---|
| **Threat Source** | Technical failure or misconfiguration |
| **Threat Event** | IPSec VPN between AWS and on-premises environment fails, disrupting access to database and audit logs |
| **Vulnerability** | Single VPN tunnel without redundancy |
| **Likelihood** | Moderate (2) |
| **Impact** | High (3) |
| **Risk Score** | 6 — Moderate |
| **Current Controls** | SC-8(1) IPSec VPN, CP contingency planning |
| **Residual Risk** | Moderate — no redundant tunnel currently in place |
| **Recommended Action** | Implement redundant VPN tunnel, define RTO/RPO for VPN failure scenario |

---

### RISK-006 — Phishing Attack on Clinical Staff
| Field | Detail |
|---|---|
| **Threat Source** | External malicious actor |
| **Threat Event** | Clinical staff member clicks malicious link, credentials harvested |
| **Vulnerability** | Lack of security awareness training, no email filtering |
| **Likelihood** | High (3) |
| **Impact** | Moderate (2) |
| **Risk Score** | 6 — Moderate |
| **Current Controls** | MFA limits impact of credential theft, AWS WAF |
| **Residual Risk** | Low-Moderate — MFA prevents full account takeover |
| **Recommended Action** | Deploy email filtering, conduct quarterly phishing simulation exercises |

---

### RISK-007 — Accidental PHI Disclosure
| Field | Detail |
|---|---|
| **Threat Source** | Internal — unintentional staff error |
| **Threat Event** | Staff member sends PHI to wrong recipient via email or messaging |
| **Vulnerability** | No outbound email DLP controls, lack of staff training |
| **Likelihood** | Moderate (2) |
| **Impact** | Moderate (2) |
| **Risk Score** | 4 — Moderate |
| **Current Controls** | AU-2 logging, IR-6 breach notification procedures |
| **Residual Risk** | Moderate — controls address response but not prevention |
| **Recommended Action** | Implement outbound email DLP, mandatory annual HIPAA training |

---

### RISK-008 — Backup Failure
| Field | Detail |
|---|---|
| **Threat Source** | Technical failure |
| **Threat Event** | AWS S3 backup process fails silently, leaving Bundle without a viable recovery point |
| **Vulnerability** | Backup integrity not verified regularly |
| **Likelihood** | Low (1) |
| **Impact** | High (3) |
| **Risk Score** | 3 — Low |
| **Current Controls** | CP contingency planning, AWS S3 redundancy |
| **Residual Risk** | Low — AWS S3 provides high durability |
| **Recommended Action** | Implement automated backup verification and alerting, test restoration quarterly |

---

### RISK-009 — Physical Unauthorized Access
| Field | Detail |
|---|---|
| **Threat Source** | External intruder or unauthorized personnel |
| **Threat Event** | Unauthorized individual gains physical access to on-premises server room |
| **Vulnerability** | Weak physical access controls at server room |
| **Likelihood** | Low (1) |
| **Impact** | High (3) |
| **Risk Score** | 3 — Low |
| **Current Controls** | PE-3 physical access controls, AU-2 logging |
| **Residual Risk** | Low — physical controls and logging reduce risk significantly |
| **Recommended Action** | Install badge access and CCTV at server room, conduct annual physical security audit |

---

### RISK-010 — Audit Log Tampering
| Field | Detail |
|---|---|
| **Threat Source** | Malicious insider — privileged user |
| **Threat Event** | System Administrator attempts to delete or modify audit logs to conceal activity |
| **Vulnerability** | Admin accounts have excessive access to logging infrastructure |
| **Likelihood** | Low (1) |
| **Impact** | High (3) |
| **Risk Score** | 3 — Low |
| **Current Controls** | AU-9 log protection, separation of duties |
| **Residual Risk** | Low — AU-9 prevents log modification by design |
| **Recommended Action** | Implement immutable log storage, send logs to SIEM for independent monitoring |

---

## 5. Risk Summary

| Risk ID | Risk Title | Likelihood | Impact | Score | Level |
|---|---|---|---|---|---|
| RISK-001 | Ransomware Attack | High | High | 9 | High |
| RISK-002 | Unauthorized PHI Access | High | High | 9 | High |
| RISK-003 | Insider Threat — Data Theft | Moderate | High | 6 | Moderate |
| RISK-004 | Database Server Compromise | Moderate | High | 6 | Moderate |
| RISK-005 | VPN Tunnel Failure | Moderate | High | 6 | Moderate |
| RISK-006 | Phishing Attack | High | Moderate | 6 | Moderate |
| RISK-007 | Accidental PHI Disclosure | Moderate | Moderate | 4 | Moderate |
| RISK-008 | Backup Failure | Low | High | 3 | Low |
| RISK-009 | Physical Unauthorized Access | Low | High | 3 | Low |
| RISK-010 | Audit Log Tampering | Low | High | 3 | Low |

---

## 6. Risk Response Summary

| Risk Level | Count | Response Strategy |
|---|---|---|
| High | 2 | Immediate remediation required before ATO |
| Moderate | 5 | Remediation planned — tracked in POA&M |
| Low | 3 | Accept with monitoring — reviewed annually |

---

## 7. Next Step
All unresolved risks will be tracked in the Plan of Action and 
Milestones (POA&M) document. High risks must be remediated or 
formally accepted by the Authorizing Official prior to ATO.

---

*This document is part of the Bundle EHR simula
