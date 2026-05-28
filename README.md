# Apache Web Server Configuration and Security Management

This project demonstrates the deployment, configuration, and security hardening of an Apache Web Server on a Linux-based system.

:contentReference[oaicite:0]{index=0}

---

## Overview

This project is focused on setting up a secure and functional web server using Apache. It includes virtual host configuration, SSL encryption, firewall setup, and basic security hardening.

---

## Objectives

- Install and configure Apache Web Server
- Create virtual hosts for custom domain
- Configure local domain (project.local)
- Enable HTTPS using SSL certificate
- Apply basic security settings
- Configure logging system

---

## Environment

- Operating System: Linux (RHEL-based)
- Web Server: Apache HTTP Server
- Domain: project.local (local testing)
- SSL: Self-signed certificate

---

## Project Structure

apache-project/
│
├── index.html
├── README.md
└── screenshots/

/web/project  
/etc/httpd/conf.d/project.conf

---

## Installation & Configuration

Install Apache:

sudo dnf install httpd -y

Start and enable service:

sudo systemctl start httpd
sudo systemctl enable httpd

---

## Virtual Host Configuration

<VirtualHost *:80>
    ServerName project.local
    Redirect permanent / https://project.local/
</VirtualHost>

<VirtualHost *:443>
    ServerName project.local
    DocumentRoot /web/project

    SSLEngine on
    SSLCertificateFile /etc/httpd/ssl/project.crt
    SSLCertificateKeyFile /etc/httpd/ssl/project.key

    <Directory /web/project>
        Require all granted
        Options -Indexes
    </Directory>
</VirtualHost>

---

## Security Features

- SSL encryption enabled (HTTPS)
- Directory listing disabled
- Basic access control configured
- SELinux security applied

:contentReference[oaicite:1]{index=1}  
:contentReference[oaicite:2]{index=2}  

---

## SSL Certificate Creation

openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/httpd/ssl/project.key \
-out /etc/httpd/ssl/project.crt

---

## Firewall Configuration

sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload

---

## Logging

Access Log:
 /var/log/httpd/project-access.log

Error Log:
 /var/log/httpd/project-error.log

---

## Testing

Open in browser:

http://project.local
https://project.local

---

## Screenshots

Add screenshots here showing:

- Apache installation
- Service running status
- Virtual host configuration
- Website working
- HTTPS warning page
- Logs output

---

## Note

This project uses a self-signed SSL certificate, so browser may show "Not Secure" warning. This is expected in a local environment.

---

## Conclusion

This project demonstrates a complete Apache web server setup with virtual hosting, SSL configuration, firewall setup, and basic security hardening on a Linux system.
