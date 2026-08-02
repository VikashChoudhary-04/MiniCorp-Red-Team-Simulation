# Network Services

## Overview

- The MiniCorp enterprise environment relies on several core network services to provide centralized authentication, directory services, name resolution, file sharing, and policy management.

- These services work together to enable communication between Windows and Linux systems while supporting enterprise administration and security assessment activities.

- This document describes the services implemented within the environment, their purpose, their interaction with other components, and how they were validated during the assessment.

---

## Objectives

- The network services implementation was designed to:

    - Provide centralized authentication.
    - Support enterprise name resolution.
    - Enable directory queries.
    - Provide departmental file sharing.
    - Support Group Policy processing.
    - Demonstrate enterprise networking concepts.
    - Provide realistic assessment targets.

---

## Network Services Overview

| Service | Primary Purpose | Hosted On |
|----------|-----------------|-----------|
| DNS | Name Resolution | MiniCorp-DC |
| Active Directory | Identity Management | MiniCorp-DC |
| LDAP | Directory Services | MiniCorp-DC |
| Kerberos | Authentication | MiniCorp-DC |
| SMB | File Sharing | MiniCorp-DC |

- These services collectively provide the foundation of the enterprise environment.

---

## Service Relationships

- The enterprise services interact throughout the authentication and authorization process.

```text
Client
   │
   ▼
DNS
   │
   ▼
Active Directory
   │
   ▼
Kerberos Authentication
   │
   ▼
LDAP Directory Services
   │
   ▼
Group Membership
   │
   ▼
SMB Authorization
   │
   ▼
Department Resources
```

- Each service performs a specific function while supporting the overall enterprise workflow.

---

## DNS

### Purpose

- The Domain Name System (DNS) provides centralized hostname resolution throughout the MiniCorp environment.

- DNS allows clients to locate enterprise services using names instead of IP addresses.

---

### Responsibilities

- DNS provides:

    - Domain name resolution
    - Service discovery
    - Active Directory integration
    - Internal host resolution
  
---

### Implemented Configuration

| Property | Value |
|----------|-------|
| DNS Server | MiniCorp-DC |
| Domain | `minicorp.local` |
| DNS Type | Active Directory Integrated |

---

### Assessment

- DNS validation included:

    - Domain resolution
    - Forward lookup testing
    - Server verification
    - Internal name resolution

- The assessment confirmed that the Active Directory domain resolved correctly using the configured DNS server.

---

## Active Directory

- Active Directory Domain Services provides centralized identity management.

- Responsibilities include:

    - User management
    - Computer management
    - Authentication
    - Authorization
    - Group Policy processing
    - Security group management

- Active Directory serves as the foundation for every Windows-based service within the enterprise.

---

## LDAP

### Purpose

- Lightweight Directory Access Protocol (LDAP) provides access to directory information stored within Active Directory.

- Authenticated users can query directory objects for administrative and operational purposes.

---

### Directory Objects

- The assessment validated access to:

    - User accounts
    - Security groups
    - Organizational Units
    - Distinguished Names
    - Naming Contexts

---

### Assessment

- Authenticated LDAP queries confirmed that:

    - Directory objects were accessible.
    - User objects could be enumerated.
    - Security groups could be enumerated.
    - Naming contexts were correctly configured.

- This behavior is consistent with a functioning Active Directory environment.

---

## Kerberos

### Purpose

- Kerberos provides centralized authentication for domain users.

- Instead of authenticating separately to each service, users authenticate once to Active Directory and receive tickets that can be used to access authorized resources.

---

### Authentication Workflow

```text
User Logon
      │
      ▼
Kerberos Authentication
      │
      ▼
Ticket Granting Ticket (TGT)
      │
      ▼
Service Ticket
      │
      ▼
Authorized Resource
```

---

### Benefits

- Kerberos provides:

    - Centralized authentication
    - Mutual authentication
    - Reduced password transmission
    - Enterprise scalability

- Within the MiniCorp environment, Kerberos supports authentication to domain resources and network services.

---

## SMB

### Purpose

- Server Message Block (SMB) provides centralized file sharing across the enterprise.

- Departmental resources are shared through SMB while access is controlled using Active Directory Security Groups and NTFS permissions.

---

### Implemented Shares

- The environment contains departmental network shares that demonstrate role-based access control.

- Examples include:

    - HR
    - Finance
    - Public

- Access is granted according to departmental group membership.

---

### Authorization Model

- Resource access follows a layered authorization model.

```text
User
   │
   ▼
Kerberos Authentication
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
Access Granted
```

---

### Assessment

- SMB validation confirmed:

    - Successful authentication.
    - Department-based authorization.
    - Correct share permissions.
    - Correct NTFS permissions.

- Example validation:

| Share | HR User |
|---------|:------:|
| HR | ✅ |
| Public | ✅ |
| Finance | ❌ |
| IT | ❌ |

- This demonstrated that access controls were functioning as intended.

---

## Group Policy Dependency

- Several enterprise services rely on DNS, LDAP, Kerberos, and SMB to process Group Policy Objects.

- During user logon:

    1. DNS locates the domain controller.
    2. Kerberos authenticates the user.
    3. LDAP retrieves directory information.
    4. SMB accesses the SYSVOL share.
    5. Group Policy is applied.

- This interaction illustrates how multiple enterprise services work together during standard Windows authentication.

---

## Observed Services

- During service enumeration, additional Windows services associated with Active Directory were identified.

- Examples included:

    - Microsoft RPC
    - Global Catalog
    - WinRM

- These services were observed during network enumeration but were not specifically configured or assessed as part of this project.

---

## Assessment Summary

- The security assessment successfully validated the operation of the implemented enterprise services.

| Service | Validation |
|----------|:----------:|
| DNS | ✅ |
| Active Directory | ✅ |
| LDAP | ✅ |
| Kerberos | ✅ |
| SMB | ✅ |

- The assessment confirmed that the services operated together to provide centralized authentication, authorization, directory access, and file sharing throughout the MiniCorp environment.

---

## Best Practices

- The following practices are recommended for enterprise deployments:

    - Centralize identity management.
    - Maintain accurate DNS records.
    - Regularly review Active Directory permissions.
    - Apply the Principle of Least Privilege.
    - Audit SMB share permissions.
    - Periodically review NTFS permissions.
    - Monitor authentication activity.
    - Keep Windows Server systems updated.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `03-active-directory.md` | Active Directory implementation |
| `06-group-policy.md` | Group Policy configuration |
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Assessment findings |
| `09-hardening-recommendations.md` | Security improvement recommendations |

---

## Summary

- The MiniCorp environment uses Active Directory, DNS, LDAP, Kerberos, and SMB to provide the core services required for centralized enterprise administration.

- Together, these services support authentication, authorization, directory management, policy processing, and departmental resource access while providing a realistic platform for security assessment and enterprise administration.
