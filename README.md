# MiniCorp Red Team Lab

## Overview

- This repository documents a simulated red team engagement against a small corporate environment called **MiniCorp**.

- The goal of the project is to demonstrate the complete attack lifecycle:

  * External Reconnaissance
  * Web Application Enumeration
  * Credential Discovery
  * Post-Authentication Access
  * Internal Network Exploration
  * Active Directory Compromise (planned)

- The entire lab was built locally using VMware and free tools.

---

## Lab Architecture

| Machine        | Role              | IP            |
| -------------- | ----------------- | ------------- |
| Kali Linux     | Attacker Machine  | 192.168.56.50 |
| Ubuntu Server  | Public Web Server | 192.168.56.10 |
| Windows Server | Domain Controller | 192.168.56.20 |
| Windows 10     | Domain Client     | 192.168.56.30 |

- Domain Name:
  ```
  minicorp.local
  ```
---

## Tools Used

- Recon:

  * nmap
  * wpscan
  * curl

- Exploitation & Enumeration:

  * searchsploit
  * impacket
  * crackmapexec
  * bloodhound
  * kerbrute
  * hashcat

- All tools used are available in Kali Linux.

---

## Attack Flow

1. External reconnaissance of public server
2. WordPress enumeration
3. Discovery of installed plugins
4. User enumeration
5. WordPress authentication
6. Internal exploration of server environment
7. Planned pivot into Active Directory

---

## Why This Project Exists

- This lab demonstrates real red team methodology:

  * Target enumeration
  * Attack surface analysis
  * Credential discovery
  * System access

- The goal is to simulate how attackers compromise small corporate environments.

---

## Disclaimer

- This project was conducted entirely inside a controlled lab environment for educational purposes.
