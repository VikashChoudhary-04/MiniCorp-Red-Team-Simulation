<div align="center">

# MiniCorp

### Enterprise Infrastructure, Active Directory Administration, and Security Assessment Lab

<p align="center">

![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-0078D6?style=for-the-badge&logo=windows)
![Windows 10](https://img.shields.io/badge/Windows-10-0078D6?style=for-the-badge&logo=windows)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=for-the-badge&logo=ubuntu)
![Apache](https://img.shields.io/badge/Apache-2.4-D22128?style=for-the-badge&logo=apache)
![MariaDB](https://img.shields.io/badge/MariaDB-11.x-003545?style=for-the-badge&logo=mariadb)
![WordPress](https://img.shields.io/badge/WordPress-Latest-21759B?style=for-the-badge&logo=wordpress)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Configured-success?style=for-the-badge)
![Group Policy](https://img.shields.io/badge/Group%20Policy-Implemented-success?style=for-the-badge)
![DNS](https://img.shields.io/badge/DNS-Operational-success?style=for-the-badge)
![LDAP](https://img.shields.io/badge/LDAP-Operational-success?style=for-the-badge)
![SMB](https://img.shields.io/badge/SMB-Configured-success?style=for-the-badge)
![Security Assessment](https://img.shields.io/badge/Security-Assessment-critical?style=for-the-badge)
![VMware](https://img.shields.io/badge/VMware-Workstation-607078?style=for-the-badge)

</p>

**A complete enterprise cybersecurity lab demonstrating infrastructure deployment, centralized identity management, Windows and Linux administration, and an evidence-based internal security assessment.**

</div>

---

## Project at a Glance

| Category | Details |
|-----------|---------|
| **Project Type** | Enterprise Infrastructure & Security Assessment Lab |
| **Environment** | VMware Workstation |
| **Domain** | `minicorp.local` |
| **Domain Controller** | Windows Server 2022 |
| **Client Workstation** | Windows 10 |
| **Linux Server** | Ubuntu Server 24.04 LTS |
| **Web Stack** | Apache, PHP, MariaDB, WordPress |
| **Core Services** | Active Directory, DNS, LDAP, SMB, Group Policy |
| **Assessment Type** | Authorized Internal Security Assessment |
| **Documentation** | Architecture, Configuration, Assessment, Findings, Hardening |

---

## Project Highlights

- Designed and deployed a complete enterprise lab from the ground up.
- Configured an Active Directory domain with Organizational Units, users, security groups, and role-based access control.
- Implemented DNS, LDAP, SMB, NTFS permissions, and Group Policy to simulate centralized enterprise administration.
- Built an Ubuntu Server hosting an Apache, PHP, MariaDB, and WordPress application stack.
- Performed a structured internal security assessment covering network services, directory services, file sharing, and the web application.
- Documented findings, recommendations, and supporting evidence using professional reporting practices.

---

## Implemented Components

| Component | Status |
|-----------|:------:|
| VMware Enterprise Lab | ✅ |
| Windows Server 2022 | ✅ |
| Windows 10 Domain Client | ✅ |
| Ubuntu Server 24.04 LTS | ✅ |
| Active Directory Domain Services | ✅ |
| DNS | ✅ |
| LDAP | ✅ |
| SMB File Sharing | ✅ |
| NTFS Permissions | ✅ |
| Group Policy | ✅ |
| Apache Web Server | ✅ |
| MariaDB | ✅ |
| WordPress | ✅ |
| Internal Security Assessment | ✅ |
| Technical Documentation | ✅ |

---

## Screenshots

> **Note**
>
> The following screenshots provide a visual overview of the MiniCorp environment. Detailed screenshots are available throughout the repository documentation.

| Infrastructure | Windows Administration |
|----------------|------------------------|
| `screenshots/infrastructure/network-overview.png` | `screenshots/active-directory/active-directory-users.png` |

| Group Policy | WordPress |
|---------------|-----------|
| `screenshots/group-policy/drive-mapping.png` | `screenshots/wordpress/dashboard.png` |

| Network Assessment | Directory Services |
|--------------------|--------------------|
| `screenshots/nmap/domain-controller-scan.png` | `screenshots/ldap/ldap-enumeration.png` |

| SMB | Findings |
|------|----------|
| `screenshots/smb/share-validation.png` | `screenshots/findings/apache-server-status.png` |

---

## Table of Contents

- [Overview](#overview)
- [Why MiniCorp?](#why-minicorp)
- [Key Features](#key-features)
- [Enterprise Architecture](#enterprise-architecture)
- [Technology Stack](#technology-stack)
- [Infrastructure Overview](#infrastructure-overview)
- [Security Configuration](#security-configuration)
- [Assessment Methodology](#assessment-methodology)
- [Assessment Summary](#assessment-summary)
- [Key Findings](#key-findings)
- [Hardening Highlights](#hardening-highlights)
- [Skills Demonstrated](#skills-demonstrated)
- [Project Statistics](#project-statistics)
- [Repository Structure](#repository-structure)
- [Documentation Guide](#documentation-guide)
- [Future Improvements](#future-improvements)
- [Lessons Learned](#lessons-learned)
- [Ethics](#ethics)
- [License](#license)

---

## Overview

- MiniCorp is a simulated enterprise environment built to demonstrate practical skills in infrastructure deployment, centralized administration, and security assessment.

- The environment models a small corporate network consisting of a Windows Active Directory domain, a domain-joined Windows workstation, and a Linux web server hosting a WordPress application. Together, these systems provide a realistic platform for learning enterprise administration, validating security configurations, and performing structured security assessments.

- Unlike projects focused solely on exploitation or infrastructure deployment, MiniCorp covers the complete lifecycle of an enterprise lab:

    - Designing the environment.
    - Deploying Windows and Linux systems.
    - Configuring centralized identity and access management.
    - Implementing enterprise services.
    - Performing an authorized security assessment.
    - Documenting observations and recommendations using professional reporting practices.

- All systems, credentials, configurations, assessment activities, and evidence contained in this repository belong exclusively to a privately owned laboratory environment created for educational and portfolio purposes.

---

## Why MiniCorp?

- Many cybersecurity projects focus on a single technology or a specific security tool. MiniCorp was designed to integrate multiple enterprise technologies into a cohesive environment that reflects common administrative and security workflows.

- The project emphasizes practical implementation rather than isolated demonstrations. It combines Windows Server administration, Linux server deployment, identity management, access control, network services, and security assessment into a single, documented environment.

- This approach provides experience with both building and assessing enterprise infrastructure while maintaining a clear distinction between system administration tasks and security evaluation.

---

## Key Features

- Enterprise Active Directory deployment.
- Windows Server 2022 administration.
- Windows 10 domain integration.
- Ubuntu Server deployment and administration.
- Apache, PHP, MariaDB, and WordPress installation.
- Active Directory Users and Computers (ADUC) management.
- Organizational Unit (OU) design.
- Security group management.
- Department-based access control.
- NTFS permission management.
- SMB share configuration.
- DNS and LDAP services.
- Group Policy configuration and enforcement.
- Internal security assessment methodology.
- Evidence-based findings and hardening recommendations.
- Comprehensive technical documentation.

---

## Enterprise Architecture

- The MiniCorp environment simulates a small enterprise network consisting of centralized identity management, managed Windows endpoints, and Linux-based web infrastructure. The architecture is intentionally designed to demonstrate enterprise administration concepts alongside practical security assessment techniques.

> **Note**
>
> A professional architecture diagram (`diagrams/enterprise-network.svg`) will be included in the final repository and referenced throughout the documentation.

<p align="center">
  <img src="diagrams/enterprise-network.svg" width="95%" alt="MiniCorp Enterprise Network Architecture">
</p>

<p align="center">
  <em>Figure 1. MiniCorp Enterprise Network Architecture.</em>
</p>

---

## Technology Stack

### Infrastructure

| Category | Technology |
|-----------|------------|
| Hypervisor | VMware Workstation |
| Domain Controller | Windows Server 2022 |
| Client Workstation | Windows 10 |
| Linux Server | Ubuntu Server 24.04 LTS |

---

### Identity & Access Management

| Component | Technology |
|-----------|------------|
| Directory Service | Active Directory Domain Services |
| Domain | `minicorp.local` |
| Authentication | Kerberos |
| Directory Queries | LDAP |
| Authorization | Active Directory Security Groups |
| Access Control | NTFS Permissions & SMB Share Permissions |
| Policy Management | Group Policy |

---

### Network Services

| Service | Technology |
|----------|------------|
| DNS | Microsoft DNS |
| SMB | Microsoft SMB |
| File Sharing | Windows File Services |
| Remote Administration | OpenSSH (Ubuntu) |

---

### Web Platform

| Component | Technology |
|-----------|------------|
| Operating System | Ubuntu Server 24.04 LTS |
| Web Server | Apache HTTP Server |
| Runtime | PHP |
| Database | MariaDB |
| Content Management System | WordPress |

---

### Assessment Tools

| Tool | Purpose |
|------|---------|
| Nmap | Host discovery, service detection, port scanning |
| Nikto | Web server assessment |
| Gobuster | Content and directory enumeration |
| curl | Manual HTTP inspection |
| ldapsearch | LDAP enumeration |
| smbclient | SMB enumeration and validation |
| nslookup | DNS testing |
| dig | DNS interrogation |

---

## Infrastructure Overview

- The MiniCorp environment consists of three primary virtual machines connected through an isolated virtual network. Each machine performs a dedicated enterprise role while interacting with the others through standard Windows and Linux services.

| System | Role | IP Address |
|---------|------|------------|
| MiniCorp-DC | Domain Controller | `192.168.192.20` |
| MiniCorp-Client | Domain-Joined Workstation | `192.168.192.30` |
| MiniCorp-Ubuntu | Linux Web Server | `192.168.192.40` |

---

## Windows Domain Controller

- The Domain Controller serves as the core of the enterprise environment, providing centralized authentication, authorization, policy enforcement, and name resolution for all domain-joined systems.

### Configured Services

| Service | Purpose |
|----------|---------|
| Active Directory Domain Services | Centralized identity management |
| DNS | Domain name resolution |
| LDAP | Directory access |
| Kerberos | Authentication |
| SMB | Network file sharing |
| SYSVOL | Group Policy replication |
| NETLOGON | Logon services |
| Group Policy Management | Centralized policy administration |

---

## Active Directory Structure

- The Active Directory implementation models a departmental organizational structure commonly found in enterprise environments.

### Organizational Units

- HR
- Finance
- IT
- Sales
- Servers
- Workstations

### Security Groups

- HR_Users
- Finance_Users
- Sales_Users
- IT_Admins
- Domain Admins
- Server_Admins
- Workstation_Admins

### Example Users

- Alice Johnson
- Bob Smith
- Charlie Brown
- David Wilson

Access to enterprise resources is controlled through Active Directory group membership combined with NTFS and SMB permissions.

---

## Windows Client

- The Windows client represents a managed enterprise workstation joined to the Active Directory domain.

- The system is used to validate centralized administration, authentication, authorization, and Group Policy enforcement.

### Configured Features

- Domain Join
- Department User Accounts
- Group Policy Application
- Drive Mapping
- Department-based Access Control
- Registry Restrictions
- Command Prompt Restrictions
- Control Panel Restrictions

The workstation demonstrates how centralized administration can enforce consistent security settings across managed devices.

---

## Ubuntu Server

- The Ubuntu server represents an internally hosted Linux web server providing a typical LAMP-style web application environment.

- It hosts the enterprise web application assessed during the security evaluation.

### Installed Components

| Component | Purpose |
|-----------|---------|
| Ubuntu Server 24.04 LTS | Operating System |
| Apache HTTP Server | Web Server |
| PHP | Server-side Runtime |
| MariaDB | Database |
| WordPress | Web Application |
| OpenSSH | Remote Administration |

---

### Network Configuration

- The Ubuntu server uses two network interfaces.

| Interface | Purpose |
|-----------|---------|
| Host-Only Adapter | Communication with the MiniCorp enterprise network |
| NAT Adapter | Internet connectivity for package installation and updates |

Separating internal communication from external connectivity reflects a common enterprise deployment pattern.

---

## Network Design

- The MiniCorp lab uses an isolated host-only network to simulate internal enterprise communication while allowing the Ubuntu server to access the internet through a separate NAT adapter for software installation and maintenance.

| Network | Purpose |
|----------|---------|
| `192.168.192.0/24` | Internal enterprise network |
| NAT Network | Internet access for Ubuntu updates |

- This design enables controlled interaction between all virtual machines while maintaining separation from the host environment.

---

## Active Directory Administration

- The project demonstrates practical administration of an Active Directory environment, including user lifecycle management, organizational design, and centralized authorization.

- Implemented administrative tasks include:

    - Domain creation
    - Organizational Unit management
    - User account creation
    - Security group administration
    - Group membership management
    - Department-based access control
    - File share authorization
    - NTFS permission management

- These tasks reflect common responsibilities performed by Windows administrators in enterprise environments.

---

## Windows Administration

- The Windows administration component focuses on centralized management through Group Policy and Active Directory.

- Implemented configuration includes:

    - Password Policy
    - Account Lockout Policy
    - Interactive Logon Banner
    - Drive Mapping
    - Registry Restrictions
    - Command Prompt Restrictions
    - Control Panel Restrictions
    - User-based Group Policy Filtering

- The configuration demonstrates how enterprise environments enforce security policies consistently across managed workstations.

---

## Linux Administration

- The Linux administration component focuses on deploying and maintaining a production-style web server.

- Administrative tasks include:

    - Ubuntu Server installation
    - Static network configuration
    - Apache deployment
    - MariaDB installation
    - WordPress deployment
    - OpenSSH configuration
    - Package management
    - Service administration

- These tasks provide practical experience with Linux server deployment and maintenance within an enterprise environment.

---

## Security Configuration

- The MiniCorp environment incorporates multiple security controls that demonstrate centralized administration and enterprise access management. These controls were implemented to simulate common organizational security policies while providing a realistic environment for validation during the security assessment.

### Identity and Access Management

- Authentication and authorization are centralized through Active Directory Domain Services.

- Implemented controls include:

    - Centralized user authentication
    - Department-based authorization
    - Security group management
    - Organizational Unit (OU) separation
    - Role-based access control
    - Centralized account management

---

### Group Policy

- Group Policy is used to enforce consistent configuration across domain-joined systems.

- Implemented policies include:

| Policy | Purpose |
|----------|---------|
| Password Policy | Enforce password complexity and length |
| Account Lockout Policy | Mitigate password guessing attacks |
| Interactive Logon Banner | Display organizational security notice |
| Drive Mapping | Automatically map departmental network shares |
| Registry Restrictions | Prevent unauthorized registry modification |
| Command Prompt Restrictions | Limit access to the command interpreter |
| Control Panel Restrictions | Restrict access to system configuration |
| User-based Filtering | Apply policies to specific security groups |

---

### File Sharing and Authorization

- Departmental resources are shared using SMB while authorization is enforced through a combination of:

    - Active Directory Security Groups
    - SMB Share Permissions
    - NTFS Permissions

- This layered approach ensures that users can only access resources explicitly assigned to their departmental roles.

---

### Network Services

- Core enterprise services include:

| Service | Purpose |
|----------|---------|
| DNS | Name resolution |
| LDAP | Directory queries |
| Kerberos | Authentication |
| SMB | File sharing |
| Group Policy | Centralized configuration |

- Together, these services provide the foundation for enterprise identity management and administration.

---

## Assessment Methodology

- Following infrastructure deployment, a structured internal security assessment was performed against the MiniCorp environment.

- The assessment focused on validating service configurations, identifying exposed attack surfaces, verifying authorization controls, and documenting evidence-based observations.

> **Important**
>
> All assessment activities were performed exclusively within the isolated MiniCorp laboratory environment.

---

## Assessment Scope

### Systems Assessed

| System | Assessment Areas |
|----------|------------------|
| MiniCorp-DC | DNS, LDAP, SMB, Active Directory Services |
| MiniCorp-Client | Group Policy, Access Control Validation |
| MiniCorp-Ubuntu | Apache, WordPress, Web Server Configuration |

---

### Assessment Objectives

- The assessment sought to:

    - Identify exposed network services.
    - Validate Active Directory functionality.
    - Verify DNS operation.
    - Assess LDAP accessibility.
    - Validate SMB authorization.
    - Review web server configuration.
    - Assess the deployed WordPress application.
    - Document observations and recommendations.

---

## Assessment Workflow

- The assessment followed a structured workflow designed to progress from discovery to validation and reporting.

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
DNS Assessment
        │
        ▼
LDAP Assessment
        │
        ▼
SMB Assessment
        │
        ▼
Web Server Assessment
        │
        ▼
WordPress Assessment
        │
        ▼
Configuration Review
        │
        ▼
Evidence Collection
        │
        ▼
Security Findings
        │
        ▼
Hardening Recommendations
```

---

## Assessment Tools

| Tool | Primary Use |
|------|-------------|
| Nmap | Host discovery and service enumeration |
| Nikto | Web server assessment |
| Gobuster | Directory enumeration |
| curl | HTTP inspection |
| ldapsearch | LDAP enumeration |
| smbclient | SMB validation |
| nslookup | DNS resolution testing |
| dig | DNS interrogation |

---

## Network Enumeration

- The assessment began with host discovery and service identification across the MiniCorp environment.

- Known enterprise systems were individually assessed to identify exposed services and verify expected functionality.

### Enumerated Hosts

| Host | Operating System | Role |
|------|------------------|------|
| MiniCorp-DC | Windows Server 2022 | Domain Controller |
| MiniCorp-Client | Windows 10 | Domain Workstation |
| MiniCorp-Ubuntu | Ubuntu Server 24.04 LTS | Web Server |

---

## Service Validation

- Enumeration confirmed services consistent with the intended roles of each system.

### MiniCorp-DC

- Observed enterprise services included:

- DNS
- Kerberos
- LDAP
- SMB
- Global Catalog
- Microsoft RPC
- WinRM

### MiniCorp-Ubuntu

- Observed services included:

    - SSH
    - HTTP

- No unexpected services were identified during the assessment.

---

## DNS Assessment

- The assessment verified the operation of the Active Directory integrated DNS service.

- Validation included:

    - Domain resolution
    - Forward lookup testing
    - Authoritative responses
    - Internal name resolution

- The assessment confirmed successful resolution of the Active Directory domain and expected DNS behavior.

---

## LDAP Assessment

- Authenticated LDAP queries were performed using standard domain credentials.

- The assessment verified access to expected directory information including:

    - User objects
    - Security groups
    - Organizational Units
    - Distinguished Names
    - Naming Contexts

- This demonstrated the information available to authenticated domain users while validating directory functionality.

---

## SMB Assessment

- SMB testing focused on validating departmental authorization rather than identifying misconfigurations.

- Authenticated access confirmed that share permissions aligned with Active Directory group membership.

### Example Validation

| Share | HR User |
|---------|:------:|
| HR | ✅ |
| Public | ✅ |
| Finance | ❌ |
| IT | ❌ |

- This confirmed the correct implementation of:

    - Department-based authorization
    - SMB Share Permissions
    - NTFS Permissions
    - Active Directory Security Groups

---

## Web Application Assessment

- The Ubuntu server hosted a WordPress application deployed on Apache with MariaDB.

- The assessment focused on:

    - Web server identification
    - HTTP response inspection
    - Content discovery
    - Default endpoint verification
    - Configuration review

---

### Technologies Identified

| Component | Technology |
|------------|------------|
| Operating System | Ubuntu Server |
| Web Server | Apache HTTP Server |
| Runtime | PHP |
| Database | MariaDB |
| CMS | WordPress |

---

### HTTP Review

- Manual HTTP inspection confirmed:

    - Successful HTTP responses
    - Standard Apache behavior
    - WordPress application deployment
    - Expected administrative endpoints

- The Apache `server-status` endpoint was also identified during configuration review and documented as a security observation.

---

## Assessment Summary

- The assessment successfully validated the intended operation of the MiniCorp environment while documenting configuration observations and authorization behavior.

| Assessment Area | Status |
|-----------------|:------:|
| Network Enumeration | ✅ |
| Service Identification | ✅ |
| DNS Validation | ✅ |
| LDAP Validation | ✅ |
| SMB Authorization Validation | ✅ |
| Group Policy Validation | ✅ |
| Web Server Assessment | ✅ |
| WordPress Assessment | ✅ |
| Configuration Review | ✅ |
| Evidence Collection | ✅ |

- The assessment demonstrated that the enterprise environment was functioning as designed while providing realistic opportunities to evaluate common administrative services and security configurations.

---

### Key Findings

- The security assessment identified several observations related to service configuration, application exposure, and enterprise security posture. Unless otherwise stated, all findings were identified within the isolated MiniCorp laboratory environment.

| ID | Finding | Severity | Status |
|----|----------|:--------:|:------:|
| MC-001 | Apache `server-status` endpoint accessible | Low | Documented |
| MC-002 | WordPress administrative interface exposed | Informational | Documented |
| MC-003 | WordPress XML-RPC endpoint available | Informational | Documented |
| MC-004 | Departmental SMB authorization functioning as intended | Positive | Validated |
| MC-005 | Active Directory integrated DNS functioning correctly | Positive | Validated |
| MC-006 | Authenticated LDAP directory enumeration available | Informational | Documented |

> **Note**
>
> Complete finding details, supporting evidence, risk analysis, and remediation guidance are available in [`docs/08-findings.md`](docs/08-findings.md).

---

## Hardening Highlights

- The assessment concluded with several recommendations to improve the security posture of the environment while preserving functionality.

### Windows Infrastructure

- Apply the Principle of Least Privilege for administrative accounts.
- Regularly review Active Directory group memberships.
- Audit delegated permissions.
- Enable advanced auditing for authentication and policy changes.
- Monitor privileged account activity.

---

### Group Policy

- Periodically review all Group Policy Objects.
- Validate security filtering.
- Remove obsolete policies.
- Test policy changes before production deployment.

---

### SMB

- Audit share permissions regularly.
- Review NTFS permissions.
- Remove unnecessary shared folders.
- Enable SMB signing where appropriate.

---

### Linux Server

- Restrict access to Apache administrative endpoints.
- Keep operating system packages updated.
- Monitor Apache and authentication logs.
- Limit SSH access to authorized administrators.

---

### WordPress

- Enable automatic updates.
- Remove unused plugins and themes.
- Enforce strong administrator passwords.
- Enable Multi-Factor Authentication where appropriate.
- Disable XML-RPC if not required.

> **Note**
>
> Detailed recommendations are available in [`docs/09-hardening-recommendations.md`](docs/09-hardening-recommendations.md).

---

## MITRE ATT&CK Mapping

- The assessment activities can be mapped to relevant MITRE ATT&CK techniques to provide defensive context.

| Assessment Activity | ATT&CK Technique |
|---------------------|------------------|
| Network Service Discovery | T1046 |
| System Network Configuration Discovery | T1016 |
| Remote System Discovery | T1018 |
| Account Discovery | T1087 |
| File and Directory Discovery | T1083 |
| Network Share Discovery | T1135 |
| Active Scanning | T1595 |

> **Note**
>
> This mapping is intended to relate assessment activities to the ATT&CK framework. It does not imply adversary emulation.

---

## Skills Demonstrated

| Domain | Skills |
|----------|---------|
| Enterprise Infrastructure | VMware Workstation, Windows Server 2022, Windows 10, Ubuntu Server |
| Windows Administration | Active Directory, ADUC, Organizational Units, Security Groups |
| Identity & Access Management | Kerberos, LDAP, Group Membership, Role-Based Access Control |
| Group Policy | Password Policy, Account Lockout, Drive Mapping, User Restrictions |
| File Services | SMB, NTFS Permissions, Departmental Shares |
| Linux Administration | Apache, PHP, MariaDB, WordPress, OpenSSH |
| Networking | DNS, LDAP, SMB, TCP/IP, HTTP |
| Security Assessment | Enumeration, Configuration Review, Authorization Validation |
| Documentation | Technical Writing, Evidence Collection, Findings, Recommendations |

---

## Project Statistics

| Metric | Value |
|---------|------:|
| Virtual Machines | 3 |
| Operating Systems | 3 |
| Active Directory Domain | 1 |
| Organizational Units | 6 |
| Security Groups | 7+ |
| Department Users | 4 |
| SMB Shares | Multiple |
| Core Infrastructure Services | 5 |
| Assessment Tools Used | 8 |
| Assessment Areas | 9 |
| Findings Documented | 6 |

---

## Repository Structure

```text
MiniCorp/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── docs/
├── diagrams/
├── screenshots/
├── evidence/
├── reports/
├── scripts/
└── resources/
```

- A complete explanation of each directory is provided within the project documentation.

---

## Documentation Guide

| Document | Description |
|----------|-------------|
| `01-project-overview.md` | Project goals, scope, and learning objectives |
| `02-lab-architecture.md` | Enterprise architecture and network design |
| `03-active-directory.md` | Active Directory implementation |
| `04-linux-server.md` | Ubuntu Server deployment and web stack |
| `05-network-services.md` | DNS, LDAP, SMB, and supporting services |
| `06-group-policy.md` | Group Policy implementation |
| `07-security-assessment.md` | Assessment methodology and execution |
| `08-findings.md` | Detailed findings and evidence |
| `09-hardening-recommendations.md` | Security improvement recommendations |
| `10-mitre-attack-mapping.md` | MITRE ATT&CK mapping |
| `11-lessons-learned.md` | Key project takeaways |

---

## Future Improvements

- Potential future enhancements include:

    - Windows Event Forwarding
    - Sysmon deployment
    - Microsoft Defender integration
    - Wazuh integration
    - SIEM log collection
    - Additional Linux servers
    - Active Directory Certificate Services
    - Internal PKI
    - IIS deployment
    - Automated compliance auditing
    - Infrastructure-as-Code deployment

- These enhancements are intentionally listed as future work and are **not** part of the current implementation.

---

## Lessons Learned

- Building MiniCorp reinforced the importance of integrating infrastructure deployment, centralized administration, and structured security assessment into a single workflow.

- The project provided practical experience with enterprise identity management, Windows administration, Linux server deployment, network services, access control, and technical reporting. It also demonstrated the value of documenting evidence, validating observations, and presenting recommendations in a clear and reproducible manner.

- Perhaps the most significant outcome was understanding that effective security assessments depend not only on technical testing but also on accurate documentation and well-supported conclusions.

---

## Ethics

- This project was designed, deployed, administered, and assessed exclusively within a privately owned laboratory environment.

- No third-party infrastructure, organizations, or individuals were targeted during the creation of this repository.

- The techniques documented throughout this project are intended solely for:

    - Authorized security assessments
    - Enterprise administration training
    - Defensive security validation
    - Cybersecurity education
    - Research within controlled environments

- Always obtain explicit authorization before assessing systems you do not own or administer.

---

## License

- This project is licensed under the **MIT License**.

- See the [LICENSE](LICENSE) file for the full license text.

---

<div align="center">

**MiniCorp**

*Enterprise Infrastructure, Active Directory Administration, and Security Assessment Lab*

Built for learning, administration, assessment, and professional cybersecurity portfolio development.

</div>
