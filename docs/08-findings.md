# Security Findings

## Overview

- This document summarizes the security observations identified during the assessment of the MiniCorp enterprise environment.

- The findings are based exclusively on evidence collected during the assessment and are intended to support remediation planning and future hardening activities.

- Unless otherwise stated, all observations were identified within the isolated MiniCorp laboratory environment.

---

## Finding Classification

- Severity levels used throughout this document.

| Severity | Description |
|----------|-------------|
| Informational | Observation with minimal security impact but useful for awareness. |
| Low | Limited security impact with straightforward remediation. |
| Medium | Moderate security impact requiring remediation. |
| High | Significant security weakness requiring prompt remediation. |
| Critical | Immediate risk requiring urgent action. |

---

## Finding Summary

| ID | Finding | Severity | Status |
|----|----------|:--------:|:------:|
| MC-001 | Apache `server-status` endpoint accessible | Low | Open |
| MC-002 | WordPress administrative interface exposed | Informational | Accepted |
| MC-003 | WordPress XML-RPC endpoint available | Informational | Open |
| MC-004 | Department-based SMB authorization functioning correctly | Informational | Validated |
| MC-005 | Active Directory integrated DNS functioning correctly | Informational | Validated |
| MC-006 | Authenticated LDAP directory enumeration | Informational | Accepted |

---

## MC-001 — Apache `server-status` Endpoint Accessible

| Field | Value |
|--------|-------|
| Finding ID | MC-001 |
| Severity | Low |
| Category | Apache Configuration |
| Asset | MiniCorp-Ubuntu |
| Status | Open |

### Description

- The Apache `server-status` endpoint was accessible during the assessment.

- This endpoint may disclose operational information about the web server including worker status, request activity, and server configuration details.

---

### Evidence

- Evidence collected during the assessment included:

    - HTTP response validation using `curl`
    - Manual endpoint verification
    - Supporting screenshot

---

### Risk

- Although the endpoint does not directly expose sensitive credentials, the information available may assist reconnaissance and provide additional context to an attacker.

---

### Recommendation

- Restrict access to the endpoint by:

    - Limiting access to localhost.
    - Restricting access to administrative IP addresses.
    - Disabling the module if operational monitoring is unnecessary.

---

## MC-002 — WordPress Administrative Interface Exposed

| Field | Value |
|--------|-------|
| Finding ID | MC-002 |
| Severity | Informational |
| Category | Web Application |
| Asset | MiniCorp-Ubuntu |
| Status | Accepted |

### Description

- The WordPress administrative interface was accessible through its standard administrative endpoint.

- Administrative interfaces are expected components of a WordPress deployment but should be protected through strong authentication and operational security controls.

---

### Evidence

- Assessment activities confirmed:

    - WordPress identification.
    - Administrative interface accessibility.
    - Expected application behavior.

---

### Risk

- The administrative interface itself does not represent a vulnerability.

- However, it may become an attack surface if combined with weak authentication or software vulnerabilities.

---

### Recommendation

- Enforce strong administrator passwords.
- Enable Multi-Factor Authentication where appropriate.
- Keep WordPress updated.
- Remove unused administrator accounts.

---

## MC-003 — WordPress XML-RPC Endpoint Available

| Field | Value |
|--------|-------|
| Finding ID | MC-003 |
| Severity | Informational |
| Category | WordPress Configuration |
| Asset | MiniCorp-Ubuntu |
| Status | Open |

### Description

- The XML-RPC endpoint was accessible during the assessment.

- XML-RPC provides legitimate remote functionality but may increase the application's attack surface if unnecessary.

---

### Evidence

- Assessment activities confirmed that the endpoint responded as expected.

---

### Risk

- Depending on deployment requirements, XML-RPC may facilitate:

    - Authentication attempts.
    - Remote publishing.
    - Additional application functionality.

- Its presence should therefore be evaluated within the organization's operational requirements.

---

### Recommendation

- Disable XML-RPC if it is not required by the application.

- If it must remain enabled, monitor authentication activity and keep the application fully updated.

---

## MC-004 — Department-Based SMB Authorization

| Field | Value |
|--------|-------|
| Finding ID | MC-004 |
| Severity | Informational |
| Category | Authorization Validation |
| Asset | MiniCorp-DC |
| Status | Validated |

### Description

- SMB authorization behaved as expected.

- Departmental users were able to access only the network shares explicitly assigned to their security groups.

---

### Evidence

- Validation confirmed:

    - Successful authentication.
    - Correct department access.
    - Proper access denial for unauthorized shares.

---

### Security Value

- This demonstrates successful implementation of:

    - Active Directory Security Groups.
    - SMB Share Permissions.
    - NTFS Permissions.

---

## MC-005 — Active Directory Integrated DNS

| Field | Value |
|--------|-------|
| Finding ID | MC-005 |
| Severity | Informational |
| Category | Infrastructure Validation |
| Asset | MiniCorp-DC |
| Status | Validated |

### Description

- DNS services were operating correctly throughout the assessment.

- Domain resolution and Active Directory integration behaved as expected.

---

### Evidence

- Validation included:

    - DNS queries.
    - Forward lookup testing.
    - Internal domain resolution.

---

### Security Value

- Reliable DNS functionality is essential for:

    - Active Directory.
    - Kerberos authentication.
    - Group Policy processing.
    - Enterprise service discovery.

---

## MC-006 — Authenticated LDAP Enumeration

| Field | Value |
|--------|-------|
| Finding ID | MC-006 |
| Severity | Informational |
| Category | Directory Services |
| Asset | MiniCorp-DC |
| Status | Accepted |

### Description

- Authenticated LDAP queries successfully returned directory information including users, groups, Organizational Units, and naming contexts.

- This behavior is expected within a functioning Active Directory environment.

---

### Evidence

- Authenticated queries successfully enumerated:

    - User objects.
    - Security groups.
    - Distinguished Names.
    - Naming Contexts.

---

### Risk

- Authenticated directory enumeration is expected functionality.

- Administrators should nevertheless ensure that sensitive directory information is protected through appropriate permissions and regular directory reviews.

---

### Recommendation

- Review delegated permissions regularly.
- Remove obsolete accounts.
- Apply the Principle of Least Privilege.
- Audit privileged group memberships.

---

## Overall Assessment

- The assessment did not identify any Critical or High severity issues within the implemented MiniCorp environment.

- The observations primarily relate to:

    - Service exposure.
    - Expected enterprise functionality.
    - Configuration review.
    - Authorization validation.

- The environment demonstrated effective implementation of centralized authentication, authorization, Group Policy, and departmental access controls.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `07-security-assessment.md` | Assessment methodology |
| `09-hardening-recommendations.md` | Security improvements |
| `10-mitre-attack-mapping.md` | ATT&CK mapping |

---

## Summary

- The findings documented throughout the assessment accurately reflect the implemented MiniCorp environment.

- Rather than emphasizing exploitation, the assessment focused on validating enterprise configuration, documenting observations, and identifying opportunities for continued hardening.

- This evidence-based approach provides realistic experience with professional security reporting while maintaining clear separation between verified observations and future improvement recommendations.
