# MITRE ATT&CK Mapping

## Overview

- This document maps the assessment activities performed during the MiniCorp security assessment to the MITRE ATT&CK® framework.

- The purpose of this mapping is to provide defensive context by relating assessment activities to standardized ATT&CK techniques.

> **Important**
>
> This document maps **assessment activities only**. It does **not** imply that adversary emulation, exploitation, persistence, privilege escalation, lateral movement, or post-exploitation activities were performed.

---

## Objectives

- The ATT&CK mapping was created to:

    - Relate assessment activities to a recognized security framework.
    - Improve understanding of enterprise attack surfaces.
    - Demonstrate familiarity with MITRE ATT&CK terminology.
    - Support defensive analysis.
    - Maintain an accurate record of the assessment scope.

---

## Assessment Scope

- The MiniCorp assessment focused on:

    - Host discovery
    - Service enumeration
    - DNS validation
    - LDAP enumeration
    - SMB authorization validation
    - Group Policy validation
    - Web server assessment
    - WordPress assessment
    - Configuration review

- Activities outside this scope are intentionally **not** mapped.

---

## ATT&CK Mapping Summary

| Assessment Activity | ATT&CK Technique | Technique ID |
|---------------------|------------------|--------------|
| Network Service Discovery | Network Service Discovery | T1046 |
| Active Scanning | Active Scanning | T1595 |
| Internal Host Discovery | Remote System Discovery | T1018 |
| DNS Validation | System Network Configuration Discovery | T1016 |
| LDAP User Enumeration | Account Discovery | T1087 |
| LDAP Group Enumeration | Permission Group Discovery | T1069 |
| SMB Share Validation | Network Share Discovery | T1135 |
| Directory Enumeration | File and Directory Discovery | T1083 |

---

## Detailed Technique Mapping

### T1595 — Active Scanning

#### Assessment Activity

- Host discovery and service enumeration.

#### Purpose

- Identify active enterprise systems prior to detailed assessment.

#### MiniCorp Activities

- Network sweep
- Live host identification
- Service discovery

#### Tools Used

- Nmap

---

### T1046 — Network Service Discovery

#### Assessment Activity

- Identification of exposed services.

#### MiniCorp Activities

- Services identified included:

    - DNS
    - LDAP
    - Kerberos
    - SMB
    - HTTP
    - SSH

#### Tools Used

- Nmap

---

### T1018 — Remote System Discovery

#### Assessment Activity

- Identification of enterprise hosts.

#### MiniCorp Activities

- Validated systems included:

    - MiniCorp-DC
    - MiniCorp-Client
    - MiniCorp-Ubuntu

#### Tools Used

- Nmap

---

### T1016 — System Network Configuration Discovery

#### Assessment Activity

- DNS validation and network verification.

#### MiniCorp Activities

- Domain resolution
- Internal DNS verification
- Name resolution testing

#### Tools Used

- dig
- nslookup

---

### T1087 — Account Discovery

#### Assessment Activity

- Authenticated LDAP enumeration.

#### MiniCorp Activities

- Directory queries returned:

    - User accounts
    - Distinguished Names
    - Naming Contexts

#### Tools Used

- ldapsearch

---

### T1069 — Permission Group Discovery

#### Assessment Activity

- Enumeration of security groups.

#### MiniCorp Activities

- Authenticated LDAP queries identified:

    - Department security groups
    - Administrative groups

#### Tools Used

- ldapsearch

---

### T1135 — Network Share Discovery

#### Assessment Activity

- Validation of departmental SMB shares.

#### MiniCorp Activities

- Authenticated users accessed:

    - Department shares
    - Public share

- Authorization boundaries were validated using security group membership.

#### Tools Used

- smbclient

---

### T1083 — File and Directory Discovery

#### Assessment Activity

- Directory and web content review.

#### MiniCorp Activities

- Assessment included:

    - Web directory review
    - WordPress endpoint review
    - Apache configuration review

#### Tools Used

- Gobuster
- curl

---

## Techniques Intentionally Excluded

- The following ATT&CK techniques are **not** mapped because they were **not performed** during the MiniCorp assessment.

| Technique Category | Reason |
|--------------------|--------|
| Credential Dumping | Not performed |
| OS Credential Access | Not performed |
| Privilege Escalation | Not performed |
| Persistence | Not performed |
| Defense Evasion | Not performed |
| Lateral Movement | Not performed |
| Pass-the-Hash | Not performed |
| Kerberoasting | Not performed |
| Golden Ticket | Not performed |
| Silver Ticket | Not performed |
| DCSync | Not performed |
| Command and Control | Not performed |
| Data Exfiltration | Not performed |

- Maintaining these exclusions preserves the accuracy of the repository.

---

## Defensive Perspective

- The ATT&CK framework can also be used to identify defensive monitoring opportunities.

- Examples include:

| Technique | Example Detection Opportunity |
|-----------|-------------------------------|
| T1595 | Monitor internal network scanning activity |
| T1046 | Alert on unexpected service enumeration |
| T1087 | Monitor large LDAP enumeration requests |
| T1069 | Review security group enumeration events |
| T1135 | Monitor SMB share access patterns |

- These examples illustrate how ATT&CK techniques can support defensive monitoring without implying malicious activity.

---

## Assessment Coverage

| ATT&CK Tactic | Covered |
|---------------|:-------:|
| Reconnaissance | ✅ |
| Discovery | ✅ |
| Initial Access | ❌ |
| Execution | ❌ |
| Persistence | ❌ |
| Privilege Escalation | ❌ |
| Defense Evasion | ❌ |
| Credential Access | ❌ |
| Lateral Movement | ❌ |
| Collection | ❌ |
| Command and Control | ❌ |
| Exfiltration | ❌ |
| Impact | ❌ |

- The MiniCorp assessment intentionally focused on reconnaissance, discovery, validation, and configuration review rather than adversary emulation.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Security findings |
| `09-hardening-recommendations.md` | Security improvement recommendations |

---

## Summary

- The MiniCorp assessment maps a limited set of reconnaissance and discovery activities to the MITRE ATT&CK framework.

- The mapping reflects only the techniques that were actually performed during the assessment, ensuring that the documentation remains technically accurate, evidence-based, and suitable for professional discussion.

- Rather than portraying a full adversary simulation, the ATT&CK mapping demonstrates how structured enterprise assessments can be aligned with an industry-standard framework while maintaining clear boundaries between validated activities and techniques that were intentionally out of scope.
