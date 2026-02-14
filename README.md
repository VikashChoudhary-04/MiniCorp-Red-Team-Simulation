# 🛡️ MiniCorp Red Team Simulation

**Full Attack Chain: External Attacker → Domain Admin**

---

## 📌 Project Overview

This project simulates a **real-world red team engagement** against a small corporate environment called **MiniCorp**.

The objective was to demonstrate how an external attacker could compromise a company starting from the public website and ultimately gain **Domain Administrator access** to the internal Active Directory environment.

This lab was built entirely using **free and open-source tools**.

---

## 🎯 Engagement Goals

Simulate a real corporate breach and demonstrate:

* External reconnaissance
* Web application exploitation
* Credential harvesting
* Network pivoting
* Active Directory attacks
* Privilege escalation
* Professional red team reporting

---

## 🏢 Lab Architecture

The simulated corporate environment consisted of **4 machines**:

| Machine             | Role                 | IP            |
| ------------------- | -------------------- | ------------- |
| Kali Linux          | Attacker Machine     | Attacker      |
| Ubuntu Server       | Public Web Server    | 192.168.56.10 |
| Windows Server 2022 | Domain Controller    | 192.168.56.20 |
| Windows 10          | Employee Workstation | Internal      |

---

## 🔥 Attack Path Summary

The attack followed a realistic red team kill chain:

1. External reconnaissance discovered the public WordPress server.
2. A vulnerable WordPress plugin was exploited to gain a reverse shell.
3. Sensitive configuration files revealed reused employee credentials.
4. Credentials were used to access the internal Windows domain.
5. Active Directory enumeration identified a Kerberoastable service account.
6. Kerberoasting attack successfully cracked the service account password.
7. Privilege escalation achieved **Domain Administrator access**.

Final Result:

> 🎉 Full compromise of MiniCorp Active Directory.

---

## 🧰 Tools Used (All Free)

### Recon & Enumeration

* Nmap
* FFUF
* WhatWeb
* theHarvester

### Web Exploitation

* Burp Suite Community
* WPScan
* Netcat

### Pivoting & Post Exploitation

* Evil-WinRM
* Impacket
* BloodHound
* Hashcat

### Documentation

* Draw.io
* LibreOffice
* Obsidian

---

## 📂 Repository Contents

| File                  | Description                     |
| --------------------- | ------------------------------- |
| LAB_SETUP.md          | Step-by-step lab creation guide |
| ATTACK_WALKTHROUGH.md | Detailed attack diary           |
| REPORT PDF            | Professional red team report    |
| Screenshots           | Evidence of compromise          |
| Network Diagram       | Visual architecture of lab      |

---

## 📈 Skills Demonstrated

* Red Team Methodology
* Active Directory Security
* Web Application Exploitation
* Credential Attacks
* Network Pivoting
* Professional Security Reporting

---

## 📜 Disclaimer

This project was conducted in a **self-hosted lab environment** for educational and ethical purposes only.

---

## 👨‍💻 Author

Aspiring Red Team / Pentester
2026 Job Preparation Project
