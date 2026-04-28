# Security Control Tailoring Decisions
**System Name:** Bundle EHR
**Document Type:** Tailoring Decisions
**Version:** 1.0
**Status:** Draft
**Prepared By:** Edward Chibuzo
**Date:** April 28, 2025
**Baseline:** NIST SP 800-53 Rev 5 — HIGH Impact

---

## 1. Purpose
This document records all tailoring decisions made to the NIST
SP 800-53 Rev 5 HIGH baseline for Bundle EHR. Tailoring decisions
reflect the hybrid AWS and On-Premises environment, the AWS Shared
Responsibility Model, and the specific operational context of a
healthcare system processing PHI and PII.

---

## 2. Tailoring Approach
Tailoring was conducted in accordance with NIST SP 800-53 Rev 5
and NIST SP 800-53B guidance. The following factors informed
all tailoring decisions:

| Factor | Detail |
|---|---|
| Environment | Hybrid — AWS Cloud + On-Premises |
| Data Sensitivity | High — PHI and PII |
| Regulatory Requirements | HIPAA Security Rule |
| Shared Responsibility | AWS manages physical infrastructure |
| System Type | Major Application |

---

## 3. Tailoring Decisions

### Decision 1 — Physical and Environmental Controls (PE Family)

| Field | Detail |
|---|---|
| **Controls Affected** | PE-3, PE-6, PE-8, PE-12, PE-13, PE-14 |
| **Decision** | Retain for On-Premises components only |
| **Rationale** | AWS physical data centers are outside the Bundle authorization boundary per the AWS Shared Responsibility Model. AWS is contractually and operationally responsible for physical security of all cloud-hosted infrastructure. Bundle retains full responsibility for physical security of On-Premises components including the database server, audit logging server, admin workstations, and clinician endpoints. |
| **Residual Risk** | Low — AWS SOC 2 Type II and FedRAMP certifications provide assurance of physical security controls |

---

### Decision 2 — Supply Chain Risk Management (SA-12)

| Field | Detail |
|---|---|
| **Control Affected** | SA-12 |
| **Decision** | Scoped to AWS and key third party vendors only |
| **Rationale** | Bundle's supply chain is limited to AWS as the primary infrastructure provider and a small number of software vendors. A full supply chain risk management program covering all potential suppliers is disproportionate to Bundle's size and operational scope. Key vendor risk is managed through AWS contractual agreements and annual vendor risk reviews. |
| **Residual Risk** | Low-Moderate — vendor risk reviews and AWS contractual controls reduce but do not eliminate supply chain risk |

---

### Decision 3 — Nonlocal Maintenance (MA-4)

| Field | Detail |
|---|---|
| **Control Affected** | MA-4 |
| **Decision** | Applied to On-Premises components only |
| **Rationale** | Cloud-hosted components (Web Application Server, Authentication Service, S3 Backup) are maintained by AWS under the Shared Responsibility Model. Bundle is not responsible for nonlocal maintenance of AWS-managed infrastructure. MA-4 controls apply fully to On-Premises database server, audit logging server, admin workstations, and clinician endpoints. |
| **Residual Risk** | Low — AWS maintenance procedures are governed by contractual SLAs and compliance certifications |

---

### Decision 4 — GDPR Controls

| Field | Detail |
|---|---|
| **Controls Affected** | Applicable privacy and data protection controls |
| **Decision** | GDPR requirements scoped conditionally |
| **Rationale** | GDPR applies to Bundle only if EU-based individuals are registered as patients. For the purposes of this portfolio project Bundle is assumed to operate primarily within the United States. GDPR applicability will be reassessed if Bundle expands to serve EU-based patients. |
| **Residual Risk** | Low for current scope — reassessment required upon international expansion |

---

## 4. Tailoring Decision Summary

| Control | Family | Decision | Rationale Summary |
|---|---|---|---|
| PE-3, PE-6, PE-8 | Physical & Environmental | On-Prem only | AWS shared responsibility |
| SA-12 | System Acquisition | Scoped to key vendors | Limited supply chain scope |
| MA-4 | Maintenance | On-Prem only | AWS shared responsibility |
| GDPR controls | Privacy | Conditional | US-based operations only |

---

## 5. Compensating Controls
Where controls have been tailored or scoped, the following
compensating controls provide additional risk coverage:

| Tailored Control | Compensating Control | Description |
|---|---|---|
| PE family — AWS components | AWS SOC 2 Type II | AWS physical security independently audited |
| SA-12 — full scope | Annual vendor risk review | Key vendors reviewed annually by ISSO |
| MA-4 — AWS components | AWS maintenance SLAs | Contractual maintenance obligations enforced |

---

*This document is part of the Bundle EHR simulated RMF authorization
package. All data and scenarios are fictional and for portfolio use only.*
