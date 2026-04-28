# System Security Plan (SSP)
**System Name:** Bundle EHR  
**Document Type:** System Security Plan  
**Version:** 1.0  
**Status:** Draft  
**Prepared By:** Edward Chibuzo  
**Date:** [02/07/2026]  
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. System Identification

| Field | Detail |
|---|---|
| System Name | Bundle EHR |
| System Abbreviation | Bundle |
| System Owner | Bundle Healthcare Organization |
| Information System Security Officer (ISSO) | Edward Chibuzo |
| Authorizing Official (AO) | Chief Information Officer (CIO) |
| System Type | Major Application |
| Operating Environment | Hybrid (AWS Cloud + On-Premises) |
| System Status | Under Development |
| Authorization Boundary | See Architecture Diagram |

---

## 2. System Purpose and Description
Bundle EHR is a hybrid Electronic Health Record Management System 
designed to support day-to-day healthcare operations. The system 
enables healthcare providers to manage patient records, appointments, 
billing, and clinical documentation in a secure and centralized 
environment.

Bundle processes, stores, and transmits Protected Health Information 
(PHI) and Personally Identifiable Information (PII), making security 
and compliance a critical organizational priority.

---

## 3. System Environment

| Component | Location | Function |
|---|---|---|
| Web Application Server | AWS (Cloud) | Hosts application logic and user interface |
| Authentication Service | AWS (Cloud) | Manages identity verification and access control |
| Backup Server (S3) | AWS (Cloud) | Encrypted backups of all critical system data |
| Database Server | On-Premises | Stores all PHI, PII, and billing records |
| Audit Logging Server | On-Premises | Captures all system activity logs |
| Admin Workstations | On-Premises | Used by IT and security staff |
| Clinician Endpoints | On-Premises | Used by doctors and nurses to access Bundle |

---

## 4. System Users

| User Role | Access Level | Authentication Requirement |
|---|---|---|
| Patients | Read own records only | MFA required |
| Doctors | Read/write patient records | MFA required |
| Nurses | Read/write care notes | MFA required |
| Administrative Staff | Scheduling and registration | MFA required |
| Billing Staff | Billing and insurance data | MFA required |
| System Administrators | Full system configuration | MFA + privileged account |
| Security Team | Audit logs and monitoring | MFA + privileged account |

---

## 5. Security Control Implementation

### AC-2 — Account Management
**Control Statement:** The organization manages information system 
accounts including establishing, activating, modifying, reviewing, 
disabling, and removing accounts.

**Bundle Implementation:**  
Bundle maintains a formal account management process for all seven 
user roles. New accounts are created only upon written request from 
a supervisor and approval from the System Administrator. All accounts 
are reviewed quarterly for continued necessity. Accounts are disabled 
within 24 hours of employee termination or role change. Shared or 
group accounts are prohibited. The Authentication Service (AWS) 
enforces all account lifecycle policies.

---

### AC-3 — Access Enforcement
**Control Statement:** The system enforces approved authorizations 
for logical access to information and system resources.

**Bundle Implementation:**  
Bundle enforces Role-Based Access Control (RBAC) at both the 
application and database layers. Each user role has a defined 
permission set that restricts access to only the data and functions 
required for that role. Doctors cannot access billing records. 
Billing staff cannot access clinical notes. Database queries are 
filtered at the application layer to prevent unauthorized data 
retrieval. Access enforcement is audited monthly.

---

### AC-6 — Least Privilege
**Control Statement:** The system employs the principle of least 
privilege, allowing only authorized access required to accomplish 
assigned tasks.

**Bundle Implementation:**  
All Bundle user accounts are provisioned with the minimum permissions 
required to perform their job functions. Administrative privileges 
are granted only to System Administrators and Security Team members 
through separate privileged accounts. Privileged access is reviewed 
monthly. No user account has administrative access to both the 
application and database simultaneously.

---

### AU-2 — Event Logging
**Control Statement:** The organization determines the events that 
the system must log in support of the audit function.

**Bundle Implementation:**  
Bundle logs the following events across all system components: 
user login and logout, failed authentication attempts, PHI access 
and modification, account creation and deletion, privilege 
escalation, system configuration changes, and backup operations. 
All logs are written to the dedicated on-premises Audit Logging 
Server in real time and retained for a minimum of 6 years in 
accordance with HIPAA requirements.

---

### AU-9 — Protection of Audit Information
**Control Statement:** The system protects audit information and 
tools from unauthorized access, modification, and deletion.

**Bundle Implementation:**  
Audit logs are stored on a dedicated on-premises Audit Logging 
Server that is physically and logically separated from the 
production environment. Only Security Team members have read 
access to audit logs. No user — including System Administrators — 
has the ability to modify or delete audit records. Log integrity 
is verified weekly using cryptographic hash verification.

---

### IA-2 — Identification and Authentication
**Control Statement:** The system uniquely identifies and 
authenticates organizational users.

