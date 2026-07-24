# MiniCorp Red Team Engagement Report

## Executive Summary

- MiniCorp is a controlled lab environment designed to simulate a small corporate network and demonstrate a structured red team assessment workflow.

- The executed assessment focused on the externally reachable Ubuntu web server and its WordPress application.

- Testing validated three security findings:

  * Weak WordPress administrator credentials
  * Exposed WordPress XML-RPC functionality
  * Directory listing on the WordPress uploads path

- Weak administrator credentials were validated through successful authentication to the WordPress administrative dashboard.

- This access demonstrated compromise of a privileged application account and exposed administrative capabilities that could materially affect the web application.

- Potential progression from WordPress administration to operating-system access, credential harvesting, internal network pivoting, lateral movement, and Active Directory compromise was analyzed as follow-on attack paths but was not executed.

---

## Assessment Objectives

- Identify the exposed attack surface of the MiniCorp web server.

- Enumerate the WordPress deployment and accessible functionality.

- Identify security weaknesses that could provide unauthorized access.

- Validate exploitable findings where safely demonstrated.

- Assess the security impact of validated access.

- Model realistic follow-on attack paths without presenting unexecuted activity as completed compromise.

---

## Scope

### Lab Environment

| System | Role | Address |
| --- | --- | --- |
| Kali Linux | Assessment workstation | `192.168.56.50` |
| Ubuntu Server | Public-facing web server | `192.168.56.10` |
| Windows Server | Domain controller | `192.168.56.20` |
| Windows 10 | Domain client | `192.168.56.30` |

- Lab domain:

  ```text
  minicorp.local
  ```

### Executed Assessment Scope

- Active testing was performed against the Ubuntu web server at:

  ```text
  192.168.56.10
  ```

- Executed activities included:

  * Network service discovery
  * Service and application identification
  * WordPress enumeration
  * User enumeration
  * Plugin-path validation
  * WordPress administrative authentication
  * Security-impact analysis

### Modeled Follow-On Scope

- The following systems and attack phases were part of the lab architecture and threat model but were not compromised during the documented assessment:

  * Windows Server domain controller
  * Windows 10 domain client
  * Internal pivoting
  * Active Directory enumeration
  * Kerberos attacks
  * SMB-based lateral movement
  * Domain privilege escalation

---

## Methodology

- The assessment followed a simplified red team workflow:

  1. Reconnaissance
  2. Service discovery
  3. Web application enumeration
  4. Identity discovery
  5. Authentication testing
  6. Privileged application access validation
  7. Impact assessment
  8. Follow-on attack-path modeling
  9. Reporting and remediation analysis

- All activity was performed inside an authorized local lab environment.

---

## Executed and Validated Attack Path

### Phase 1 — Network Reconnaissance

- The Ubuntu web server was scanned to identify exposed services.

- Command:

  ```bash
  nmap -sC -sV -p- 192.168.56.10
  ```

- The assessment identified:

  * TCP/22 — SSH
  * TCP/80 — HTTP

- The HTTP service was associated with an Apache-hosted WordPress deployment.

### Phase 2 — WordPress Enumeration

- WPScan was used to enumerate the WordPress application.

- Plugin-oriented enumeration:

  ```bash
  wpscan --url http://192.168.56.10 --enumerate ap
  ```

- User enumeration:

  ```bash
  wpscan --url http://192.168.56.10 --enumerate u
  ```

- The assessment identified the WordPress user:

  ```text
  admin
  ```

- Additional observations included:

  * XML-RPC enabled
  * Upload directory listing enabled
  * `twentytwentyfive` theme identified

### Phase 3 — Plugin-Path Validation

- Manual HTTP validation was performed against the WP File Manager plugin path.

- Command:

  ```bash
  curl -I http://192.168.56.10/wp-content/plugins/wp-file-manager/
  ```

- The endpoint returned an HTTP `200 OK` response, confirming that the plugin path was reachable.

- This validation established plugin presence/path exposure only. No plugin exploit is claimed as part of the executed attack path.

### Phase 4 — Administrative Authentication

- The assessment validated weak WordPress administrator credentials.

- Account:

  ```text
  admin
  ```

- Successful authentication to:

  ```text
  /wp-admin
  ```

  provided access to the WordPress administrative dashboard.

- The lab credential itself is documented separately in the technical evidence for reproducibility; the security issue is the use of a weak privileged credential rather than the specific password value.

### Phase 5 — Privileged Application Access

- Validated WordPress administrative access exposed privileged application capabilities, including:

  * Plugin management
  * Theme management and editing capabilities
  * Media upload functionality
  * Administrative configuration access

- This demonstrated compromise of a privileged application account.

- The assessment did not claim or validate operating-system shell access, database credential extraction, SSH compromise, or host-level persistence.

---

## Validated Impact

- The validated compromise resulted in unauthorized access to a privileged WordPress administrator account.

- Demonstrated impact included the ability to access administrative functionality capable of materially changing the WordPress application.

- The validated security consequences include:

  * Loss of administrative account confidentiality
  * Unauthorized privileged access
  * Potential modification of application content and configuration
  * Increased opportunity for malicious application changes
  * Expanded attack surface for follow-on compromise

- Full operating-system compromise was not executed and is therefore not presented as a validated result.

---

## Key Findings

### Finding 1 — Weak WordPress Administrator Credentials

- **Severity:** High

- A privileged WordPress administrator account used a weak credential that permitted successful administrative authentication.

- Successful access exposed privileged WordPress functionality.

- **Validated impact:**

  * Unauthorized administrator access
  * Access to privileged application-management functionality
  * Ability to make high-impact application-level changes

