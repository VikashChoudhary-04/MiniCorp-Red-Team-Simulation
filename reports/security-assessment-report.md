# MiniCorp Security Assessment Report

## Assessment Information

| Item | Value |
|------|-------|
| Project | MiniCorp Enterprise Infrastructure Lab |
| Assessment Type | Internal Infrastructure Security Assessment |
| Environment | Private Laboratory |
| Assessment Scope | Windows Server, Windows Client, Ubuntu Server |
| Domain | `minicorp.local` |
| Report Version | 1.0 |
| Classification | Internal |
| Status | Final |

---

## Table of Contents

1. Executive Overview
2. Assessment Objectives
3. Scope
4. Environment Overview
5. Assessment Methodology
6. Assessment Activities
7. Assessment Results
8. Security Findings
9. Risk Analysis
10. Recommendations
11. Limitations
12. Conclusion

---

## Executive Overview

- MiniCorp is a simulated enterprise environment designed to demonstrate enterprise infrastructure deployment, centralized administration, and structured security assessment.

- The assessment evaluated the deployment and configuration of Windows and Linux systems integrated through Active Directory Domain Services. The review focused on validating enterprise services, authorization mechanisms, and web application configuration while documenting observations and recommendations.

- The assessment was conducted entirely within a controlled laboratory environment.

---

## Assessment Objectives

- The assessment was performed to:

    - Validate enterprise infrastructure.
    - Verify Active Directory functionality.
    - Review DNS configuration. 
    - Validate LDAP services.
    - Assess SMB authorization.
    - Verify Group Policy implementation.
    - Review Linux web server configuration.
    - Assess the WordPress deployment.
    - Identify configuration observations.
    - Recommend practical hardening measures.

---

## Scope

### Systems

| Host | Role |
|------|------|
| MiniCorp-DC | Windows Server 2022 Domain Controller |
| MiniCorp-Client | Windows 10 Domain Workstation |
| MiniCorp-Ubuntu | Ubuntu Server 24.04 LTS |

---

### Services

- The assessment included:

    - Active Directory
    - DNS
    - LDAP
    - Kerberos
    - SMB
    - Apache
    - PHP
    - MariaDB
    - WordPress

---

### Out of Scope

- The following activities were intentionally excluded:

    - Privilege escalation
    - Persistence
    - Malware deployment
    - Credential dumping
    - Lateral movement
    - Active Directory compromise
    - Data exfiltration
    - Denial of Service
    - Testing against third-party infrastructure

---

## Environment Overview

- The MiniCorp environment models a small enterprise network.

| Component | Description |
|-----------|-------------|
| Domain Controller | Windows Server 2022 |
| Client | Windows 10 |
| Web Server | Ubuntu Server 24.04 LTS |
| Domain | `minicorp.local` |
| Internal Network | `192.168.192.0/24` |

- Core enterprise services include:

    - Active Directory Domain Services
    - DNS
    - LDAP
    - Kerberos
    - SMB
    - Group Policy

- The Ubuntu server hosts a WordPress application using Apache, PHP, and MariaDB.

---

## Assessment Methodology

- The assessment followed a structured methodology to ensure repeatable and evidence-based results.

```text
Infrastructure Verification
        │
        ▼
Host Discovery
        │
        ▼
Service Enumeration
        │
        ▼
DNS Validation
        │
        ▼
LDAP Validation
        │
        ▼
SMB Authorization Validation
        │
        ▼
Group Policy Validation
        │
        ▼
Web Server Assessment
        │
        ▼
WordPress Assessment
        │
        ▼
Evidence Collection
        │
        ▼
Findings
        │
        ▼
Recommendations
```

- Each phase built on the previous stage, ensuring that observations were supported by collected evidence.

---

## Assessment Activities

### Infrastructure Verification

- Connectivity between enterprise systems was verified prior to assessment.

- Validation included:

    - IP connectivity
    - Domain communication
    - Internal routing
    - Name resolution

---

### Host Discovery

- Active hosts within the enterprise network were identified.

- Observed systems:

    - MiniCorp-DC
    - MiniCorp-Client
    - MiniCorp-Ubuntu

- No unexpected hosts were detected.

---

### Service Enumeration

- Network services were identified to verify that each system exposed only the expected functionality.

#### Domain Controller

- Observed services included:

    - DNS
    - LDAP
    - Kerberos
    - SMB
    - Microsoft RPC
    - Global Catalog

#### Ubuntu Server

