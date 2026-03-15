# Kali Attacker Machine

- Operating System:
  ```
  Kali Linux
  ```
- Role:

  - Red Team attacker system used for reconnaissance and exploitation.

---

## VM Configuration

- CPU: 2 cores
- RAM: 3 GB
- Disk: 40 GB

- Network Mode:
  ```
  Host-Only (VMnet1)
  ```
---

## Static IP Configuration

- File edited:

  - /etc/network/interfaces

- Configuration:
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.56.50
  netmask 255.255.255.0
  ```
- Restart networking:
```
sudo systemctl restart networking
```
---

## Verification
```
ip a
```
- Expected IP:
```
192.168.56.50
```
