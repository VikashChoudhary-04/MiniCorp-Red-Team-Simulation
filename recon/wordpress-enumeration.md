# WordPress Enumeration

- Tool used:

  - wpscan

- Command:
  ```
  wpscan --url http://192.168.56.10 --enumerate ap
  ```
---

## Findings

- XML-RPC enabled

- Upload directory listing enabled

- WordPress theme:

  - twentytwentyfive

---

## User Enumeration

- Command:
  ```
  wpscan --url http://192.168.56.10 --enumerate u
  ```
- Result:
  ```
  admin
  ```
---

## Plugin Discovery

- Manual validation:
  ```
  curl -I http://192.168.56.10/wp-content/plugins/wp-file-manager/
  ```
- Result:
  ```
  200 OK
  ```
- Confirmed plugin:
  ```
  WP File Manager
  ```
