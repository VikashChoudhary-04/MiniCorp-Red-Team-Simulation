# Internal Network Discovery

- Once attackers gain access to a server inside the network, they can begin internal reconnaissance.

- Internal reconnaissance allows attackers to identify additional targets.

---

## Network Enumeration

- Attackers often perform internal scanning to identify:

  - Domain controllers
  - Workstations
  - File servers
  - Additional web services

- Example targets inside the MiniCorp network:

  - 192.168.56.20 – Domain Controller
  - 192.168.56.30 – Domain Client

---

## Internal Attack Surface

- Once inside the network, attackers may attempt:

  - Credential harvesting
  - Password spraying
  - Kerberos attacks
  - SMB enumeration

---

## Active Directory Targets

- Active Directory environments contain high-value assets such as:

  - Domain administrators
  - Service accounts
  - File shares

- Compromising these assets may allow attackers to control the entire domain.

---

## Security Impact

- Internal access dramatically increases attacker capability.

- An attacker who reaches this stage may perform lateral movement and privilege escalation.
