# Linux Server

## Overview

- The MiniCorp-Ubuntu server provides the Linux infrastructure for the MiniCorp enterprise environment. It hosts the public-facing web application and demonstrates practical Linux server deployment, service administration, network configuration, and web application hosting.

- The server was deployed using Ubuntu Server 24.04 LTS and configured with a LAMP-style web stack consisting of Apache HTTP Server, PHP, MariaDB, and WordPress.

- The Linux server also served as the primary target during the web application security assessment documented in this repository.

---

## Objectives

- The Linux server was implemented to:

    - Deploy a production-style Linux server.
    - Host a web application.
    - Provide a realistic target for security assessment.
    - Demonstrate Linux administration skills.
    - Integrate with the MiniCorp enterprise network.
    - Support Apache, PHP, MariaDB, and WordPress.

---

## System Information

| Property | Value |
|----------|-------|
| Hostname | MiniCorp-Ubuntu |
| Operating System | Ubuntu Server 24.04 LTS |
| Primary Role | Web Server |
| Web Server | Apache HTTP Server |
| Database | MariaDB |
| Runtime | PHP |
| Web Application | WordPress |
| Remote Administration | OpenSSH |

---

## Server Architecture

- The Ubuntu server hosts the complete web application stack.

```text
Ubuntu Server
      │
      ▼
Apache HTTP Server
      │
      ▼
PHP Runtime
      │
      ▼
WordPress
      │
      ▼
MariaDB
```

- This layered architecture separates web serving, application execution, and data storage into distinct components.

---

## Network Configuration

- The server uses two network interfaces.

| Interface | Purpose |
|-----------|---------|
| Host-Only Adapter | Internal enterprise communication |
| NAT Adapter | Internet access for package installation and updates |

- The host-only adapter enables communication with other virtual machines in the MiniCorp environment.

- The NAT adapter is used only for operating system updates, package installation, and software downloads.

---

## IP Configuration

| Network | Address |
|----------|---------|
| Enterprise Network | `192.168.192.40` |
| Internet Connectivity | NAT Adapter |

- This dual-interface configuration reflects a common deployment pattern where internal communication is separated from external connectivity.

---

## Installed Components

### Apache HTTP Server

- Apache provides HTTP services for the WordPress application.

- Responsibilities include:

    - Serving web pages
    - Processing HTTP requests
    - Delivering WordPress content
    - Supporting PHP execution

- Apache was configured to start automatically during system boot.

---

### PHP

- PHP provides the server-side runtime required by WordPress.

- Responsibilities include:

    - Dynamic page generation
    - Database interaction
    - Session handling
    - WordPress execution

---

### MariaDB

- MariaDB stores the WordPress application data.

- Responsibilities include:

    - User authentication
    - Content storage
    - Configuration storage
    - Plugin and theme data

- A dedicated database was created for the WordPress installation.

---

### WordPress

- WordPress serves as the enterprise web application deployed within the MiniCorp environment.

- The application was used during the security assessment to validate:

    - Web server configuration
    - HTTP responses
    - Administrative interface accessibility
    - Default application endpoints

---

### OpenSSH

- OpenSSH provides secure remote administration of the Linux server.

- Administrative tasks performed through SSH included:

    - Package installation
    - Service management
    - Network configuration
    - Web server administration
    - Database administration

---

## Service Management

- System services were managed using `systemd`.

- Common administrative tasks included:

    - Starting services
    - Stopping services
    - Restarting services
    - Verifying service status
    - Enabling services at boot

- Core services managed during the project included:

    - Apache
    - MariaDB

---

## File System Layout

- The project primarily interacted with the standard web server directories.

| Directory | Purpose |
|-----------|---------|
| `/var/www/html/` | Web root |
| `/etc/apache2/` | Apache configuration |
| `/etc/php/` | PHP configuration |
| `/etc/netplan/` | Network configuration |

- These locations were used during deployment and administration.

---

## Administrative Tasks Performed

- The following Linux administration tasks were completed during the project:

    - Ubuntu Server installation
    - Static network configuration
    - Hostname configuration
    - Apache installation
    - PHP installation
    - MariaDB installation
    - WordPress deployment
    - Database creation
    - Service management
    - SSH administration
    - Package updates

- These tasks demonstrate common responsibilities associated with Linux system administration.

---

## Security Considerations

- The Linux server was configured to support the project while maintaining a controlled assessment environment.

- The assessment included review of:

    - HTTP responses
    - Default WordPress endpoints
    - Apache configuration behavior
    - Administrative interface exposure
    - Publicly accessible resources

- Security observations identified during the assessment are documented separately within the Findings document.

---

## Assessment Role

- The Ubuntu server served as the primary target for the web application assessment.

- Assessment activities included:

    - Web server identification
    - Service validation
    - HTTP inspection
    - Directory enumeration
    - Configuration review
    - WordPress assessment

- These activities focused on understanding the deployed services rather than exploiting the system.

---

## Best Practices

- The following practices were followed during implementation:

    - Use a supported Long Term Support (LTS) operating system.  
    - Separate internal and external network communication.
    - Enable only required services.
    - Keep installed packages updated.
    - Manage services through `systemd`.
    - Use SSH for remote administration.
    - Regularly review web server configuration.

- These practices improve maintainability while reflecting common Linux administration standards.

---

## Related Documentation

| Document | Description |
|----------|-------------|
| `02-lab-architecture.md` | Enterprise architecture |
| `05-network-services.md` | DNS, LDAP, SMB, and networking services |
| `07-security-assessment.md` | Security assessment methodology |
| `08-findings.md` | Security findings |
| `09-hardening-recommendations.md` | Security improvement recommendations |

---

## Summary

- The MiniCorp-Ubuntu server provides the Linux infrastructure for the enterprise environment by hosting Apache, PHP, MariaDB, and WordPress on Ubuntu Server 24.04 LTS.

- The deployment demonstrates practical Linux administration skills including operating system installation, network configuration, service management, web application hosting, and remote administration.

- As the primary web server within the MiniCorp environment, it also serves as the focus of the web application assessment documented throughout this repository.
