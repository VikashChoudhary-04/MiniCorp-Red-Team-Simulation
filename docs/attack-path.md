# Attack Path – MiniCorp Red Team Simulation

- This document reconstructs the validated attack path demonstrated during the MiniCorp simulated red team assessment.
- It separates executed and validated activity from modeled follow-on phases that were not executed.

---

## Attack Path Summary

```text
External Reconnaissance
        │
        ▼
Web Service Discovery
        │
        ▼
WordPress Identification
        │
        ▼
WordPress Enumeration
        │
        ├── XML-RPC Exposure
        ├── Upload Directory Listing
        ├── Administrator Username Discovery
        └── WP File Manager Presence
        │
        ▼
WordPress Administrator Authentication
        │
        ▼
Administrative Application Access
        │
        ▼
Validated High-Impact Application Control
        │
        └──► Modeled Follow-On Path
             Server Compromise
                    │
                    ▼
             Credential Discovery
                    │
                    ▼
             Internal Reconnaissance
                    │
                    ▼
             Active Directory Attack Chain
```

- The attack path through WordPress administrative access was executed and validated.
- Server compromise, credential discovery, internal reconnaissance, and Active Directory phases were modeled but not executed.

---

## Phase 1 — External Reconnaissance

### Objective

- Identify exposed services on the MiniCorp Ubuntu web server.

### Target

```text
192.168.56.10
```

### Command

```bash
nmap -sC -sV -p- 192.168.56.10
```

### Validated Results

```text
22/tcp
SSH - OpenSSH 9.6p1

80/tcp
HTTP - Apache 2.4.58
```

- HTTP reconnaissance identified an Ubuntu-based Apache web server running WordPress.

### Security Significance

- The exposed HTTP service established the primary application attack surface.
- WordPress identification provided a path for application-specific enumeration.

---

## Phase 2 — WordPress Enumeration

### Objective

- Enumerate the WordPress installation for exposed functionality, users, plugins, and security-relevant configuration.

### Application Enumeration

```bash
wpscan --url http://192.168.56.10 --enumerate ap
```

### Validated Findings

- XML-RPC enabled.
- Upload directory listing enabled.
- `twentytwentyfive` WordPress theme identified.

- These observations expanded the known attack surface.

---

## Phase 3 — User Enumeration

### Command

```bash
wpscan --url http://192.168.56.10 --enumerate u
```

### Validated Result

```text
admin
```

### Security Significance

- Username disclosure reduced the information required to target authentication.
- A known administrative username becomes more significant when combined with weak password controls.

---

## Phase 4 — Plugin Discovery and Validation

### Manual Validation

```bash
curl -I http://192.168.56.10/wp-content/plugins/wp-file-manager/
```

### Validated Result

```text
200 OK
```

- The response confirmed the presence of the WP File Manager plugin directory.

### Security Significance

- Installed plugins introduce additional application functionality and attack surface.
- Plugin presence alone does not prove that a vulnerability was exploited.
- No plugin exploitation is claimed in the validated attack path.

---

## Phase 5 — WordPress Administrator Authentication

### Login Endpoint

```text
http://192.168.56.10/wp-admin
```

### Lab Credentials

```text
Username: admin
Password: Password123
```

### Validated Result

- Authentication succeeded.
- The WordPress administrative dashboard became accessible.

### Access Available

- Plugin management.
- File editing functionality.
- Theme editing functionality.
- Media uploads.

### Security Significance

- Weak administrator credentials resulted in high-privilege application compromise.
- This was the highest level of access directly validated during the documented assessment.

---

## Validated Impact

- WordPress administrative access provided significant control over the application.
- The account exposed administrative functionality capable of modifying application-controlled content and server-side application files.
- This created a credible path toward deeper system compromise.

- The assessment does not demonstrate execution of:

  * Web shell deployment.
  * Arbitrary operating-system command execution.
  * Operating-system shell access.
  * Database credential extraction.
  * SSH compromise.
  * Credential reuse against internal systems.
  * Network pivoting.
  * Active Directory exploitation.

---

## Modeled Follow-On Attack Path

```text
WordPress Administrator Access
        │
        ▼
Potential Server-Side Execution
        │
        ▼
Potential Operating-System Access
        │
        ▼
Credential Discovery
        │
        ▼
Internal Network Reconnaissance
        │
        ▼
Domain Controller / Client Discovery
        │
        ▼
Active Directory Enumeration
        │
        ▼
Potential Lateral Movement
        │
        ▼
Potential Domain Compromise
```

- This sequence represents attack-path reasoning only.
- These phases were not executed or validated in the documented engagement.

---

## Modeled Phase — Server Compromise

- WordPress administrative privileges can create potential paths toward server-side execution through capabilities such as:

  * Theme modification.
  * Plugin installation.
  * Plugin modification.
  * File management.

