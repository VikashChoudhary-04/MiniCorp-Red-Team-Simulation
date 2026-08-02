# Project Overview

## Overview

- MiniCorp is a simulated enterprise environment designed to provide practical experience in enterprise infrastructure deployment, Windows and Linux administration, centralized identity management, and internal security assessment.

- The project recreates a small corporate network using virtual machines to simulate common enterprise services including Active Directory Domain Services (AD DS), Domain Name System (DNS), Lightweight Directory Access Protocol (LDAP), Server Message Block (SMB), Group Policy, and a Linux-based web application stack.

- Unlike projects that focus exclusively on offensive security or systems administration, MiniCorp combines infrastructure engineering with security validation. The environment is designed to demonstrate the complete lifecycle of an enterprise lab—from planning and deployment to assessment, documentation, and hardening.

- All systems, configurations, credentials, assessment activities, and evidence contained in this repository belong exclusively to a privately owned laboratory environment created for educational, research, and portfolio purposes.

---

## Project Objectives

- The primary objectives of MiniCorp are to:

    - Design and deploy a realistic enterprise network.
    - Configure centralized identity and access management using Active Directory.
    - Implement enterprise network services including DNS, LDAP, SMB, and Group Policy.
    - Deploy and administer Windows and Linux systems.
    - Host and maintain a web application using Apache, PHP, MariaDB, and WordPress.
    - Perform an authorized internal security assessment.
    - Validate enterprise security controls.
    - Produce professional technical documentation and assessment reports.
    - Develop practical skills applicable to enterprise IT and cybersecurity roles.

---

## Lab Scope

- The MiniCorp environment represents a small enterprise consisting of three primary systems.

| System | Role |
|----------|------|
| MiniCorp-DC | Windows Server 2022 Domain Controller |
| MiniCorp-Client | Windows 10 Domain Workstation |
| MiniCorp-Ubuntu | Ubuntu Server hosting the web application |

- Together, these systems provide a realistic platform for practicing enterprise administration and conducting structured security assessments.

---

## Project Scope

- MiniCorp covers multiple technical domains that are commonly encountered in enterprise environments.

### Infrastructure

- Virtual machine deployment
- Enterprise network design
- Windows Server administration
- Windows client management
- Linux server administration

---

### Identity and Access Management

- Active Directory Domain Services
- Organizational Units
- User account administration
- Security group management
- Authentication
- Authorization

---

### Enterprise Services

- DNS
- LDAP
- Kerberos
- SMB
- Group Policy

---

### Linux Services

- Apache HTTP Server
- PHP
- MariaDB
- WordPress
- OpenSSH

---

### Security Assessment

- Host discovery
- Service enumeration
- DNS validation
- LDAP assessment
- SMB authorization validation
- Web server assessment
- WordPress assessment
- Configuration review
- Evidence collection

---

## Design Principles

- Several principles guided the design and implementation of the MiniCorp environment.

### Realistic Enterprise Structure

- The environment reflects the architecture of a small organization rather than an intentionally vulnerable laboratory.

- Users, departments, access permissions, and services are configured to resemble common enterprise deployments.

---

### Centralized Administration

- Identity, authentication, authorization, and policy enforcement are managed centrally through Active Directory and Group Policy.

- This demonstrates how enterprise administrators maintain consistent configuration across multiple systems.

---

### Layered Access Control

- Access to shared resources is controlled using multiple layers of authorization.

- These include:

    - Active Directory group membership
    - SMB share permissions
    - NTFS permissions

- This layered approach reflects common enterprise security practices.

---

### Evidence-Based Assessment

- The security assessment emphasizes validation rather than assumption.

- Every observation documented within the project is supported by evidence collected during the assessment.

- Where future improvements are discussed, they are clearly identified as recommendations rather than implemented features.

---

## Learning Outcomes

- Completing the MiniCorp project provides practical experience with:

    - Enterprise infrastructure deployment.
    - Active Directory administration.
    - Windows Server management.
    - Windows client administration.
    - Linux server administration.
    - Identity and access management.
    - DNS, LDAP, and SMB services.
    - Group Policy implementation.
    - Web server deployment.
    - WordPress administration.
    - Internal security assessment.
    - Technical documentation.
    - Security reporting.
    - Hardening recommendations.

---

## Intended Audience

- This repository is intended for:

    - Students learning enterprise administration.
    - Cybersecurity learners building practical skills.
    - Aspiring penetration testers.
    - Security analysts.
    - Windows administrators.
    - Linux administrators.
    - Technical interviewers evaluating practical experience.
    - Recruiters reviewing cybersecurity portfolios.

---

## Technology Summary

| Category | Technologies |
|-----------|--------------|
| Virtualization | VMware Workstation |
| Windows Infrastructure | Windows Server 2022, Windows 10 |
| Linux Infrastructure | Ubuntu Server 24.04 LTS |
| Identity Management | Active Directory Domain Services |
| Network Services | DNS, LDAP, Kerberos, SMB |
| Policy Management | Group Policy |
| Web Stack | Apache, PHP, MariaDB, WordPress |
| Assessment Tools | Nmap, Nikto, Gobuster, ldapsearch, smbclient, curl, dig, nslookup |

---

## Repository Organization

- The repository is organized into several major sections.

| Directory | Purpose |
|------------|---------|
| `docs/` | Technical documentation |
| `diagrams/` | Architecture and workflow diagrams |
| `screenshots/` | Visual evidence |
| `evidence/` | Assessment artifacts |
| `reports/` | Executive and technical reports |
| `scripts/` | Supporting automation scripts |
| `resources/` | Additional reference material |

- Each section is designed to provide a specific type of information while avoiding duplication across the repository.

---

## Related Documentation

- The following documents provide additional technical detail.

| Document | Description |
|----------|-------------|
| `02-lab-architecture.md` | Enterprise architecture and network design |
| `03-active-directory.md` | Active Directory implementation |
| `04-linux-server.md` | Ubuntu Server deployment |
| `05-network-services.md` | DNS, LDAP, SMB, and related services |
| `06-group-policy.md` | Group Policy configuration |
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Security findings |
| `09-hardening-recommendations.md` | Security improvements |
| `10-mitre-attack-mapping.md` | ATT&CK mapping |
| `11-lessons-learned.md` | Project reflections |

---

## Summary

- MiniCorp combines enterprise infrastructure deployment, centralized administration, Linux server management, and structured security assessment into a single cohesive project.

- The environment demonstrates practical implementation of enterprise technologies while emphasizing evidence-based validation, professional documentation, and continuous improvement.

- The following documents explore each component of the environment in greater technical detail.
