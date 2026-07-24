# MiniCorp Red Team Simulation

![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)
![Markdown](https://img.shields.io/badge/Markdown-Documentation-blue?style=flat-square)
![Hands-on](https://img.shields.io/badge/Hands--on-Yes-success?style=flat-square)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Offensive-red?style=flat-square)
![Red Team](https://img.shields.io/badge/Red%20Team-Simulation-critical?style=flat-square)

## Overview

- **MiniCorp Red Team Simulation** documents a controlled security assessment performed against a locally hosted corporate lab environment.
- The project demonstrates a structured attack workflow from initial reconnaissance through validated compromise of a WordPress administrative account.
- It also documents potential post-compromise attack paths separately from actions that were actually executed.
- The purpose of this separation is to maintain a clear distinction between:
  * Observed and validated results.
  * Demonstrated security impact.
  * Modeled attack paths that were not executed.
- All systems, credentials, network addresses, and attack activity documented in this repository belong to an isolated lab environment created for educational and portfolio purposes.

---

## Lab Architecture

| Machine | Role | Lab IP |
| --- | --- | --- |
| Kali Linux | Attacker Machine | `192.168.56.50` |
| Ubuntu Server | Public Web Server | `192.168.56.10` |
| Windows Server | Domain Controller | `192.168.56.20` |
| Windows 10 | Domain Client | `192.168.56.30` |

- Lab domain:

  ```text
  minicorp.local
  ```

- The environment models a small organization containing:
  * An externally targeted web server.
  * A Windows Active Directory domain controller.
  * A domain-joined Windows workstation.
  * A dedicated attacker system.

---

## Assessment Boundary

### Executed and Validated

- The following activities were performed and documented during the simulation:
  * Network reconnaissance against the Ubuntu web server.
  * Service and port enumeration.
  * WordPress identification.
  * WordPress user enumeration.
  * Plugin discovery and verification.
  * Authentication testing.
  * Successful access to the WordPress administrative interface using weak lab credentials.
  * Security finding identification and remediation analysis.

### Validated Impact

- The assessment demonstrated unauthorized administrative control of the WordPress application.
- WordPress administrator privileges provide significant control over application functionality and create potential paths toward deeper compromise.
- The simulation did **not** validate operating-system-level compromise of the Ubuntu server.

### Modeled but Not Executed

- The following phases are documented as potential follow-on attack paths and were not executed as part of the validated assessment:
  * Server-level compromise.
  * Credential extraction from the underlying host.
  * Internal network pivoting.
  * Lateral movement.
  * Active Directory enumeration and exploitation.
  * Domain compromise.
- These sections demonstrate attack-path analysis without presenting unperformed activity as an achieved result.

---

## Tools Used

- Tools with documented usage during the executed assessment:
  * **Nmap** — network and service reconnaissance.
  * **WPScan** — WordPress enumeration.
  * **curl** — manual HTTP inspection and endpoint verification.
- Additional techniques discussed in modeled attack-path documentation are conceptual follow-on activities and are not represented as executed tool usage.

---

## Validated Attack Flow

```text
External Reconnaissance
        │
        ▼
Service Enumeration
        │
        ▼
WordPress Discovery
        │
        ▼
WordPress Enumeration
        │
        ├── User Discovery
        │
        └── Plugin Discovery
        │
        ▼
Authentication Testing
        │
        ▼
Weak Administrator Credentials
        │
        ▼
WordPress Administrative Access
        │
        ▼
Security Impact Analysis
```

- The validated attack chain stops at confirmed WordPress administrative access.
- Server compromise, credential harvesting, internal pivoting, and Active Directory compromise remain modeled follow-on scenarios rather than completed attack stages.

---

## Key Findings

### Weak WordPress Administrator Credentials

- A weak administrator password allowed successful authentication to the WordPress administrative interface.
- This represented the primary validated compromise path in the simulation.

### XML-RPC Exposure

- The WordPress XML-RPC endpoint was exposed.
- Depending on configuration and defensive controls, exposed XML-RPC functionality can increase authentication and application attack surface.

### Directory Listing

- Directory listing was observed within the WordPress uploads path.
- Exposed directory contents can reveal files and information useful during reconnaissance.

---

## Repository Structure

```text
MiniCorp-Red-Team-Simulation/
│
├── README.md
│
├── docs/
│   ├── attack-path.md
│   ├── domain-controller.md
│   ├── kali-attacker.md
│   ├── lab-architecture.md
│   ├── network-diagram.md
│   ├── ubuntu-webserver.md
│   └── windows-client.md
│
├── recon/
│   ├── nmap-scan.md
│   └── wordpress-enumeration.md
│
├── exploitation/
│   └── wordpress-access.md
│
├── post-exploitation/
│   ├── credential-discovery.md
│   └── server-access.md
│
├── pivoting/
│   └── internal-network-discovery.md
│
└── reports/
    ├── findings.md
    └── redteam-engagement-report.md
```

---

## Documentation

### Lab Design

- [`docs/lab-architecture.md`](docs/lab-architecture.md) — overall lab architecture.
- [`docs/network-diagram.md`](docs/network-diagram.md) — network layout and system relationships.
- [`docs/kali-attacker.md`](docs/kali-attacker.md) — attacker system.
- [`docs/ubuntu-webserver.md`](docs/ubuntu-webserver.md) — public-facing web server.
- [`docs/domain-controller.md`](docs/domain-controller.md) — Active Directory domain controller.
- [`docs/windows-client.md`](docs/windows-client.md) — Windows domain client.

### Executed Assessment

- [`recon/nmap-scan.md`](recon/nmap-scan.md) — network reconnaissance.
- [`recon/wordpress-enumeration.md`](recon/wordpress-enumeration.md) — WordPress enumeration.
- [`exploitation/wordpress-access.md`](exploitation/wordpress-access.md) — validated WordPress administrative access.
- [`docs/attack-path.md`](docs/attack-path.md) — consolidated attack-path analysis.

### Modeled Follow-On Analysis

- [`post-exploitation/server-access.md`](post-exploitation/server-access.md) — potential transition from application access to server compromise.
- [`post-exploitation/credential-discovery.md`](post-exploitation/credential-discovery.md) — modeled credential-discovery opportunities.
- [`pivoting/internal-network-discovery.md`](pivoting/internal-network-discovery.md) — modeled internal reconnaissance and pivoting opportunities.

### Reporting

- [`reports/findings.md`](reports/findings.md) — documented security findings.
- [`reports/redteam-engagement-report.md`](reports/redteam-engagement-report.md) — engagement-level assessment report.

---

## Skills Demonstrated

- This project demonstrates practical understanding of:
  * Red team engagement structure.
  * Network reconnaissance.
  * Service enumeration.
  * Web attack-surface analysis.
  * WordPress security assessment.
  * Authentication weakness identification.
  * Evidence-based attack-path documentation.
  * Security impact analysis.
  * Post-compromise attack-path modeling.
  * Technical finding documentation.
  * Remediation recommendations.
  * Clear separation between validated results and hypothetical attack progression.

---

## Key Lessons

- Successful red team work is not defined only by the number of systems compromised.
- A defensible assessment requires:
  * Clear scope.
  * Reproducible evidence.
  * Accurate reporting.
  * Explicit distinction between confirmed compromise and potential impact.
  * Practical remediation guidance.
- In this simulation, weak application credentials demonstrated how an initial authentication weakness could create a significant foothold while also illustrating where further validation would be required before claiming server or domain compromise.

---

## Ethics and Scope

- This project was conducted entirely inside a controlled local lab.
- The IP addresses, domain, credentials, systems, and attack scenarios documented here are part of the simulated MiniCorp environment.
- No unauthorized third-party systems were targeted.
- Techniques documented in this repository are intended for:
  * Authorized penetration testing.
  * Red team training.
  * Security research in controlled environments.
  * Defensive education.

---

## Disclaimer

- This repository is provided for educational and authorized security-testing purposes only.
- Always obtain explicit authorization before performing security testing against systems you do not own or control.
