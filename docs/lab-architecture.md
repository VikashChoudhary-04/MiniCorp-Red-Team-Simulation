# Lab Architecture

- The MiniCorp lab simulates a small corporate infrastructure.

## Network

- Subnet:
```
192.168.56.0/24
```
## Machines

### Kali Linux

- Role: Attacker machine

- IP: 192.168.56.50

---

### Ubuntu Server

- Role: Public Web Server

- Services:

  * Apache
  * WordPress
  * SSH

- IP: 192.168.56.10

---

### Windows Server

- Role: Domain Controller

- Domain:
  ```
  minicorp.local
  ```
- IP: 192.168.56.20

---

### Windows 10

- Role: Corporate Workstation

- Domain joined:

  - minicorp.local

- IP: 192.168.56.30

---

## Network Diagram

- Attacker → Web Server → Internal Network → Domain Controller