**Bundle Implementation:**  
Every Bundle user is assigned a unique user ID upon account 
creation. Shared credentials are strictly prohibited. The 
Authentication Service (AWS Cognito) verifies user identity 
at every login attempt. Failed login attempts are logged and 
after 5 consecutive failures the account is temporarily locked 
for 30 minutes. Security Team is alerted on repeated lockouts.

---

### IA-2(1) — MFA for Privileged Accounts
**Control Statement:** The system implements multi-factor 
authentication for privileged accounts.

**Bundle Implementation:**  
All System Administrator and Security Team accounts require 
multi-factor authentication using a time-based one-time password 
(TOTP) application in addition to a strong password. MFA cannot 
be bypassed or disabled by the user. Privileged sessions are 
automatically terminated after 15 minutes of inactivity.

---

### IA-2(2) — MFA for Non-Privileged Accounts
**Control Statement:** The system implements multi-factor 
authentication for non-privileged accounts.

**Bundle Implementation:**  
All clinical and administrative user accounts require MFA at 
login. This applies to Patients, Doctors, Nurses, Administrative 
Staff, and Billing Staff. MFA is enforced through the AWS 
Authentication Service and cannot be disabled by individual users. 
Users who lose MFA access must follow the formal account recovery 
procedure administered by the System Administrator.

---

### SC-8 — Transmission Confidentiality and Integrity
**Control Statement:** The system implements cryptographic 
mechanisms to prevent unauthorized disclosure of information 
during transmission.

**Bundle Implementation:**  
All data transmitted between users and the Bundle web application 
is encrypted using TLS 1.2 or higher. HTTP connections are 
automatically redirected to HTTPS. Communication between the AWS 
cloud layer and on-premises components (database and audit server) 
is encrypted via IPSec VPN tunnels. Unencrypted transmission of 
PHI or PII is technically prohibited at the network layer.

---

### SC-28 — Protection of Information at Rest
**Control Statement:** The system protects the confidentiality 
and integrity of information at rest.

**Bundle Implementation:**  
All PHI and PII stored in the on-premises database is encrypted 
using AES-256 encryption. AWS S3 backup buckets use server-side 
encryption (SSE-S3) with AES-256. Encryption keys are managed 
through AWS Key Management Service (KMS). Clinician endpoint 
hard drives are encrypted using full-disk encryption. Unencrypted 
storage of PHI on any system component is prohibited.

---

### IR-4 — Incident Handling
**Control Statement:** The organization implements an incident 
handling capability including preparation, detection, analysis, 
containment, eradication, and recovery.

**Bundle Implementation:**  
Bundle maintains a formal Incident Response Plan (IRP) that 
defines procedures for each phase of incident handling. The 
Security Team is responsible for incident detection through 
continuous monitoring of audit logs and system alerts. Upon 
detection, incidents are classified by severity and the 
appropriate response procedure is activated. All incidents 
are documented in the incident log and reviewed monthly by 
the Security Team lead.

---

### IR-6 — Incident Reporting
**Control Statement:** The organization reports security 
incidents to appropriate authorities.

**Bundle Implementation:**  
In the event of a confirmed PHI breach, Bundle follows the 
HIPAA Breach Notification Rule. Affected individuals are 
notified within 60 days of discovery. If the breach affects 
500 or more individuals, the Department of Health and Human 
Services (HHS) is notified immediately. Business associates 
are notified within 60 days. All breach notifications are 
documented and retained for a minimum of 6 years.

---

### SI-2 — Flaw Remediation
**Control Statement:** The organization identifies, reports, 
and corrects information system flaws.

**Bundle Implementation:**  
Bundle conducts monthly vulnerability scans across all system 
components using automated scanning tools. Critical and high 
vulnerabilities are remediated within 30 days of discovery. 
Medium vulnerabilities are remediated within 90 days. All 
identified flaws are tracked in the POA&M until remediation 
is confirmed. Patch management is the responsibility of the 
System Administrator for on-premises components and follows 
AWS patch schedules for cloud components.

---

### SI-3 — Malware Protection
**Control Statement:** The system implements malware protection 
mechanisms at entry and exit points.

**Bundle Implementation:**  
Endpoint detection and response (EDR) software is deployed 
on all Admin Workstations and Clinician Endpoints. AWS WAF 
provides web application firewall protection at the perimeter. 
Malware definition updates are applied automatically. Any 
detected malware triggers an immediate security alert to the 
Security Team and initiates the incident response procedure.

---

## 6. Document Control

| Field | Detail |
|---|---|
| Author | Edward Chibuzo |
| Created | [Today's date] |
| Last Updated | [Today's date] |
| Next Review | [Date + 1 year] |
| Version | 1.0 |

---

*This document is part of the Bundle EHR simulated RMF authorization 
package. All data and scenarios are fictional and for portfolio use only.*