- **Recommendation:**

  * Enforce strong, unique passwords
  * Require multi-factor authentication for privileged accounts
  * Implement login throttling or rate limiting
  * Monitor privileged authentication activity
  * Remove or disable unnecessary administrator accounts

### Finding 2 — XML-RPC Exposure

- **Severity:** Medium

- The WordPress XML-RPC interface was exposed at:

  ```text
  /xmlrpc.php
  ```

- Exposed XML-RPC functionality can increase authentication and application attack surface when it is not operationally required.

- **Recommendation:**

  * Disable XML-RPC when unnecessary
  * Restrict permitted XML-RPC functionality when it must remain enabled
  * Apply authentication protections and monitoring
  * Review logs for suspicious XML-RPC activity

### Finding 3 — Directory Listing Enabled

- **Severity:** Low

- Directory listing was observed for:

  ```text
  /wp-content/uploads/
  ```

- Directory indexing can expose filenames and stored content that would otherwise require prior knowledge of exact resource paths.

- **Recommendation:**

  * Disable directory indexing
  * Review publicly accessible uploaded content
  * Apply appropriate web-server access controls
  * Avoid storing sensitive material in publicly reachable upload directories

---

## Risk Summary

| Finding | Severity | Validation Status |
| --- | --- | --- |
| Weak WordPress administrator credentials | High | Validated |
| XML-RPC exposure | Medium | Observed |
| Directory listing enabled | Low | Observed |

- The highest-risk validated issue was weak privileged authentication because it resulted in successful WordPress administrator access.

- The remaining findings increase attack surface and should be addressed as part of defense-in-depth hardening.

---

## Modeled but Not Executed

- After obtaining privileged WordPress access, a realistic adversary could investigate whether application-level control can be converted into deeper host or network access.

- Potential follow-on phases include:

  * Server-side code execution
  * Operating-system shell access
  * Configuration-file access
  * Credential discovery
  * Credential reuse testing
  * Internal network reconnaissance
  * Pivoting
  * Active Directory enumeration
  * Kerberos or SMB attack paths
  * Lateral movement
  * Domain privilege escalation

- These phases represent attack-path analysis only.

- They were not executed or validated during the documented assessment and must not be interpreted as evidence that the Ubuntu host, Windows systems, or Active Directory domain were compromised.

---

## Remediation Priorities

### Priority 1 — Secure Privileged Authentication

- Immediately replace weak administrator credentials.

- Require unique passwords for privileged accounts.

- Enable multi-factor authentication.

- Review administrator accounts and remove unnecessary privileges.

- Monitor failed and successful privileged logins.

### Priority 2 — Reduce WordPress Attack Surface

- Disable XML-RPC if it is not required.

- Remove unused plugins and themes.

- Keep WordPress core, plugins, and themes patched.

- Restrict administrative interfaces where operationally feasible.

- Review plugin exposure and configuration.

### Priority 3 — Harden Web-Server Configuration

- Disable directory listing.

- Review access controls on uploaded content.

- Minimize information disclosure.

- Review Apache and WordPress configuration against hardened baselines.

### Priority 4 — Limit Follow-On Compromise

- Avoid credential reuse between web applications, Linux hosts, and domain accounts.

- Apply least privilege to service and administrative accounts.

- Segment externally exposed services from sensitive internal systems.

- Monitor internal authentication and lateral-movement indicators.

- Protect Active Directory administrative accounts with dedicated privileged-access controls.

---

## Defensive Detection Opportunities

- Defenders should monitor for:

  * Repeated WordPress authentication attempts
  * Successful privileged logins from unusual sources
  * Administrative plugin or theme changes
  * Unexpected file modifications in WordPress directories
  * Suspicious XML-RPC activity
  * Unusual access to exposed directories
  * New or unexpected administrator accounts
  * Web-server activity followed by internal authentication attempts

- Correlating web, authentication, endpoint, and network telemetry can help detect progression from initial application access toward deeper compromise.

---

## Assessment Limitations

- This engagement was a controlled portfolio lab rather than a production red team operation.

- The documented evidence supports:

  * External reconnaissance of the Ubuntu web server
  * WordPress discovery and enumeration
  * WordPress user discovery
  * Plugin-path validation
  * Weak administrator credential validation
  * Successful WordPress administrative access

- The documented evidence does not support claims of:

  * Operating-system shell compromise
  * Database credential extraction
  * SSH compromise
  * Internal pivot execution
  * Windows host compromise
  * Active Directory compromise
  * Domain administrator access

- Maintaining this distinction ensures that the report accurately represents demonstrated work.

---

## Conclusion

- The MiniCorp assessment demonstrated how weak privileged authentication can turn routine reconnaissance and application enumeration into unauthorized administrative access.

- The most significant validated issue was the weak WordPress administrator credential, which exposed high-impact application-management capabilities.

- XML-RPC exposure and directory listing further increased the externally accessible attack surface.

- The lab architecture also provides a realistic basis for modeling how an attacker might attempt to progress from a compromised web application toward host access, credential discovery, internal pivoting, and Active Directory attacks.

- Those later phases remain explicitly modeled rather than executed.

- The engagement demonstrates a complete assessment mindset: reconnaissance, enumeration, validation, impact analysis, attack-path reasoning, defensive recommendations, and evidence-based reporting.

---

## Ethics and Authorization

- All testing documented in this report was performed inside a controlled lab environment created for educational and portfolio purposes.

- No third-party or production systems were targeted.

- Techniques described in modeled follow-on sections are included to demonstrate security reasoning and should only be applied to systems with explicit authorization.
