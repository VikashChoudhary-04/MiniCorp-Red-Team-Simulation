# Hardening Recommendations

## Overview

- This document provides security recommendations based on the observations made during the MiniCorp security assessment.

- The recommendations are intended to improve the overall security posture of the environment while maintaining functionality and administrative usability.

- Unless otherwise stated, the recommendations represent future improvements and are **not** claimed as implemented within the current version of the MiniCorp environment.

---

## Objectives

- The recommendations aim to:

    - Reduce attack surface.
    - Strengthen authentication.
    - Improve authorization.
    - Protect enterprise services.
    - Improve monitoring.
    - Support secure administration.
    - Encourage long-term maintainability.

---

## Recommendation Priorities

| Priority | Description |
|----------|-------------|
| High | Should be implemented as soon as possible. |
| Medium | Improves overall security posture. |
| Low | Long-term enhancements and operational improvements. |

---

## Windows Infrastructure

### High Priority

#### Apply the Principle of Least Privilege

- Administrative rights should be granted only to users who require them.

- Recommended actions:

    - Limit Domain Admin membership.
    - Use dedicated administrative accounts.
    - Remove unnecessary administrative privileges.

---

#### Review Administrative Group Membership

- Administrative groups should be reviewed regularly.

- Examples include:

    - Domain Admins
    - Server_Admins
    - Workstation_Admins

- Periodic reviews reduce the likelihood of privilege creep.

---

### Medium Priority

#### Enable Advanced Auditing

- Recommended audit categories include:

    - Account Logon
    - Account Management
    - Logon Events
    - Object Access
    - Policy Changes
    - Privilege Use

- Centralized auditing improves visibility into administrative activity.

---

#### Regular Patch Management

- Maintain Windows Server and Windows clients with current security updates.

- Routine patching reduces exposure to known vulnerabilities.

---

## Active Directory

### High Priority

#### Review Delegated Permissions

- Only trusted administrators should receive delegated management permissions.

- Recommended actions:

    - Review delegated rights.
    - Remove obsolete delegations.
    - Document administrative responsibilities.

---

### Medium Priority

#### Periodic User Review

- Regularly review:

    - Disabled accounts
    - Inactive users
    - Stale computer accounts
    - Unused security groups

- Maintaining directory hygiene reduces unnecessary risk.

---

#### Review Organizational Unit Design

- Ensure Organizational Units continue to reflect administrative requirements as the environment grows.

---

## Group Policy

### High Priority

#### Review Security Filtering

- Security filtering should be reviewed whenever policies are modified.

- Verify:

    - Correct security groups.
    - Correct delegated permissions.
    - Intended scope of application.

---

### Medium Priority

#### Periodically Audit Group Policy Objects

- Recommended activities:

    - Remove unused GPOs.
    - Consolidate duplicate settings.
    - Review policy inheritance.
    - Document policy purpose.

---

#### Test Policy Changes

- New or modified Group Policy Objects should be validated within a test environment before deployment.

---

## SMB and File Services

### High Priority

#### Review Share Permissions

- Regularly verify:

    - Share permissions.
    - NTFS permissions.
    - Departmental access.

- Access should align with business requirements.

---

### Medium Priority

#### Periodic Access Reviews

- Conduct scheduled reviews to ensure users retain access only to resources required for their role.

---

#### Enable SMB Signing

- Where appropriate, enable SMB signing to improve protection against certain network attacks.

---

## Linux Server

### High Priority

#### Restrict Administrative Endpoints

- Administrative interfaces should not be publicly accessible.

- Examples include:

    - Apache `server-status`
    - Administrative configuration pages

- Restrict access to trusted administrative systems where operationally appropriate.

---

#### Keep Software Updated

- Maintain current versions of:

    - Ubuntu
    - Apache
    - PHP
    - MariaDB
    - WordPress

- Timely updates reduce exposure to publicly known vulnerabilities.

---

### Medium Priority

#### Review Apache Configuration

- Recommended activities:

    - Remove unnecessary modules.
    - Disable directory listing where not required.
    - Review default configuration.
    - Limit information disclosure.

---

#### Secure SSH

- Recommended improvements:

    - Disable password authentication where possible.
    - Use SSH key authentication.
    - Restrict administrative access.
    - Review authentication logs.

---

## WordPress

### High Priority

#### Strong Administrative Authentication

- Administrative accounts should use:

    - Strong passwords.
    - Unique credentials.
    - Multi-Factor Authentication where available.

---

#### Plugin and Theme Management

- Remove:

    - Unused plugins.
    - Unused themes.
    - Unsupported extensions.

- Reducing unnecessary software decreases attack surface.

---

### Medium Priority

#### Review XML-RPC

- If XML-RPC is not required:

    - Disable the endpoint.

- If required:

    - Monitor authentication activity.
    - Keep WordPress updated.
    - Restrict access where operationally feasible.

---

#### Scheduled Backups

- Implement regular backups of:

    - WordPress files.
    - Database.
    - Configuration.

- Periodic restoration testing should also be performed.

---

## Monitoring and Logging

### Medium Priority

- Implement centralized logging where practical.

- Examples include:

    - Windows Event Logs
    - Apache Logs
    - SSH Logs
    - Authentication Logs

- Centralized monitoring improves incident detection and investigation.

---

### Low Priority

- Future versions of the environment could integrate:

    - Windows Event Forwarding
    - Sysmon
    - Wazuh
    - SIEM platforms

- These technologies would provide enhanced visibility and support advanced defensive monitoring.

---

## Security Awareness

- Administrative controls should be complemented by operational practices.

- Recommendations include:

    - Security awareness training.
    - Strong password hygiene.
    - Administrative account separation.
    - Periodic access reviews.
    - Change management documentation.

---

## Implementation Roadmap

| Phase | Activities |
|--------|------------|
| Phase 1 | Restrict Apache administrative endpoints, review administrative privileges, review share permissions |
| Phase 2 | Enable advanced auditing, review Group Policy Objects, improve SSH configuration |
| Phase 3 | Centralized logging, endpoint monitoring, infrastructure expansion |

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `07-security-assessment.md` | Assessment methodology |
| `08-findings.md` | Assessment findings |
| `10-mitre-attack-mapping.md` | MITRE ATT&CK mapping |

---

## Summary

- The MiniCorp assessment identified opportunities to further strengthen an already functional enterprise environment.

- The recommendations focus on reducing attack surface, improving centralized administration, strengthening authentication and authorization, enhancing monitoring, and supporting long-term maintainability.

- These recommendations are intentionally presented as future improvements rather than implemented features, maintaining a clear distinction between validated configuration and proposed hardening activities.
