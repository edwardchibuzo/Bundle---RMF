# Incident Response Plan (IRP)
**System Name:** Bundle EHR
**Document Type:** Incident Response Plan
**Version:** 1.0
**Status:** Draft
**Prepared By:** Edward Chibuzo
**Date:** April 28, 2025
**Classification:** Unclassified — For Portfolio Use Only

---

## 1. Purpose
This Incident Response Plan defines the procedures Bundle EHR
will follow to prepare for, detect, contain, eradicate, recover
from, and learn from security incidents. This plan aligns with
NIST SP 800-61 Rev 2 (Computer Security Incident Handling Guide)
and satisfies the requirements of NIST SP 800-53 Rev 5 controls
IR-1, IR-4, IR-6, and IR-8.

This plan also addresses HIPAA Breach Notification Rule
requirements for incidents involving Protected Health Information
(PHI) or Personally Identifiable Information (PII).

---

## 2. Scope
This plan applies to all components within the Bundle EHR
authorization boundary including:

- Web Application Server (AWS)
- Authentication Service (AWS)
- Backup Server — S3 (AWS)
- Database Server (On-Premises)
- Audit Logging Server (On-Premises)
- Admin Workstations (On-Premises)
- Clinician Endpoints (On-Premises)

---

## 3. Incident Response Team

| Role | Responsibility |
|---|---|
| ISSO — Incident Commander | Overall incident coordination and AO notification |
| Security Team Lead | Technical investigation and containment |
| System Administrator | System isolation and recovery actions |
| Legal / Compliance Officer | HIPAA breach assessment and notification |
| Communications Lead | Internal and external communications |
| Executive Sponsor — CIO | Final authorization for major response actions |

---

## 4. Incident Categories

### 4.1 Severity Levels

| Severity | Definition | Response Time |
|---|---|---|
| Critical | Active breach of PHI, ransomware, or system-wide compromise | Immediate — within 1 hour |
| High | Confirmed unauthorized access, malware detection, data exfiltration attempt | Within 4 hours |
| Moderate | Suspicious activity, policy violation, failed intrusion attempt | Within 24 hours |
| Low | Minor policy violation, single failed login, non-sensitive anomaly | Within 72 hours |

### 4.2 Incident Types

| Type | Examples |
|---|---|
| Unauthorized Access | Compromised credentials, privilege escalation, account takeover |
| Malware | Ransomware, virus, spyware on endpoints or servers |
| Data Breach | PHI exfiltration, accidental disclosure, insider data theft |
| Denial of Service | DDoS attack, system unavailability affecting patient care |
| Physical Security | Unauthorized access to server room, stolen endpoint |
| Insider Threat | Malicious staff activity, policy violation, data misuse |

---

## 5. Incident Response Phases

### Phase 1 — Preparation
Preparation activities ensure Bundle is ready to respond
effectively before an incident occurs.

| Activity | Responsible Party | Frequency |
|---|---|---|
| Maintain and update IRP | ISSO | Annually |
| Conduct tabletop exercise | Security Team Lead | Annually |
| Train all staff on incident reporting | Security Team | Annually |
| Verify incident response contact list | ISSO | Quarterly |
| Test backup restoration | System Administrator | Quarterly |
| Review and update audit log monitoring | Security Team | Monthly |

---

### Phase 2 — Detection and Analysis

#### 2.1 Detection Sources
Incidents may be detected through any of the following:

| Source | Method |
|---|---|
| Audit Logging Server | Anomalous activity alerts |
| AWS WAF | Perimeter threat alerts |
| EDR Solution | Malware detection on endpoints |
| Authentication Service | Failed login threshold alerts |
| Staff Reports | Users reporting suspicious activity |
| AWS CloudTrail | Anomalous cloud activity |
| Vulnerability Scanner | Critical vulnerability discovery |

#### 2.2 Initial Analysis Steps
Upon detection of a potential incident the Security Team will:

1. Confirm whether the activity is a true positive or false positive
2. Assign a severity level using the scale in Section 4.1
3. Identify the affected systems and data types involved
4. Determine whether PHI or PII is potentially compromised
5. Document all findings in the Incident Log
6. Notify the ISSO immediately for Critical and High incidents

#### 2.3 Incident Log Fields
Every incident must be logged with the following information:

| Field | Description |
|---|---|
| Incident ID | Unique identifier e.g. INC-2025-001 |
| Date and Time Detected | Timestamp of initial detection |
| Detected By | Name and role of person who detected |
| Incident Type | Category from Section 4.2 |
| Severity Level | Critical / High / Moderate / Low |
| Affected Systems | All systems involved |
| PHI/PII Involved | Yes / No / Under Investigation |
| Initial Description | Brief summary of what was observed |
| Current Status | Open / Contained / Resolved |

