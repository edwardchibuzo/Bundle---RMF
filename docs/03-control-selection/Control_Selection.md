# Security Control Selection & Tailoring
**System Name:** Bundle EHR  
**Document Type:** Control Selection  
**Version:** 1.0  
**Status:** Draft  
**Prepared By:** Edward Chibuzo  
**Date:** [04/27/2026]  
**Baseline:** NIST SP 800-53 Rev 5 — HIGH Impact

---

## 1. Purpose
This document identifies the security controls selected for Bundle EHR 
based on its FIPS 199 High impact categorization. Controls are drawn 
from the HIGH baseline of NIST SP 800-53 Rev 5 and tailored to reflect 
Bundle's hybrid (AWS + On-Premises) healthcare environment.

---

## 2. Control Selection Approach

| Step | Action |
|---|---|
| 1 | Start with NIST SP 800-53 Rev 5 HIGH baseline |
| 2 | Review each control family for applicability to Bundle |
| 3 | Tailor out controls not applicable to Bundle's environment |
| 4 | Document rationale for any tailoring decisions |
| 5 | Cross-reference with HIPAA Security Rule requirements |

---

## 3. Selected Control Families

| Control Family | Family Code | Rationale |
|---|---|---|
| Access Control | AC | Bundle manages PHI/PII — strict access control is critical |
| Audit & Accountability | AU | HIPAA requires audit logs of all PHI access |
| Configuration Management | CM | Hybrid environment requires hardened configurations |
| Contingency Planning | CP | Healthcare availability requirements demand DR planning |
| Identification & Authentication | IA | Multi-factor authentication required for PHI access |
| Incident Response | IR | HIPAA Breach Notification Rule requires IR capability |
| Maintenance | MA | On-premise components require controlled maintenance |
| Media Protection | MP | PHI stored on-prem requires physical media controls |
| Personnel Security | PS | Insider threat risk in healthcare environment |
| Physical & Environmental | PE | On-premise database and audit server require physical security |
| Planning | PL | SSP and security planning documentation required |
| Risk Assessment | RA | NIST RMF requires formal risk assessment |
| System & Communications Protection | SC | IPSec VPN and encryption of PHI in transit |
| System & Information Integrity | SI | Malware protection and integrity monitoring required |
| System & Services Acquisition | SA | Third-party vendor risk management (AWS) |

---

## 4. Key Controls Selected

### Access Control (AC)
| Control | Title | Implementation Notes |
|---|---|---|
| AC-2 | Account Management | Role-based accounts for all 7 user types |
| AC-3 | Access Enforcement | RBAC enforced at application and database layer |
| AC-6 | Least Privilege | Users granted minimum access required for their role |
| AC-17 | Remote Access | VPN required for all remote administrative access |

### Audit & Accountability (AU)
| Control | Title | Implementation Notes |
|---|---|---|
| AU-2 | Event Logging | All PHI access, modifications, and deletions logged |
| AU-3 | Content of Audit Records | Logs capture user ID, timestamp, action, and outcome |
| AU-9 | Protection of Audit Information | Audit logs stored on separate on-prem server |
| AU-12 | Audit Record Generation | All system components generate audit records |

### Identification & Authentication (IA)
| Control | Title | Implementation Notes |
|---|---|---|
| IA-2 | User Identification & Authentication | Unique IDs required for all users |
| IA-2(1) | MFA for Privileged Accounts | MFA enforced for admins and security team |
| IA-2(2) | MFA for Non-Privileged Accounts | MFA enforced for all clinical staff |
| IA-5 | Authenticator Management | Password policy enforced — complexity, expiry, history |

### System & Communications Protection (SC)
| Control | Title | Implementation Notes |
|---|---|---|
| SC-8 | Transmission Confidentiality | TLS 1.2+ for all data in transit |
| SC-8(1) | Cryptographic Protection | IPSec VPN for AWS to On-Prem communication |
| SC-28 | Protection of Information at Rest | AES-256 encryption for database and backups |
| SC-5 | Denial of Service Protection | AWS WAF deployed at perimeter |

### Incident Response (IR)
| Control | Title | Implementation Notes |
|---|---|---|
| IR-1 | Policy and Procedures | IR policy documented and approved |
| IR-4 | Incident Handling | Incident handling procedures defined |
| IR-6 | Incident Reporting | HIPAA breach notification procedures in place |
| IR-8 | Incident Response Plan | IRP developed and tested annually |

---

## 5. Tailoring Decisions

| Control | Decision | Rationale |
|---|---|---|
| PE-3 (Physical Access — Server Rooms) | Retained for On-Prem only | AWS physical security is AWS responsibility per shared responsibility model |
| SA-12 (Supply Chain Protection) | Scoped to AWS and key vendors | Bundle relies on AWS as primary infrastructure provider |
| MA-4 (Nonlocal Maintenance) | Applied to On-Prem components only | Cloud components maintained by AWS under shared responsibility |

---

## 6. HIPAA Security Rule Crosswalk

| HIPAA Safeguard | Requirement | NIST 800-53 Control Mapping |
|---|---|---|
| Administrative — Access Control | Limit PHI access to authorized users | AC-2, AC-3, AC-6 |
| Administrative — Audit Controls | Record PHI access activity | AU-2, AU-3, AU-12 |
| Administrative — Incident Procedures | Respond to security incidents | IR-4, IR-6, IR-8 |
| Technical — Access Control | Unique user identification | IA-2, IA-5 |
| Technical — Encryption in Transit | Encrypt PHI over networks | SC-8, SC-8(1) |
| Technical — Encryption at Rest | Encrypt stored PHI | SC-28 |
| Physical — Workstation Security | Secure clinical endpoints | PE-3, AC-3 |

---

## 7. Next Step
The controls identified in this document will be fully documented in 
the System Security Plan (SSP), where each control's implementation 
within Bundle will be described in detail.

---

*This document is part of the Bundle EHR simulated RMF authorization 
package. All data and scenarios are fictional and for portfolio use only.*
