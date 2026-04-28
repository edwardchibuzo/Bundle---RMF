# FIPS 199 System Categorization
**System Name:** Bundle EHR  
**Document Type:** Security Categorization  
**Version:** 1.0  
**Status:** Draft  
**Prepared By:** Edward Chibuzo  
**Date:** [01/27/2026]

---

## 1. Purpose
This document categorizes Bundle EHR in accordance with FIPS 199 
(Standards for Security Categorization of Federal Information and 
Information Systems) and NIST SP 800-60 Vol. 1 & 2. The categorization 
determines the impact level for Confidentiality, Integrity, and 
Availability across all information types handled by Bundle.

---

## 2. Information Types

| Information Type | NIST 800-60 Identifier | Confidentiality | Integrity | Availability |
|---|---|---|---|---|
| Protected Health Information (PHI) | C.3.1.1 | High | High | High |
| Personally Identifiable Information (PII) | C.3.1.1 | High | High | Moderate |
| Billing & Insurance Data | C.3.1.3 | High | High | Moderate |
| Treatment & Clinical Notes | C.3.1.1 | High | High | High |
| Appointment / Scheduling Data | C.3.1.2 | Moderate | Moderate | High |
| Audit & System Logs | C.3.1.5 | Moderate | High | Moderate |
| Authentication Credentials | C.3.1.4 | High | High | High |

---

## 3. Security Categorization Result

Using the high-water mark principle per FIPS 199, the overall system 
categorization is determined by the highest impact level across all 
information types.

| Security Objective | Impact Level |
|---|---|
| Confidentiality | **High** |
| Integrity | **High** |
| Availability | **High** |

**Overall System Categorization: SC = {Confidentiality: High, Integrity: 
High, Availability: High}**

> This results in a **High impact system** under FIPS 199, requiring 
> the HIGH baseline control set from NIST SP 800-53 Rev 5.

---

## 4. Rationale

**Confidentiality — High**  
Bundle processes PHI and PII for all registered patients. Unauthorized 
disclosure would cause severe harm to individuals including identity theft, 
reputational damage, and HIPAA violations resulting in significant financial 
and legal penalties.

**Integrity — High**  
Corruption or unauthorized modification of clinical records, treatment 
notes, or billing data could directly harm patient safety, result in 
incorrect treatment decisions, and expose the organization to regulatory 
and legal liability.

**Availability — High**  
Healthcare providers depend on continuous access to Bundle for patient 
care. Prolonged unavailability during clinical operations could result 
in delayed treatment, patient harm, or inability to access critical 
medical history in emergency situations.

---

## 5. Applicable Frameworks

| Framework | Application |
|---|---|
| FIPS 199 | Categorization methodology |
| NIST SP 800-60 Vol. 1 & 2 | Information type identification |
| NIST SP 800-53 Rev 5 | Control baseline selection (HIGH) |
| HIPAA Security Rule | Healthcare compliance requirements |

---

## 6. Next Step
Based on this High impact categorization, the HIGH baseline control 
set from NIST SP 800-53 Rev 5 will be used as the starting point for 
control selection in Step 3.

---

*This document is part of the Bundle EHR simulated RMF authorization 
package. All data and scenarios are fictional and for portfolio use only.*
