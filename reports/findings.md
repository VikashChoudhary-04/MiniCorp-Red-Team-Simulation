# Security Findings – MiniCorp Lab

## Finding 1 – Weak WordPress Credentials

- Severity: High

- Description:

  - The WordPress administrator account used a weak password.

- Credentials:

  - admin / Password123

- Impact:

  - Attackers can gain administrative access to the WordPress dashboard.

- This allows modification of server-side files and potential server compromise.

- Recommendation:

  - Use strong password policies and multi-factor authentication.

---

## Finding 2 – XML-RPC Enabled

- Severity: Medium

- Description:

  - The WordPress XML-RPC interface is exposed.

- Endpoint:

  - /xmlrpc.php

- Impact:

  - Attackers may abuse XML-RPC for authentication attacks or amplification attacks.

- Recommendation:

  - Disable XML-RPC if not required.

---

## Finding 3 – Directory Listing Enabled

- Severity: Low

- Location:

  - /wp-content/uploads/

- Impact:

  - Attackers may view uploaded files or sensitive data.

- Recommendation:

  - Disable directory listing in the web server configuration.
