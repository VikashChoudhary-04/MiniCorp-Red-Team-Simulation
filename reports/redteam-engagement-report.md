# MiniCorp Red Team Engagement Report

## Scope

- Internal simulation of a small corporate network.

- Targets:

  * Ubuntu Web Server
  * Windows Domain Controller
  * Windows Client

---

## Attack Path

1. External reconnaissance
2. WordPress discovery
3. Plugin identification
4. User enumeration
5. Administrative login

---

## Key Findings

- Weak administrator credentials allowed direct access to WordPress administrative panel.

- This could allow attackers to modify web server files.

---

## Risk Level

- High

- Weak authentication mechanisms expose critical systems.

---

## Recommendations

* Enforce strong password policy
* Disable XML-RPC if not required
* Restrict WordPress administrative access
* Implement monitoring for authentication attempts
