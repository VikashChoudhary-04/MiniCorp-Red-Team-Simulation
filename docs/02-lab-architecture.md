# Lab Architecture

## Overview

- The MiniCorp environment is a virtual enterprise network designed to simulate a small corporate infrastructure. The architecture combines Windows and Linux systems to provide practical experience with centralized administration, identity management, file services, web application hosting, and structured security assessment.

- The lab is intentionally isolated from production environments and exists solely for education, experimentation, and portfolio development.

---

## Architecture Objectives

- The architecture was designed to achieve the following objectives:

    - Simulate a realistic enterprise environment.
    - Centralize identity and access management.
    - Demonstrate Windows and Linux interoperability.
    - Implement common enterprise network services.
    - Support security assessment activities.
    - Provide a safe environment for learning and experimentation.

---

## Enterprise Topology

- The MiniCorp environment consists of three primary virtual machines connected through an isolated host-only network.

<p align="center">
  <img src="../diagrams/enterprise-network.svg" width="95%" alt="MiniCorp Enterprise Network">
</p>

<p align="center">
  <em>Figure 1. MiniCorp enterprise network topology.</em>
</p>

---

## Virtual Infrastructure

| Virtual Machine | Operating System | Primary Role |
|-----------------|------------------|--------------|
| MiniCorp-DC | Windows Server 2022 | Domain Controller |
| MiniCorp-Client | Windows 10 | Domain-Joined Workstation |
| MiniCorp-Ubuntu | Ubuntu Server 24.04 LTS | Linux Web Server |

---

## Network Design

- The environment uses a dedicated host-only network for internal communication.

| Network | Purpose |
|----------|---------|
| `192.168.192.0/24` | Internal enterprise communication |

- The Ubuntu server also includes a secondary NAT adapter used exclusively for internet access during software installation and package updates.

- This design separates enterprise traffic from internet connectivity while maintaining a controlled assessment environment.

---

## IP Addressing

| System | Address | Role |
|----------|---------|------|
| MiniCorp-DC | `192.168.192.20` | Domain Controller |
| MiniCorp-Client | `192.168.192.30` | Windows Workstation |
| MiniCorp-Ubuntu | `192.168.192.40` | Linux Web Server |

---

## Domain Configuration

| Component | Value |
|-----------|-------|
| Domain Name | `minicorp.local` |
| Forest | `minicorp.local` |
| Authentication | Kerberos |
| Directory Service | Active Directory |
| DNS | Microsoft DNS |

- The Active Directory domain provides centralized authentication, authorization, and directory services for all Windows-based systems within the environment.

---

## System Roles

### MiniCorp-DC

- The Domain Controller serves as the central management system for the enterprise.

- Responsibilities include:

    - Active Directory Domain Services
    - DNS
    - LDAP
    - Kerberos Authentication
    - SMB File Sharing
    - Group Policy Management
    - User and Group Administration
    - Organizational Unit Management

---

### MiniCorp-Client

- The Windows workstation represents a standard enterprise endpoint.

- Responsibilities include:

    - Domain Authentication
    - Group Policy Application
    - Department User Access
    - Drive Mapping
    - Security Policy Enforcement
    - Access Validation

---

### MiniCorp-Ubuntu

- The Ubuntu server provides the Linux infrastructure used for web application hosting.

- Responsibilities include:

    - Apache HTTP Server
    - PHP Runtime
    - MariaDB Database
    - WordPress Deployment
    - OpenSSH Administration

- The server also acts as the primary target during the web application assessment.

---

## Enterprise Services

- The following enterprise services are deployed within the environment.

| Service | Hosted On | Purpose |
|----------|-----------|---------|
| Active Directory | MiniCorp-DC | Identity Management |
| DNS | MiniCorp-DC | Name Resolution |
| LDAP | MiniCorp-DC | Directory Queries |
| Kerberos | MiniCorp-DC | Authentication |
| SMB | MiniCorp-DC | File Sharing |
| Group Policy | MiniCorp-DC | Centralized Configuration |
| Apache | MiniCorp-Ubuntu | Web Hosting |
| MariaDB | MiniCorp-Ubuntu | Database |
| WordPress | MiniCorp-Ubuntu | Web Application |

---

## Authentication Flow

- User authentication follows the standard Active Directory workflow.

```text
User Logon
     │
     ▼
Windows Client
     │
     ▼
Kerberos Authentication
     │
     ▼
Active Directory
     │
     ▼
Authorization
     │
     ▼
Group Membership Evaluation
     │
     ▼
Access to Authorized Resources
```

- This centralized process ensures that authentication and authorization decisions are managed consistently across the environment.

---

## File Access Workflow

- Departmental resources are protected using multiple authorization layers.

```text
User
   │
   ▼
Active Directory Group Membership
   │
   ▼
SMB Share Permissions
   │
   ▼
NTFS Permissions
   │
   ▼
Authorized File Access
```

- This layered model demonstrates defense in depth by requiring both share-level and file system permissions before access is granted.

---

## Assessment Architecture

- The environment was designed to support a structured internal security assessment.

- Assessment activities included:

    - Host discovery
    - Service enumeration
    - DNS validation
    - LDAP enumeration
    - SMB authorization validation
    - Web server assessment
    - WordPress assessment
    - Configuration review

- The architecture intentionally exposes only those services necessary to fulfill each system's intended role.

---

## Design Decisions

- Several architectural decisions were made to improve realism and maintainability.

### Host-Only Enterprise Network

- Using a dedicated host-only network isolates enterprise traffic from the host system while allowing communication between all virtual machines.

---

### Dual-NIC Ubuntu Server

- The Ubuntu server uses:

    - Host-only networking for enterprise communication.
    - NAT networking for package installation and updates.

- This configuration reflects a common administrative pattern while preserving lab isolation.

---

### Centralized Administration

- Identity management, authorization, and policy enforcement are centralized through Active Directory and Group Policy.

- This reduces administrative complexity and provides a consistent security baseline.

---

### Layered Authorization

- Access to shared resources depends on:

    - Active Directory Security Groups
    - SMB Share Permissions
    - NTFS Permissions

- No single control is solely responsible for granting access.

---

## Architecture Summary

- The MiniCorp architecture provides a practical enterprise environment that combines Windows infrastructure, Linux services, centralized identity management, and web application hosting within an isolated virtual network.

- The design supports both administrative tasks and structured security assessments while remaining scalable for future enhancements such as centralized logging, endpoint monitoring, additional servers, or expanded enterprise services.
