# Internal Network Discovery – Modeled Pivoting and Internal Reconnaissance

## Overview

- This document describes internal network discovery as a modeled follow-on phase of the MiniCorp simulated red team assessment.

- The validated engagement established WordPress administrator access to the Ubuntu web application.

- Pivoting through the Ubuntu server, internal network scanning from a compromised host, Active Directory enumeration, lateral movement, and domain compromise were **not executed or validated**.

- The techniques described here represent a realistic continuation of the attack path if server-level access and an appropriate network position were separately established.

---

## Validated Starting Point

- The assessment validated:

  * External reconnaissance of the Ubuntu web server at `192.168.56.10`.
  * WordPress discovery and enumeration.
  * WordPress administrator authentication.
  * High-privilege application-level access.

- The assessment did not validate:

  * Operating-system access to the Ubuntu server.
  * A shell on the Ubuntu server.
  * Use of the Ubuntu server as a pivot host.
  * Internal scanning from the Ubuntu server.
  * Authentication to Windows systems.
  * Active Directory enumeration.

- Therefore, internal network discovery remains outside the executed portion of the engagement.

---

## MiniCorp Internal Architecture

- The designed MiniCorp lab includes the following systems:

  | IP Address | System | Intended Role |
  | --- | --- | --- |
  | `192.168.56.10` | Ubuntu Server | Public-facing WordPress web server |
  | `192.168.56.20` | Windows Server | Domain Controller |
  | `192.168.56.30` | Windows 10 | Domain Client |
  | `192.168.56.50` | Kali Linux | Attacker workstation |

- The lab domain is:

  ```text
  minicorp.local
  ```

- These systems are part of the documented lab architecture.

- Their presence in the architecture does not mean they were reached or compromised through the validated attack path.

---

## What Pivoting Would Require

- Pivoting requires a validated foothold on a system that can communicate with networks or services unavailable directly to the attacker.

- A modeled MiniCorp progression would be:

  ```text
  Validated WordPress Administrator Access
                  │
                  ▼
  Potential Server-Side Execution
                  │
                  ▼
  Potential Operating-System Foothold
                  │
                  ▼
  Verify Network Interfaces and Routes
                  │
                  ▼
  Establish Authorized Pivot Channel
                  │
                  ▼
  Internal Network Discovery
  ```

- The documented assessment stopped before server-side execution or an operating-system foothold was established.

- Therefore, no pivot channel was created.

---

## Internal Network Discovery Goals

- If a pivot were successfully established during a future authorized lab phase, internal reconnaissance would focus on understanding the reachable environment.

- Typical objectives include:

  * Identifying reachable hosts.
  * Determining available network segments.
  * Identifying exposed internal services.
  * Locating authentication infrastructure.
  * Identifying workstations and servers.
  * Mapping trust relationships.
  * Prioritizing systems for further authorized assessment.

- Discovery should be controlled and scoped to minimize unnecessary traffic and avoid disruption.

---

## Host Discovery

- From a validated internal foothold, a red team operator may first determine the host's network context.

- Relevant information could include:

  * Assigned IP addresses.
  * Network interfaces.
  * Subnet masks.
  * Routing tables.
  * DNS configuration.
  * Known neighboring systems.

- This information helps determine which internal networks are actually reachable.

- No such host-based network enumeration was performed in the documented MiniCorp engagement.

---

## Modeled Target Identification

- Based on the predefined lab architecture, two important internal systems would be logical assessment targets:

  ```text
  192.168.56.20 – Windows Server / Domain Controller
  192.168.56.30 – Windows 10 / Domain Client
  ```

- If these systems were discovered from a compromised internal host, the next step would be controlled service enumeration.

- Their IP addresses are known from lab design documentation, not from executed pivot-host discovery.

---

## Service Discovery

- Internal service discovery could be used to identify services such as:

  * DNS.
  * Kerberos.
  * LDAP.
  * SMB.
  * RPC.
  * WinRM.
  * RDP.
  * HTTP or HTTPS.
  * Other administrative or application services.

- Service exposure can help determine system roles and potential authentication paths.

- Service discovery alone does not establish vulnerability or compromise.

- No internal service scan against `192.168.56.20` or `192.168.56.30` is claimed as part of the validated engagement.

---

## Domain Controller Identification

- In an Active Directory environment, the Domain Controller is a high-value infrastructure component because it commonly provides services associated with:

  * Domain authentication.
  * Kerberos.
  * LDAP directory services.
  * DNS.
  * Group Policy.
  * Domain account and computer management.