- Observed services included:

    - SSH
    - HTTP

- The observed services were consistent with the intended system roles.

---

### DNS Validation

- DNS testing confirmed:

    - Successful domain resolution.
    - Functional Active Directory integration.
    - Reliable internal name resolution.

---

### LDAP Validation

- Authenticated LDAP queries verified:

    - User objects.
    - Security groups.
    - Organizational Units.
    - Naming contexts.

- Directory services behaved as expected for authenticated users.

---

### SMB Authorization Validation

- Departmental file shares were reviewed to confirm authorization controls.

- Testing demonstrated:

    - Authorized users accessed assigned resources.
    - Unauthorized access was denied.
    - Share permissions and NTFS permissions functioned together as intended.

---

### Group Policy Validation

- The assessment confirmed successful application of:

    - Password Policy
    - Account Lockout Policy
    - Drive Mapping
    - Control Panel Restrictions
    - Command Prompt Restrictions
    - Registry Editor Restrictions

- Security filtering and delegation operated as expected.

---

### Web Server Assessment

- The Ubuntu server was reviewed to validate the deployed web application stack.

- Activities included:

    - HTTP inspection
    - Service identification
    - Endpoint review
    - Configuration review

- Apache successfully hosted the WordPress application.

---

### WordPress Assessment

- The WordPress deployment was assessed to understand its exposed functionality.

- Validation confirmed:

    - Administrative interface accessibility.
    - XML-RPC availability.
    - Expected application behavior.

---

## Assessment Results

| Assessment Area | Result |
|-----------------|:------:|
| Infrastructure Verification | ✅ |
| Host Discovery | ✅ |
| Service Enumeration | ✅ |
| DNS Validation | ✅ |
| LDAP Validation | ✅ |
| SMB Authorization Validation | ✅ |
| Group Policy Validation | ✅ |
| Web Server Assessment | ✅ |
| WordPress Assessment | ✅ |
| Evidence Collection | ✅ |

- The assessment successfully validated the implementation of the MiniCorp enterprise environment.

---

## Security Findings

| ID | Finding | Severity |
|----|----------|:--------:|
| MC-001 | Apache `server-status` endpoint accessible | Low |
| MC-002 | WordPress administrative interface exposed | Informational |
| MC-003 | WordPress XML-RPC endpoint available | Informational |
| MC-004 | Department-based SMB authorization validated | Informational |
| MC-005 | Active Directory integrated DNS validated | Informational |
| MC-006 | Authenticated LDAP directory enumeration | Informational |

- Detailed analysis is available in `docs/08-findings.md`.

---

## Risk Analysis

| Severity | Count |
|----------|------:|
| Critical | 0 |
| High | 0 |
| Medium | 0 |
| Low | 1 |
| Informational | 5 |

- No Critical, High, or Medium severity issues were identified.

- The assessment primarily identified expected enterprise functionality and opportunities for additional hardening.

---

## Recommendations

### High Priority

- Restrict access to the Apache `server-status` endpoint.
- Review privileged group memberships.
- Maintain operating system and application updates.
- Periodically review SMB and NTFS permissions.

---

### Medium Priority

- Enable enhanced Windows auditing.
- Review Group Policy Objects regularly.
- Review Apache configuration.
- Evaluate the operational requirement for XML-RPC.

---

### Long-Term Improvements

- Future enhancements may include:

    - Windows Event Forwarding
    - Sysmon
    - Wazuh
    - SIEM integration
    - Active Directory Certificate Services
    - Infrastructure automation

- These enhancements are recommended for future versions of the environment and were not part of the assessed implementation.

---

## Limitations

- This assessment was intentionally limited to the MiniCorp laboratory environment.

- The report does not claim:

    - Domain compromise.
    - Privilege escalation.
    - Credential extraction.
    - Lateral movement.
    - Persistence.
    - Post-exploitation activities.

- The findings reflect only activities that were performed and validated during the assessment.

---

## Conclusion

- The MiniCorp Security Assessment confirmed that the enterprise environment was successfully deployed and that its core infrastructure components operated as intended.

- The review validated Active Directory services, enterprise authentication, centralized authorization, Group Policy implementation, and Linux web hosting while identifying a small number of low-risk configuration observations.

- The assessment demonstrates how enterprise infrastructure can be evaluated through a structured, evidence-based methodology without overstating risk or claiming unsupported attack outcomes.

- The recommendations presented in this report provide a practical roadmap for strengthening the environment while maintaining its educational and administrative objectives.
