# 🧪 MiniCorp Lab Setup Guide

This document explains how the MiniCorp red team lab was built from scratch using only free tools.

---

# 💻 Hardware Requirements

Minimum recommended system:

* 16 GB RAM
* 200 GB free disk space
* CPU virtualization enabled (Intel VT-x / AMD-V)

---

# 🧰 Software Used

All tools are free:

* VirtualBox
* Kali Linux VM
* Ubuntu Server
* Windows Server 2022 Evaluation
* Windows 10 Evaluation

---

# 🌐 Virtual Network Configuration

Create an isolated corporate network.

VirtualBox → File → Tools → Network Manager

Create new network:

Name: MiniCorpNet
Type: Internal Network

This network will connect all corporate machines.

---

# 🐉 Attacker Machine — Kali Linux

Import Kali Linux VirtualBox image.

Recommended settings:

* RAM: 4 GB
* CPU: 2 cores
* Network: NAT

This machine represents the external attacker.

---

# 🌍 Public Web Server — Ubuntu

Create Ubuntu Server VM.

Settings:

* RAM: 2 GB
* Disk: 30 GB
* Adapter 1: NAT (internet access)
* Adapter 2: Internal Network → MiniCorpNet

Set static IP:

192.168.56.10

---

# 🌐 Install Web Stack

Install Apache, MySQL and PHP:

sudo apt update
sudo apt install apache2 mysql-server php php-mysql unzip -y

---

# 📝 Install WordPress

Download WordPress:

cd /var/www/html
sudo rm index.html
sudo wget https://wordpress.org/latest.zip
sudo unzip latest.zip
sudo mv wordpress/* .

Create database:

sudo mysql

CREATE DATABASE wordpress;
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'Password123!';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;

Complete setup via browser.

---

# ⚠️ Add Intentional Vulnerability

Install vulnerable plugin:

WP File Manager (outdated version)

This provides initial access vector.

---

# 🪟 Domain Controller — Windows Server

Create Windows Server 2022 VM.

Settings:

* RAM: 4 GB
* Network: Internal → MiniCorpNet
* Static IP: 192.168.56.20

Install Active Directory Domain Services.

Create domain:

minicorp.local

Domain Admin credentials:

Administrator / Winter2024!

---

# 💼 Employee Workstation — Windows 10

Create Windows 10 VM.

Settings:

* RAM: 3 GB
* Network: Internal → MiniCorpNet

Join domain: minicorp.local

Create user:

john / Password123

---

# 🔓 Create Credential Leak

On Ubuntu server create file:

/var/www/html/config_backup.txt

Add:

VPN USER: john
PASSWORD: Password123

This simulates developer credential reuse.

---

# 🧨 Create Active Directory Weakness

On Domain Controller create service account:

svc_backup
Password: Backup123!

Register SPN:

setspn -a backup/minicorp svc_backup

This creates Kerberoasting attack path.

---

# ✅ Lab Ready

The MiniCorp corporate environment is now ready for red team simulation.
