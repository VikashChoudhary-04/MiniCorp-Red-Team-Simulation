# Attack Path – MiniCorp Red Team Lab

- This document outlines the attack chain used during the simulated red team engagement.

## Step 1 — External Reconnaissance

- The attacker scanned the exposed infrastructure.

- Command used:
  ```
  nmap -sC -sV -p- 192.168.56.10
  ```
- Result:

  - Open ports discovered:
    ```
    22 – SSH
    80 – HTTP (Apache)
    ```
- WordPress detected.

---

## Step 2 — WordPress Enumeration

- Tool used:

  - wpscan

- Command:
  ```
  wpscan --url http://192.168.56.10 --enumerate u
  ```
- Result:

  - User discovered:
    ```
    admin
    ```
---

## Step 3 — Plugin Discovery

- Manual plugin verification revealed the presence of the WP File Manager plugin.

- Endpoint:
  ```
  /wp-content/plugins/wp-file-manager/
  ```
- HTTP response confirmed plugin directory.

---

## Step 4 — Authentication Access

- Weak administrator credentials allowed login to WordPress.

- URL:
  ```
  /wp-admin
  ```
- Credentials:
  ```
  admin / Password123
  ```
---

## Step 5 — Post Authentication Access

- WordPress administrative access allows modification of server files.

- Possible impacts:

  - File upload
  - Web shell deployment
  - Database credential discovery
  - System level compromise

---

## Planned Next Steps

- Further attack phases may include:

  - Server credential harvesting
  - Internal network discovery
  - Active Directory attack chain