- The MiniCorp architecture designates:

  ```text
  192.168.56.20
  ```

  as the Domain Controller for:

  ```text
  minicorp.local
  ```

- This role is known from the lab design.

- It was not independently discovered through an executed internal reconnaissance phase.

---

## Windows Client Context

- The MiniCorp architecture also includes:

  ```text
  192.168.56.30
  ```

  as a Windows domain client.

- In a modeled internal assessment, a workstation could provide opportunities to evaluate:

  * Domain membership.
  * Logged-on user context.
  * Accessible shares.
  * Local security configuration.
  * Credential exposure.
  * Trust relationships.
  * Lateral movement controls.

- No authentication, enumeration, or compromise of the Windows client was performed in the validated attack path.

---

## Active Directory Discovery

- If an authorized internal foothold and valid domain context were established, Active Directory discovery could focus on:

  * Domain information.
  * Users.
  * Groups.
  * Computers.
  * Service accounts.
  * Group memberships.
  * Administrative relationships.
  * Trusts.
  * Access-control relationships.

- Tools commonly associated with authorized AD assessment may include:

  * BloodHound.
  * Impacket utilities.
  * Kerberos enumeration tooling.
  * SMB and LDAP enumeration utilities.

- Listing these tools describes potential methodology only.

- Their presence in the project context does not mean they were used successfully against the MiniCorp domain.

---

## Credential-Based Internal Enumeration

- Internal authentication testing requires valid credentials or another authorized authentication mechanism.

- A modeled progression could be:

  ```text
  Credential Discovery
          │
          ▼
  Credential Validation
          │
          ▼
  Identify Accessible Internal Services
          │
          ▼
  Authenticate Within Scope
          │
          ▼
  Enumerate Granted Privileges
  ```

- The documented engagement did not discover or validate reusable internal credentials.

- Therefore, authenticated internal enumeration was not executed.

---

## SMB Enumeration

- SMB can expose useful information in Windows environments when appropriately configured.

- A future authorized assessment might evaluate:

  * Reachable SMB services.
  * Authentication requirements.
  * Accessible shares.
  * Share permissions.
  * Host information.
  * User-access boundaries.

- SMB enumeration should not be described as successful without evidence of actual connectivity and results.

- No SMB enumeration results are claimed in the validated MiniCorp assessment.

---

## Kerberos and LDAP Context

- Kerberos and LDAP are central technologies in many Active Directory environments.

- If the Domain Controller were reachable from a validated internal position, an authorized assessment could examine:

  * Domain naming information.
  * Authentication behavior.
  * Directory visibility.
  * Account configuration.
  * Service-account exposure.
  * Access relationships.

- Techniques such as password spraying, Kerberos account attacks, or service-ticket analysis would require explicit authorization and careful controls.

- None of these techniques were executed as part of the validated MiniCorp attack path.

---

## Password Spraying Boundary

- Password spraying can create account-lockout and operational risks.

- It should only be performed when:

  * Explicitly authorized.
  * Lockout policies are understood.
  * Test rates are controlled.
  * Target accounts are within scope.
  * Monitoring and safety conditions are established.

- No password spraying was performed against MiniCorp domain accounts.

---

## Pivoting Architecture

- If a future lab exercise established server-level access to `192.168.56.10`, a conceptual pivot architecture could look like:

  ```text
  Kali Attacker
  192.168.56.50
        │
        │ Authorized foothold
        ▼
  Ubuntu Web Server
  192.168.56.10
        │
        │ Pivot / routed access
        ▼
  Internal MiniCorp Network
        │
        ├── 192.168.56.20
        │   Domain Controller
        │
        └── 192.168.56.30
            Windows Client
  ```

- This diagram represents a modeled architecture.

- It does not indicate that such a pivot was established during the documented assessment.

---

## Potential Pivoting Technologies

- Depending on network design and assessment requirements, authorized red team operators may use technologies such as:

  * SSH tunneling.
  * SOCKS proxies.
  * Port forwarding.
  * Purpose-built tunneling utilities.
  * Proxy-aware scanning.
  * Controlled routing through a compromised host.

- Tool choice depends on:

  * Available access.
  * Network topology.
  * Operating-system privileges.
  * Firewall rules.
  * Engagement constraints.
  * Detection and safety requirements.

- No pivoting technology was used to reach the MiniCorp Windows systems during the validated engagement.

---

## Evidence Required to Claim Successful Pivoting

- Pivoting should only be documented as successful when supported by direct evidence.

