### Exim Mail Server Configuration on Windows

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
Exim is a highly configurable open-source Mail Transfer Agent (MTA) used for routing and delivering email messages. It is known for its flexibility, efficiency, and extensive configuration options. This document provides detailed steps to configure Exim on a Windows environment using Cygwin.

## Prerequisites
1. Administrative privileges on your Windows machine.

2. Install Cygwin with the required packages, including Exim.
    - Visit the Cygwin website.
    - Download the setup executable and install Cygwin.
    - During the installation, select the `Exim` package.

## Installation Steps
1. **Update Package Index:**`
     ```shell
     apt-cyg update
     ```

2. **Install Exim:**
     ```shell
     apt-cyg install exim
     ```

## Basic Configuration
Modify `/etc/exim/exim.conf` within the Cygwin environment with basic settings:
```ini
primary_hostname = mail.example.com
domainlist local_domains = @ : example.com
smarthost = 

interface_list = *
host_lookup = *
transport_smtp = smtp

message_spool_directory = /var/mail
delivery_mode = smtp

acl_check_rcpt = acl_check_rcpt_local

tls_on_connect_ports = 465
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
tls_require_ciphers = HIGH

log_file_path = /var/log/exim/mainlog
log_selector = +all
```


### Domain Configuration
To set up domain-specific configurations, edit the `/etc/exim/exim.conf` file within the Cygwin environment:

```ini
domainlist local_domains = @ : example.com
```

### SSL Configuration
To enable TLS, modify `/etc/exim/exim.conf` within the Cygwin environment:

```ini
tls_advertise_hosts = *
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
```

### Virtual Alias Configuration
Create a virtual alias file at `/etc/exim/virtual` within the Cygwin environment and add your mappings:

```ini
admin@example.com: user1
info@example.com: user2
support@example.com: user3
@example.com: catchall
```

Add the following line to `/etc/exim/exim.conf` within the Cygwin environment to use the virtual alias file:

```ini
system_aliases:
  driver = redirect
  data = ${lookup{$local_part}lsearch{/etc/exim/virtual}}
```

## Useful Commands
- **Start Exim:**
  ```shell
  cygrunsrv -S 
  ```
- **Stop Exim:**
  ```shell
  cygrunsrv -E exim
  ```
- **Restart Exim:**
  ```shell
  cygrunsrv -R exim
  ```
- **Reload Configuration:**
  ```shell
  exim -qff
  ```
- **Check Status:**
  ```shell
  cygrunsrv -Q exim
  ```

## Log Files for Debugging
- **View Mail Logs:**
  ```shell
  tail -f /var/log/exim/mainlog
  ```
- **View Rejection Logs:**
  ```shell
  tail -f /var/log/exim/rejectlog
  ```
- **View Panic Logs:**
  ```shell
  tail -f /var/log/exim/paniclog
  ```

This configuration document provides a structured approach for setting up Exim Mail Server on Windows using Cygwin. Adjust the settings as per your specific requirements and environment.