---

### Phase 3 — Containment

#### 3.1 Short-Term Containment
Immediate actions to stop the incident from spreading:

| Incident Type | Containment Action |
|---|---|
| Ransomware | Isolate affected endpoint from network immediately |
| Unauthorized Access | Disable compromised account, revoke active sessions |
| Data Exfiltration | Block outbound connection, preserve network logs |
| Malware | Quarantine affected system, block malicious IP |
| Physical Breach | Secure server room, revoke physical access credentials |
| Insider Threat | Suspend user account, preserve audit logs |

#### 3.2 Long-Term Containment
After immediate containment, implement measures to allow
operations to continue safely while eradication is underway:

- Deploy patched or clean system image if needed
- Implement additional monitoring on affected systems
- Restrict access to affected data until investigation completes
- Notify affected business units of temporary restrictions

---

### Phase 4 — Eradication
Remove the root cause of the incident from the environment:

| Activity | Responsible Party |
|---|---|
| Remove malware or malicious code | Security Team |
| Patch exploited vulnerability | System Administrator |
| Reset all compromised credentials | System Administrator |
| Review and harden affected configurations | Security Team |
| Verify no persistence mechanisms remain | Security Team Lead |
| Conduct full vulnerability scan post-eradication | Security Team |

---

### Phase 5 — Recovery
Restore affected systems to normal operation:

| Activity | Responsible Party |
|---|---|
| Restore systems from verified clean backup | System Administrator |
| Verify system integrity before reconnecting | Security Team |
| Monitor restored systems closely for 72 hours | Security Team |
| Confirm normal business operations have resumed | ISSO |
| Document recovery timeline and actions taken | ISSO |
| Notify AO that recovery is complete | ISSO |

#### 5.1 Recovery Time Objectives

| System | RTO | RPO |
|---|---|---|
| Web Application Server | 4 hours | 24 hours |
| Database Server | 8 hours | 4 hours |
| Authentication Service | 2 hours | 24 hours |
| Audit Logging Server | 24 hours | 48 hours |

---

### Phase 6 — Post-Incident Activity

#### 6.1 Lessons Learned Review
Within 2 weeks of incident closure a lessons learned review
must be conducted with the full Incident Response Team:

- What happened and what was the root cause
- How effectively was the incident detected and contained
- What actions worked well and what needs improvement
- Were response times within defined thresholds
- Does the IRP need to be updated based on this incident

#### 6.2 Post-Incident Report
A formal post-incident report must be completed for all
Critical and High severity incidents containing:

| Section | Content |
|---|---|
| Executive Summary | Non-technical summary for AO and CIO |
| Incident Timeline | Chronological sequence of events |
| Root Cause Analysis | Technical cause of the incident |
| Impact Assessment | Systems affected, data involved, downtime |
| Response Actions | All containment and recovery steps taken |
| Lessons Learned | What worked, what did not |
| Recommendations | Control improvements to prevent recurrence |

---

## 6. HIPAA Breach Notification Procedures

### 6.1 Breach Assessment
Upon detection of any incident involving PHI or PII the
Legal/Compliance Officer must conduct a breach risk assessment
within 24 hours to determine:

- Was PHI or PII actually accessed, acquired, used, or disclosed
- What is the nature and extent of the PHI involved
- Who accessed or could have accessed the PHI
- Has the risk to PHI been mitigated

### 6.2 Notification Requirements

| Notification | Requirement | Deadline |
|---|---|---|
| Affected Individuals | Written notice of breach | Within 60 days of discovery |
| HHS — under 500 affected | Annual log submission | Within 60 days of year end |
| HHS — 500 or more affected | Immediate HHS notification | Within 60 days of discovery |
| Media — 500+ in one state | Prominent media notice | Within 60 days of discovery |
| Business Associates | Notify covered entity | Within 60 days of discovery |

### 6.3 Breach Notification Content
All breach notifications must include:

- Description of what happened
- Types of PHI involved
- Steps individuals should take to protect themselves
- What Bundle is doing to investigate and prevent recurrence
- Contact information for affected individuals to ask questions

---

## 7. Incident Communication Plan

| Audience | Communication Method | Timing |
|---|---|---|
| ISSO | Direct call or message | Immediately upon Critical/High detection |
| AO — CIO | Formal email notification | Within 2 hours of Critical incident |
| Affected Staff | Internal notification | As needed duri
