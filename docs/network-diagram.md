# Network Architecture – MiniCorp Lab

## Network Range

- 192.168.56.0/24

## Infrastructure

- Kali Linux (Attacker)
  - IP: 192.168.56.50

- Ubuntu Web Server
  - IP: 192.168.56.10

- Windows Server Domain Controller
  - IP: 192.168.56.20

- Windows 10 Workstation
  - IP: 192.168.56.30

- Domain:
  ```
  minicorp.local
  ```
---

## Network Flow

- External attacker → Web server → Internal network → Domain controller

---

## Attack Surface

- Public services:
  ```
  SSH
  HTTP
  ```
- Internal assets:

  - Active Directory domain controller
  - Domain joined workstation
