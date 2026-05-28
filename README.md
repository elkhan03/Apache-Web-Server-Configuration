# Apache Web Server Deployment & Security Hardening

This repository contains the configuration files and step-by-step documentation for deploying a secure, TLS-encrypted Apache Web Server on an RHEL-based Linux environment.

---

## Deployment Architecture

* **Custom Document Root:** `/web/project`
* **Virtual Host Configuration:** `/etc/httpd/conf.d/project.conf`
* **Target Domain:** `project.local` (Local DNS)
* **Secure Port:** `443` (HTTPS) with permanent port `80` redirection

---

## Technical Directory Structure

```text
apache-project/
├── index.html          # Web application source
├── project.conf        # Custom production Virtual Host file
└── README.md           # Engineering documentation
