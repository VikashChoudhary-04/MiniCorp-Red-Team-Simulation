# Active Directory

## Overview

- Active Directory Domain Services (AD DS) provides the centralized identity and access management platform for the MiniCorp enterprise environment.

- Within the lab, Active Directory is responsible for authenticating users, authorizing access to enterprise resources, applying Group Policy Objects (GPOs), and managing directory objects such as users, groups, computers, and Organizational Units (OUs).

- The implementation follows a departmental structure representative of a small enterprise and demonstrates common Windows Server administration tasks.

---

## Objectives

- The Active Directory implementation was designed to:

    - Centralize user authentication.
    - Centralize authorization.
    - Organize enterprise resources.
    - Simplify administrative management.
    - Implement role-based access control.
    - Demonstrate enterprise administration practices.
    - Support security assessment activities.

---

## Domain Information

| Property | Value |
|----------|-------|
| Domain Name | `minicorp.local` |
| Forest | `minicorp.local` |
| Domain Controller | MiniCorp-DC |
| Operating System | Windows Server 2022 |
| Authentication Protocol | Kerberos |
| Directory Service | LDAP |

---

## Active Directory Components

- The domain controller hosts several enterprise services that work together to provide centralized administration.

| Component | Purpose |
|-----------|---------|
| Active Directory Domain Services | Identity management |
| DNS | Name resolution |
| LDAP | Directory queries |
| Kerberos | Authentication |
| Group Policy | Centralized configuration |
| SMB | File sharing |

---

## Organizational Unit Structure

- The directory is organized into Organizational Units (OUs) to separate administrative responsibilities and simplify policy management.

### Organizational Units

| Organizational Unit | Purpose |
|---------------------|---------|
| HR | Human Resources users |
| Finance | Finance department users |
| IT | IT administrators and staff |
| Sales | Sales department users |
| Servers | Server computer objects |
| Workstations | Client computer objects |

- This structure enables policies and permissions to be applied to groups of related objects instead of individual users.

---

## User Accounts

- Departmental user accounts were created to represent employees within the organization.

| User | Department |
|------|------------|
| Alice Johnson | HR |
| Bob Smith | Finance |
| Charlie Brown | IT |
| David Wilson | Sales |

- These accounts were used to validate authentication, authorization, Group Policy application, and departmental resource access.

---

## Security Groups

- Security groups simplify permission management by assigning access rights to groups rather than individual users.

| Security Group | Purpose |
|----------------|---------|
| HR_Users | HR department access |
| Finance_Users | Finance department access |
| Sales_Users | Sales department access |
| IT_Admins | Administrative access for IT staff |
| Domain Admins | Full domain administration |
| Server_Admins | Server management |
| Workstation_Admins | Workstation administration |

- This model improves scalability and follows common enterprise administration practices.

---

## Authentication

- Authentication is performed using Kerberos.

- The authentication process includes:

    1. User logon.
    2. Credential validation.
    3. Kerberos ticket issuance.
    4. Access token creation.
    5. Group membership evaluation.
    6. Resource authorization.

- This centralized workflow ensures users authenticate once before accessing authorized enterprise resources.

---

## Authorization

- Authorization decisions are based on Active Directory group membership.

- When users access network resources:

    1. Active Directory identifies the user.
    2. Security groups are evaluated.
    3. SMB permissions are checked.
    4. NTFS permissions are verified.
    5. Access is granted or denied.

- This layered authorization model supports the Principle of Least Privilege.

---

## Resource Access Model

- Departmental resources are protected using multiple authorization layers.

```text
User
   │
   ▼
Active Directory Authentication
   │
   ▼
Security Group Membership
   │
   ▼
SMB Share Permissions
   │
   ▼
NTFS Permissions
   │
   ▼
Resource Access
```

- No single permission layer independently grants access.

---

## Group Policy Integration

- Active Directory integrates with Group Policy to provide centralized configuration management.

- Implemented policies include:

    - Password Policy
    - Account Lockout Policy
    - Interactive Logon Banner
    - Drive Mapping
    - Registry Restrictions
    - Command Prompt Restrictions
    - Control Panel Restrictions
    - User-based Security Filtering

- These policies demonstrate how administrators can maintain consistent configurations across domain-joined systems.

---

## Directory Services

- LDAP provides authenticated access to directory information.

- The assessment validated access to:

    - User objects
    - Group objects
    - Organizational Units
    - Distinguished Names
    - Naming Contexts

- This functionality supports administrative operations while demonstrating the visibility available to authenticated domain users.

---

## Administrative Tasks Performed

- The project included practical administration of Active Directory using standard Windows Server management tools.

- Completed tasks include:

    - Domain creation
    - Organizational Unit creation
    - User account creation
    - Security group creation
    - Group membership management
    - Computer account management
    - Group Policy creation
    - Group Policy linking
    - Group Policy filtering
    - SMB share administration
    - NTFS permission management

- These activities reflect common responsibilities performed by Windows administrators.

---

## Security Considerations

- Several security practices were implemented throughout the Active Directory environment.

- Examples include:

    - Department-based authorization.
    - Group-based permission management.
    - Centralized policy enforcement.
    - Password policy configuration.
    - Account lockout policy.
    - Restricted administrative privileges.
    - Layered file access controls.

- Together, these measures help reduce administrative complexity while improving security.

---

## Best Practices

- The following practices were followed during implementation:

    - Use Organizational Units to separate administrative boundaries.
    - Assign permissions through security groups instead of individual users.
    - Apply the Principle of Least Privilege.
    - Use Group Policy for centralized configuration.
    - Combine SMB permissions with NTFS permissions.
    - Review administrative memberships regularly.
    - Audit policy changes periodically.

- These practices align with common enterprise administration recommendations.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `02-lab-architecture.md` | Enterprise architecture |
| `05-network-services.md` | DNS, LDAP, SMB services |
| `06-group-policy.md` | Group Policy implementation |
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Assessment findings |

---

## Summary

- Active Directory serves as the foundation of the MiniCorp enterprise environment by providing centralized identity management, authentication, authorization, and policy enforcement.

- The implementation demonstrates practical Windows Server administration through the creation and management of Organizational Units, users, security groups, Group Policy Objects, and departmental access controls.

- Together with DNS, LDAP, SMB, and Group Policy, Active Directory enables consistent administration and secure access to enterprise resources while supporting the structured security assessment documented throughout this repository.
