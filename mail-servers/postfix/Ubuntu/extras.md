### Postfix Mail Server Configuration on Ubuntu

## Table of Contents
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Installation Steps](#installation-steps)
4. [Basic Configuration](#basic-configuration)
5. [Domain Configuration](#domain-configuration)
6. [SSL Configuration](#ssl-configuration)
7. [Virtual Alias Configuration](#virtual-alias-configuration)
8. [Useful Commands](#useful-commands)
9. [Log Files for Debugging](#log-files-for-debugging)

## Overview
Postfix is a widely used open-source Mail Transfer Agent (MTA) that routes and delivers emails. It is known for its simplicity, security, and flexibility. This document provides detailed steps to configure Postfix on an Ubuntu environment.

## Prerequisites
1. Administrative privileges on your Ubuntu machine.
2. Install Postfix using the package manager:
     ```shell
     sudo apt update
     sudo apt install postfix
     ```

## Installation Steps
1. **Update Package Index:**
     ```shell
     sudo apt update
     ```

2. **Install Postfix:**
     ```shell
     sudo apt install postfix
     ```

## Basic Configuration
Modify `/etc/postfix/main.cf` with basic settings:

```ini
myhostname = mail.example.com
mydomain = example.com
myorigin = $mydomain
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mail_spool_directory = /var/mail
relayhost = 
```

## Domain Configuration
Create a domain-based setup by editing `/etc/postfix/main.cf`:

```ini
smtpd_recipient_restrictions = \
    permit_mynetworks, \
    reject_unauth_destination
```

## SSL Configuration
Modify `/etc/postfix/main.cf` to enable TLS:

```ini
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.key
smtpd_use_tls = yes
smtpd_tls_security_level = encrypt
```

Modify `/etc/postfix/master.cf` to enable secure SMTP:

```ini
smtps     inet  n       -       n       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
```

## Virtual Alias Configuration
Create the `/etc/postfix/virtual` file with mappings:

```ini
admin@example.com    user1
info@example.com     user2
support@example.com  user3
@example.com        catchall
```

Run the following command to update the virtual alias database:
```shell
sudo postmap /etc/postfix/virtual
```

## Useful Commands
- **Start Postfix:**
  ```shell
  sudo systemctl start postfix
  ```
- **Stop Postfix:**
  ```shell
  sudo systemctl stop postfix
  ```
- **Restart Postfix:**
  ```shell
  sudo systemctl restart postfix
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload postfix
  ```
- **Check Status:**
  ```shell
  sudo systemctl status postfix
  ```

## Log Files for Debugging
- **View Mail Logs:**
  ```shell
  sudo tail -f /var/log/mail.log
  ```
- **View Authentication Logs:**
  ```shell
  sudo tail -f /var/log/mail.err
  ```

This configuration document provides a structured approach for setting up Postfix Mail Server on Ubuntu. Adjust the settings as per your specific requirements and environment.