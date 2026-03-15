# Domain Controller

- Role:

  - Active Directory Domain Controller for the MiniCorp network.

- Operating System:

  - Windows Server

- Domain:

  - minicorp.local

- IP Address:

  - 192.168.56.20

---

## Responsibilities

- The domain controller manages:

  - User authentication
  - Group policies
  - Domain services
  - Kerberos authentication

---

## Security Importance

- The domain controller is the most critical asset in the network.

- If attackers obtain domain administrator privileges, they can control:

  - All domain users
  - All domain computers
  - Network policies
  - File access

---

## Example Attacks

- Typical attacks against domain controllers include:

  - Kerberoasting
  - Pass-the-Hash
  - Golden Ticket attacks
  - DCSync attacks
