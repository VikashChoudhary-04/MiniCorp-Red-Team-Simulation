# Group Policy

## Overview

- Group Policy provides centralized configuration management for domain-joined systems within the MiniCorp enterprise environment.

- Using Group Policy Objects (GPOs), administrators can enforce security settings, configure user environments, and manage Windows workstations without requiring manual configuration on individual systems.

- The MiniCorp implementation demonstrates practical Group Policy administration through policy creation, linking, security filtering, delegation, and validation.

---

## Objectives

- The Group Policy implementation was designed to:

    - Centralize workstation configuration.
    - Enforce enterprise security settings.
    - Demonstrate policy deployment.
    - Restrict unauthorized user actions.
    - Automate departmental drive mapping.
    - Validate policy application.
    - Support enterprise administration.

---

## Group Policy Architecture

```text
Administrator
      │
      ▼
Group Policy Management
      │
      ▼
Group Policy Object (GPO)
      │
      ▼
Linked Organizational Unit
      │
      ▼
Security Filtering
      │
      ▼
Domain User
      │
      ▼
Policy Applied
```

---

## Implemented Group Policy Objects

- Two primary Group Policy Objects were implemented within the MiniCorp environment.

| Group Policy Object | Purpose |
|---------------------|---------|
| MiniCorp Workstation Security | Centralized workstation security configuration |
| MiniCorp Drive Mapping | Departmental network drive mapping |

---

## Group Policy Linking

- The implemented GPOs were linked to the appropriate Organizational Units within Active Directory.

- Linking ensures that policies are processed only for the intended users and computers.

- The assessment confirmed:

    - Successful GPO linking.
    - Link Enabled configuration.
    - GPO Status enabled.
    - Successful application to target users.

---

## Security Filtering

- Security filtering was used to control which users received specific policies.

- Examples include:

    - HR_Users
    - Finance_Users
    - Sales_Users

- The assessment confirmed that policies were applied only to users who met the required filtering criteria.

---

## Delegation

- Appropriate permissions were delegated to allow Group Policy processing.

- Validated permissions included:

    - Read
    - Apply Group Policy

- These permissions were assigned to the relevant security groups to ensure correct policy application.

---

## Password Policy

- Password policies were configured to strengthen account security.

- The implemented policy demonstrates centralized password management through Active Directory Group Policy.

- Examples include:

    - Password complexity
    - Password length
    - Password management settings

- Password policies help reduce the risk of weak credentials across enterprise systems.

---

## Account Lockout Policy

- Account lockout policies were configured to reduce the effectiveness of password guessing attacks.

- The implementation demonstrates how centralized policies can protect enterprise accounts from repeated authentication failures.

---

## Drive Mapping

- The MiniCorp Drive Mapping Group Policy automatically maps departmental network resources for authorized users.

- Benefits include:

    - Consistent user experience.
    - Centralized administration.
    - Reduced manual configuration.
    - Department-specific resource access.

- Drive mapping was successfully validated during testing.

---

## Workstation Restrictions

- Several user restrictions were implemented to demonstrate centralized workstation security.

### Control Panel Restriction

- Control Panel access was restricted for standard departmental users.

- Validation confirmed:

| User | Result |
|------|:------:|
| Alice Johnson | Restricted |
| Bob Smith | Restricted |
| David Wilson | Restricted |
| Charlie Brown | Allowed |

- This behavior reflects the intended security policy for the environment.

---

### Command Prompt Restriction

- Command Prompt access was restricted for standard users.

- Validation confirmed:

| User | Result |
|------|:------:|
| Alice Johnson | Restricted |
| Charlie Brown | Allowed |

- This demonstrates how Group Policy can differentiate administrative users from standard users.

---

### Registry Editor Restriction

- Registry Editor access was restricted for standard users.

- Validation confirmed:

| User | Result |
|------|:------:|
| Alice Johnson | Restricted |
| Charlie Brown | Allowed |

- Restricting Registry Editor reduces the likelihood of unauthorized system configuration changes.

---

## Group Policy Validation

- Policy application was verified using standard Windows administration tools.

- Validation activities included:

    - Reviewing applied Group Policy Objects.
    - Confirming security filtering.
    - Verifying delegated permissions.
    - Testing user restrictions.
    - Validating drive mapping.

- The assessment confirmed successful policy application across the intended users.

---

## Administrative Tasks Performed

- The project included the following Group Policy administration tasks:

    - Creating Group Policy Objects.
    - Linking GPOs.
    - Configuring security filtering.
    - Configuring delegation.
    - Implementing workstation restrictions.
    - Implementing drive mapping.
    - Verifying policy application.
    - Testing user access.

- These activities reflect common enterprise Windows administration responsibilities.

---

## Security Benefits

- Centralized Group Policy management provides several security advantages.

- Examples include:

    - Consistent workstation configuration.
    - Reduced administrative overhead.
    - Centralized policy enforcement.
    - Standardized user experience.
    - Reduced opportunity for unauthorized configuration changes.

---

## Best Practices

- The following practices were followed during implementation:

    - Apply policies through Organizational Units.
    - Use security groups for filtering.
    - Test policies before deployment.
    - Review delegated permissions.
    - Keep policies organized by function.
    - Remove unused Group Policy Objects.
    - Document policy purpose and scope.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `03-active-directory.md` | Active Directory implementation |
| `05-network-services.md` | Enterprise services |
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Security findings |

---

## Summary

- Group Policy provides centralized configuration management throughout the MiniCorp environment.

- The implementation demonstrates practical administration through policy creation, security filtering, delegation, workstation restrictions, and automated drive mapping.

- Assessment activities confirmed that policies were successfully applied to their intended users while preserving administrative access where appropriate. Together with Active Directory, Group Policy forms a core component of the centralized management model implemented within MiniCorp.