- If converted into arbitrary server-side execution, an attacker could potentially transition from application compromise to operating-system access.
- This transition was not executed in the documented assessment.

---

## Modeled Phase — Credential Discovery

- If operating-system access were obtained, a follow-on assessment could investigate credentials stored in application configuration and system files.

- A high-value WordPress configuration file would include:

```text
wp-config.php
```

- Such configuration data may contain database credentials or other secrets.
- Credential extraction or reuse was not executed in the documented assessment.

---

## Modeled Phase — Internal Network Discovery

- The MiniCorp lab architecture includes:

```text
192.168.56.20 - Windows Server / Domain Controller
192.168.56.30 - Windows 10 / Domain Client
```

- Potential internal assessment activities could include:

  * Host discovery.
  * Service enumeration.
  * SMB enumeration.
  * Controlled authentication testing.
  * Active Directory service identification.

- The presence of these systems in the lab architecture does not mean they were reached or compromised through the validated WordPress attack path.

---

## Modeled Phase — Active Directory Assessment

- If valid internal access and credentials were established, a later phase could examine:

  * Domain users and groups.
  * Service accounts.
  * Kerberos configuration.
  * SMB permissions.
  * Credential reuse.
  * Privilege relationships.
  * Attack paths.

- Tools such as BloodHound, Kerberos enumeration utilities, and Impacket-based tooling would only become relevant after an authorized internal foothold was established.
- No Active Directory compromise is claimed in this project.

---

## Evidence Chain

| Phase | Evidence | Status |
| --- | --- | --- |
| External port scanning | Nmap results for `192.168.56.10` | Executed and validated |
| SSH and HTTP discovery | Ports `22/tcp` and `80/tcp` identified | Executed and validated |
| WordPress identification | HTTP reconnaissance | Executed and validated |
| WordPress enumeration | WPScan findings | Executed and validated |
| Username discovery | `admin` identified | Executed and validated |
| WP File Manager discovery | Plugin path returned `200 OK` | Executed and validated |
| Administrator authentication | WordPress dashboard access | Executed and validated |
| Administrative application control | High-privilege dashboard capabilities observed | Validated impact |
| Server shell / OS compromise | No execution evidence documented | Modeled only |
| Credential harvesting | No extraction evidence documented | Modeled only |
| Internal pivoting | No pivot evidence documented | Modeled only |
| Active Directory compromise | No AD attack evidence documented | Modeled only |

---

## Attack-Path Interpretation

```text
Exposed Web Application
        +
Discoverable Administrator Username
        +
Weak Administrator Credentials
        =
WordPress Administrative Compromise
```

- The assessment demonstrates how several weaknesses can combine into meaningful compromise.
- The critical validated outcome is that weak administrator credentials enabled successful high-privilege application access.

---

## Defensive Breakpoints

### Authentication Hardening

- Enforce strong, unique administrator passwords.
- Require multi-factor authentication for privileged accounts.
- Apply login rate limiting and monitoring.

### Exposure Reduction

- Restrict administrative interfaces where appropriate.
- Disable unnecessary WordPress functionality.
- Review XML-RPC exposure based on business requirements.

### Information Exposure Reduction

- Prevent unnecessary directory listing.
- Reduce avoidable username disclosure where practical.

### WordPress Hardening

- Maintain WordPress core, themes, and plugins.
- Remove unused components.
- Restrict file-editing and plugin-management capabilities where appropriate.
- Apply least privilege to administrative accounts.

### Monitoring

- Alert on unusual administrator authentication.
- Monitor plugin and theme modifications.
- Detect unexpected changes to application files.
- Review authentication failures and suspicious enumeration activity.

---

## Assessment Boundary

### Executed and Validated

- External Nmap reconnaissance.
- HTTP and WordPress identification.
- WordPress enumeration.
- XML-RPC exposure identification.
- Upload directory listing identification.
- WordPress username enumeration.
- WP File Manager presence validation.
- Successful WordPress administrator authentication.
- Verification of administrative dashboard capabilities.

### Validated Impact

- High-privilege control of the WordPress application.
- Access to administrative functionality capable of modifying application-controlled content and server-side application files.
- Credible escalation potential resulting from privileged application access.

### Modeled but Not Executed

- Web shell deployment.
- Operating-system compromise.
- Database credential extraction.
- Credential reuse.
- SSH compromise.
- Internal network pivoting.
- Lateral movement.
- Active Directory enumeration through a compromised foothold.
- Domain privilege escalation or domain compromise.

---

## Key Takeaways

- Reconnaissance identified the exposed attack surface.
- WordPress enumeration revealed security-relevant information and an administrative username.
- Weak credentials converted reconnaissance findings into validated administrative access.
- Administrative access established significant application-level impact and a credible route toward deeper compromise.
- Server, pivoting, and Active Directory stages remain modeled attack paths rather than completed attack phases.
- Maintaining this distinction makes the project technically accurate and defensible during portfolio review or technical interviews.