- Appropriate evidence could include:

  * A validated operating-system foothold on the pivot host.
  * Verified internal interfaces or routes.
  * A successfully established tunnel or proxy.
  * Confirmed connectivity through the pivot.
  * Internal hosts discovered through that path.
  * Reproducible evidence showing traffic traversed the pivot.

- The documented MiniCorp assessment contains no such evidence.

- Therefore, successful pivoting is not claimed.

---

## Evidence Required to Claim Internal Discovery

- Internal network discovery should be supported by evidence such as:

  * Host discovery results.
  * Internal service enumeration.
  * DNS or directory discovery.
  * Validated system-role identification.
  * Reachability evidence from the established internal position.

- Architecture diagrams alone are not discovery evidence.

- The known MiniCorp host roles came from lab design documentation rather than an executed internal discovery phase.

---

## Modeled Internal Reconnaissance Workflow

```text
Establish Validated Server Foothold
            │
            ▼
Identify Interfaces and Routes
            │
            ▼
Determine Reachable Internal Networks
            │
            ▼
Establish Controlled Pivot
            │
            ▼
Perform Low-Impact Host Discovery
            │
            ▼
Enumerate Relevant Internal Services
            │
            ▼
Identify Domain Infrastructure
            │
            ▼
Validate Authorized Credentials
            │
            ▼
Perform Authenticated Enumeration
            │
            ▼
Map Potential Attack Paths
```

- This workflow represents a professional follow-on methodology.

- It was not completed during the documented MiniCorp engagement.

---

## Potential Security Impact

- If an attacker successfully moves from a public-facing application into an internal network, the security impact can increase substantially.

- Potential consequences include:

  * Discovery of additional systems.
  * Exposure of internal-only services.
  * Credential reuse.
  * Lateral movement.
  * Access to file shares.
  * Privilege escalation.
  * Active Directory compromise.
  * Broader organizational impact.

- These consequences are conditional and must not be presented as achieved without evidence.

---

## Defensive Recommendations

- Organizations can reduce pivoting and internal discovery risk by:

  * Segmenting public-facing servers from internal networks.
  * Restricting unnecessary outbound connectivity from web servers.
  * Applying host-based firewalls.
  * Limiting management protocols between network zones.
  * Enforcing least privilege.
  * Using unique credentials across systems.
  * Monitoring unusual east-west network traffic.
  * Detecting unexpected scanning behavior.
  * Monitoring authentication attempts across multiple hosts.
  * Restricting access to Domain Controllers.
  * Hardening SMB, WinRM, RDP, LDAP, and other administrative services.
  * Maintaining centralized logging and alerting.
  * Applying multi-factor authentication where appropriate.

---

## Assessment Boundary

### Executed and Validated

- External reconnaissance of `192.168.56.10`.
- WordPress enumeration.
- WordPress administrator authentication.
- High-privilege WordPress application access.
- Documentation of the predefined MiniCorp lab architecture.

### Validated Impact

- Compromise of a privileged WordPress account.
- Credible potential for escalation toward server-side execution depending on configuration.
- A plausible path from a public-facing application toward deeper infrastructure if additional compromise were separately achieved.

### Modeled but Not Executed

- Operating-system compromise of `192.168.56.10`.
- Shell access to the Ubuntu server.
- Internal interface or route enumeration from the Ubuntu server.
- Establishment of a pivot tunnel or proxy.
- Internal host discovery through a compromised system.
- Internal scanning of `192.168.56.20`.
- Internal scanning of `192.168.56.30`.
- SMB enumeration.
- LDAP enumeration.
- Kerberos enumeration.
- Password spraying.
- Credential reuse against internal systems.
- BloodHound data collection.
- Active Directory attack-path mapping from live data.
- Lateral movement.
- Domain privilege escalation.
- Domain compromise.

---

## Key Takeaways

- Internal network discovery was not executed during the validated MiniCorp assessment.

- The Windows Server and Windows client are known because they are part of the predefined lab architecture, not because they were discovered through a successful pivot.

- WordPress administrator access does not by itself establish server access or internal network reachability.

- A professional red team report must distinguish between:

  ```text
  Known Lab Architecture
          │
          ▼
  Actually Discovered Infrastructure
          │
          ▼
  Successfully Reached Systems
          │
          ▼
  Successfully Authenticated Systems
          │
          ▼
  Compromised Systems
  ```

- For the documented MiniCorp engagement, pivoting, internal reconnaissance, Active Directory enumeration, lateral movement, and domain compromise remain **modeled but not executed**.
