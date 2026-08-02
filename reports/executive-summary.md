# Executive Summary

## Engagement Overview

- The MiniCorp Security Assessment was conducted to evaluate the security posture of a simulated enterprise environment consisting of Windows and Linux infrastructure integrated through Active Directory Domain Services.

- The assessment focused on validating the implementation of core enterprise services, reviewing system configuration, assessing authorization controls, and identifying opportunities to improve the overall security posture of the environment.

- All activities were performed within a privately owned laboratory environment designed for education, enterprise administration practice, and cybersecurity training.

---

## Assessment Objectives

- The primary objectives of the assessment were to:

    - Validate enterprise infrastructure deployment.
    - Review Active Directory configuration.
    - Verify DNS, LDAP, Kerberos, and SMB functionality.
    - Assess Group Policy implementation.
    - Review the Ubuntu web server configuration.
    - Assess the deployed WordPress application.
    - Identify security observations.
    - Provide practical hardening recommendations.

---

## Environment Summary

| Component | Description |
|-----------|-------------|
| Domain | `minicorp.local` |
| Domain Controller | Windows Server 2022 |
| Client Workstation | Windows 10 |
| Linux Server | Ubuntu Server 24.04 LTS |
| Web Platform | Apache, PHP, MariaDB, WordPress |
| Enterprise Services | Active Directory, DNS, LDAP, Kerberos, SMB, Group Policy |

- The environment reflects a small enterprise network managed through centralized identity and access management.

---

## Assessment Scope

- The assessment included the following systems:

| System | Role |
|----------|------|
| MiniCorp-DC | Windows Server 2022 Domain Controller |
| MiniCorp-Client | Windows 10 Domain Workstation |
| MiniCorp-Ubuntu | Ubuntu Server Web Server |

- Assessment activities included:

    - Host discovery
    - Service enumeration
    - DNS validation
    - LDAP validation
    - SMB authorization validation
    - Group Policy validation
    - Web server review  
    - WordPress assessment
    - Configuration review

---

## Key Observations

- The assessment confirmed that the deployed infrastructure functioned as intended.

- Key observations included:

    - Active Directory services were operating correctly.
    - DNS successfully resolved internal enterprise resources.
    - LDAP directory services responded correctly to authenticated queries.
    - SMB permissions enforced department-based authorization.
    - Group Policy Objects were successfully applied to intended users.
    - The Ubuntu server successfully hosted the WordPress application.
    - Apache configuration exposed the `server-status` endpoint.
    - The WordPress XML-RPC endpoint remained enabled.

- No Critical or High severity security issues were identified during the assessment.

---

## Risk Summary

| Severity | Findings |
|----------|---------:|
| Critical | 0 |
| High | 0 |
| Medium | 0 |
| Low | 1 |
| Informational | 5 |

- The majority of observations related to expected enterprise functionality and configuration review rather than exploitable vulnerabilities.

---

## Overall Security Posture

- The MiniCorp environment demonstrates a sound implementation of centralized enterprise administration.

- Positive observations include:

    - Centralized identity management through Active Directory.
    - Department-based authorization using security groups.
    - Layered file access controls through SMB and NTFS permissions.
    - Successful Group Policy enforcement.
    - Functional enterprise network services.
    - Well-defined system roles and responsibilities.

- The assessment indicates that the environment provides a suitable foundation for enterprise administration and continued security improvement.

---

## Priority Recommendations

- The following actions are recommended to further strengthen the environment.

### High Priority

- Restrict access to the Apache `server-status` endpoint.
- Review privileged group memberships.
- Periodically review SMB and NTFS permissions.
- Maintain current operating system and application updates.

---

### Medium Priority

- Enable additional Windows auditing.
- Review Group Policy Objects periodically.
- Review Apache configuration.
- Evaluate whether XML-RPC is required.

---

### Long-Term Improvements

- Future versions of the environment could incorporate:

    - Centralized logging.
    - Windows Event Forwarding.
    - Sysmon deployment.
    - Wazuh integration.
    - SIEM connectivity.
    - Infrastructure automation.

- These enhancements would improve monitoring, detection, and operational maturity.

---

## Conclusion

- The MiniCorp Security Assessment successfully validated the deployment and configuration of a small enterprise environment consisting of Windows infrastructure, Linux services, centralized identity management, and a hosted web application.

- The assessment identified a limited number of low-risk configuration observations while confirming the correct operation of core enterprise services, authorization controls, and administrative policies.

- The documented recommendations provide a practical roadmap for strengthening the environment while preserving its educational and administrative objectives.

---

## Executive Statement

- The MiniCorp project demonstrates how enterprise infrastructure deployment, centralized administration, and structured security assessment can be combined into a cohesive, well-documented environment.

- The assessment emphasizes evidence-based validation, accurate reporting, and practical recommendations, reflecting the principles of professional internal security reviews.
