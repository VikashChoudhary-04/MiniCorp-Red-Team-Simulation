# Security Assessment

## Overview

- Following the deployment and configuration of the MiniCorp enterprise environment, a structured internal security assessment was conducted to validate infrastructure configuration, enterprise services, access controls, and the deployed web application.

- The assessment focused on identifying exposed services, verifying enterprise functionality, evaluating authorization mechanisms, and documenting evidence-based observations.

- All assessment activities were performed within the isolated MiniCorp laboratory environment against systems owned and administered as part of this project.

---

## Assessment Objectives

- The assessment was designed to:

    - Verify network connectivity.
    - Identify active hosts.
    - Enumerate exposed services.
    - Validate Active Directory functionality.
    - Verify DNS operation.
    - Assess LDAP accessibility.
    - Validate SMB authorization.
    - Review Group Policy implementation.
    - Assess the Ubuntu web server.
    - Review the WordPress deployment.
    - Collect evidence.
    - Document observations and recommendations.

---

## Assessment Scope

### Systems

| System | Role |
|----------|------|
| MiniCorp-DC | Windows Server 2022 Domain Controller |
| MiniCorp-Client | Windows 10 Domain Workstation |
| MiniCorp-Ubuntu | Ubuntu Server Web Server |

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

## Assessment Methodology

- The assessment followed a structured workflow.

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
SMB Validation
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

- This methodology ensured that each stage built upon the previous one while maintaining traceable evidence.

---

## Phase 1 — Infrastructure Verification

- Before beginning service assessment, network connectivity between all systems was verified.

- Validation included:

    - Host communication
    - IP addressing
    - Domain membership
    - Name resolution
    - Linux connectivity

- Successful verification confirmed that the environment was operating as expected.

---

## Phase 2 — Host Discovery

- Host discovery identified active systems within the MiniCorp network.

### Objective

- Identify reachable enterprise assets prior to service enumeration.

### Tool

- Nmap

### Activities

- Network sweep
- Host identification
- Live host verification

### Result

- The assessment identified the expected enterprise systems:

    - MiniCorp-DC
    - MiniCorp-Client
    - MiniCorp-Ubuntu

- No unexpected hosts were observed.

---

## Phase 3 — Service Enumeration

- Service enumeration identified the network services exposed by each host.

### Domain Controller

- Observed services included:

    - DNS
    - Kerberos
    - LDAP
    - SMB
    - Microsoft RPC
    - Global Catalog

- These services were consistent with the intended role of an Active Directory Domain Controller.

---

### Ubuntu Server

- Observed services included:

    - SSH
    - HTTP

- The exposed services matched the expected configuration of the Linux web server.

---

## Phase 4 — DNS Validation

- DNS functionality was validated to confirm correct Active Directory integration.

### Activities

- Domain resolution
- Forward lookup testing
- DNS server verification
- Internal name resolution

### Result

- The assessment confirmed successful resolution of the MiniCorp domain and expected DNS behavior.

---

## Phase 5 — LDAP Validation

- Authenticated LDAP queries were performed using standard domain credentials.

### Objectives

- Verify directory accessibility.
- Enumerate users.
- Enumerate groups.
- Review directory structure.

### Activities

- Authenticated queries validated access to:

    - User objects
    - Security groups
    - Organizational Units
    - Distinguished Names
    - Naming Contexts

### Result

- LDAP behaved as expected for an authenticated domain user.

- The assessment confirmed correct directory functionality.

---

## Phase 6 — SMB Validation

- SMB testing focused on authorization rather than exploitation.

### Objectives

- Validate authentication.
- Verify departmental access.
- Confirm permission boundaries.

### Activities

- Access to departmental shares was tested using authenticated users.

- Validation confirmed that:

    - Authorized users accessed permitted shares.
    - Unauthorized users were denied access.

- Example:

| Share | HR User |
|---------|:------:|
| HR | ✅ |
| Public | ✅ |
| Finance | ❌ |
| IT | ❌ |

- This demonstrated that both SMB share permissions and NTFS permissions were functioning correctly.

---

## Phase 7 — Group Policy Validation

- The assessment verified that Group Policy Objects were correctly applied to target users.

- Validated configuration included:

    - Password Policy
    - Account Lockout Policy
    - Drive Mapping
    - Control Panel Restriction
    - Command Prompt Restriction
    - Registry Editor Restriction

- Testing confirmed that policy application matched the intended security filtering.

- Administrative users retained appropriate privileges while standard users received the configured restrictions.

---

## Phase 8 — Web Server Assessment

- The Ubuntu server hosted the enterprise web application.

- Assessment activities included:

    - HTTP inspection
    - Header review
    - Web server identification
    - Default endpoint review
    - Directory enumeration

- Apache responded correctly and served the deployed WordPress application.

---

## Phase 9 — WordPress Assessment

- The WordPress deployment was reviewed to understand its exposed functionality.

- Assessment activities included:

    - CMS identification
    - Administrative interface review
    - XML-RPC verification
    - Configuration review
    - Default endpoint validation

- The assessment confirmed that WordPress was functioning correctly within the intended environment.

---

## Evidence Collection

- Evidence was collected throughout the assessment to support every documented observation.

- Evidence included:

    - Network scans
    - DNS queries
    - LDAP query results
    - SMB validation
    - HTTP responses
    - Service identification
    - Administrative screenshots
    - Configuration screenshots

- Supporting evidence is organized within the repository under the `evidence/` and `screenshots/` directories.

---

## Assessment Results

| Assessment Area | Status |
|-----------------|:------:|
| Infrastructure Verification | ✅ |
| Host Discovery | ✅ |
| Service Enumeration | ✅ |
| DNS Validation | ✅ |
| LDAP Validation | ✅ |
| SMB Validation | ✅ |
| Group Policy Validation | ✅ |
| Web Server Assessment | ✅ |
| WordPress Assessment | ✅ |
| Evidence Collection | ✅ |

- The assessment successfully validated the deployed infrastructure and documented the observed security posture.

---

## Limitations

- The assessment was intentionally limited to the MiniCorp laboratory environment.

- The project did not include:

    - External infrastructure
    - Third-party systems
    - Unauthorized testing
    - Malware deployment
    - Persistence mechanisms
    - Privilege escalation
    - Lateral movement
    - Domain compromise

- These exclusions ensure that the documented results accurately reflect the activities performed.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `05-network-services.md` | Enterprise network services |
| `06-group-policy.md` | Group Policy implementation |
| `08-findings.md` | Detailed findings |
| `09-hardening-recommendations.md` | Security improvements |
| `10-mitre-attack-mapping.md` | ATT&CK mapping |

---

## Summary

- The MiniCorp security assessment validated the deployment and configuration of the enterprise environment through a structured methodology covering infrastructure verification, service enumeration, directory services, authorization controls, Group Policy, and web application review.

- Rather than focusing on exploitation, the assessment emphasized configuration validation, evidence collection, and professional documentation. This approach demonstrates how systematic evaluation can be used to verify enterprise security controls while producing reproducible findings and actionable recommendations.
