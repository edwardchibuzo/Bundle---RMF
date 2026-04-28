# System Overview & Authorization Boundary
**System Name:** Bundle EHR
**Document Type:** System Overview
**Version:** 1.0
**Status:** Draft
**Prepared By:** Edward Chibuzo
**Date:** 01/20/2026
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. System Description
Bundle is a hybrid Electronic Healthcare Management System designed
to support day-to-day healthcare operations. The system enables
healthcare providers to manage patient records, appointments, billing,
and clinical documentation in a secure and centralized environment.

Bundle processes, stores, and transmits sensitive health information
including Protected Health Information (PHI) and Personally
Identifiable Information (PII), making security and compliance a
critical priority.

---

## 2. System Purpose and Mission

The primary mission of Bundle is to:

- Support patient registration and profile management
- Enable appointment scheduling and tracking
- Maintain and manage Electronic Health Records (EHR)
- Facilitate billing and insurance coordination
- Support clinical documentation by healthcare providers
- Generate operational and compliance reports
- Maintain audit logs for security and compliance purposes

---

## 3. System Users

| User Role | Description |
|---|---|
| Patients | Access personal health records and appointments |
| Doctors | View and update patient records and treatment notes |
| Nurses | Access patient information and update care notes |
| Administrative Staff | Manage scheduling and patient registration |
| Billing Staff | Process billing and insurance claims |
| System Administrators | Manage system configuration and user accounts |
| Security Team | Monitor system security and respond to incidents |

---

## 4. System Environment

Bundle operates in a hybrid environment consisting of:

| Component | Environment |
|---|---|
| Web Application Server | Cloud-hosted (AWS) |
| Database Server | On-Premises |
| Authentication Service | Cloud-hosted (AWS) |
| Audit Logging Server | On-Premises |
| Backup Server | Cloud-hosted (AWS) |
| Admin Workstations | On-Premises |
| Clinician Endpoints | On-Premises |

---

## 5. Data Handled by Bundle

| Data Type | Description | Sensitivity |
|---|---|---|
| PHI | Protected Health Information | High |
| PII | Personally Identifiable Information | High |
| Billing Data | Insurance and payment records | High |
| Treatment Notes | Clinical documentation | High |
| Appointment Data | Scheduling records | Moderate |
| Audit Logs | System activity records | Moderate |
| Authentication Data | Login credentials and access tokens | High |

---

## 6. Authorization Boundary

Bundle EHR's authorization boundary encompasses all components
directly operated and managed by the Bundle Healthcare Organization.
This includes:

**Within the boundary:**
- Web Application Server (AWS)
- Authentication Service (AWS)
- Backup Server — S3 (AWS)
- Database Server (On-Premises)
- Audit Logging Server (On-Premises)
- Admin Workstations (On-Premises)
- Clinician Endpoints (On-Premises)
- IPSec VPN tunnels connecting AWS and On-Premises components

**Outside the boundary:**
- AWS Physical Data Centers (AWS responsibility per Shared
  Responsibility Model)
- Patient personal devices
- External insurance and billing systems

---

## 7. Architecture Diagram

The diagram below illustrates the full system authorization boundary
across three trust zones — Internet/Untrusted Zone, AWS IaaS Zone,
and On-Premises Zone.

![Architecture Diagram](./diagrams/Architecture_Diagram.png)

---

## 8. Trust Zones

**Internet / Untrusted Zone**
All external traffic enters exclusively through HTTPS, intercepted
by AWS WAF before reaching any application layer. No untrusted
traffic ever touches Bundle's core infrastructure directly.

**AWS IaaS Zone (Shared Responsibility)**
Filtered traffic passes through an Application Load Balancer (ALB)
before reaching the Web Application Server. Backups are
automatically offloaded to S3. AWS manages physical infrastructure
security — Bundle owns everything above the hypervisor.

**On-Premises Zone (Org-Controlled)**
The on-premises database (PHI/PII) and Audit Log Server live
entirely within the organization's physical control, connected
to the AWS layer exclusively via IPSec VPN tunnels. All
administrative and clinical endpoint activity is captured
in the audit log.

---

## 9. Compliance and Regulatory Scope

| Framework | Relevance |
|---|---|
| HIPAA | Bundle processes PHI and must meet HIPAA Security Rule requirements |
| NIST SP 800-53 Rev 5 | Primary control framework for RMF authorization |
| FIPS 199 | Used to categorize Bundle based on impact levels |
| NIST SP 800-60 | Used to identify information types handled by Bundle |
| GDPR | Applicable if Bundle handles data of EU-based individuals |

---

## 10. Key Assumptions

- Bundle is a fictional system created for portfolio and learning purposes
- All data, scenarios, and documentation are simulated
- Security controls are selected based on a High impact baseline
- The hybrid environment assumes AWS as the cloud service provider
- No real PHI or PII is used anywhere in this project

---

*This document is part of the Bundle EHR simulated RMF authorization
package. All data and scenarios are fictional and for portfolio use only.*
