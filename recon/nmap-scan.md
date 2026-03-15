# Nmap Reconnaissance

- Command used:
  ```
  nmap -sC -sV -p- 192.168.56.10
  ```
---

## Results

- Open Ports:
  ```
  22/tcp
  SSH - OpenSSH 9.6p1

  80/tcp
  HTTP - Apache 2.4.58
  ```
---

## Observations

- WordPress detected through HTTP headers.

- Server identified as Ubuntu running Apache.
