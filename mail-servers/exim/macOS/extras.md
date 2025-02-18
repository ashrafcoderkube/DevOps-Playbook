### Exim Mail Server Configuration on macOS

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
Exim is a highly configurable open-source Mail Transfer Agent (MTA) used for routing and delivering email messages. It is known for its flexibility, efficiency, and extensive configuration options. This document provides detailed steps to configure Exim on a macOS environment.

## Prerequisites
1. Administrative privileges on your macOS machine.
2. Install Exim using Homebrew:

     ```shell
     brew install exim
     ```

## Installation Steps
1. **Update Package Index:**`
     ```shell
     brew update
     ```

2. **Install Exim:**
     ```shell
     brew install exim
     ```

## Basic Configuration
Modify `/usr/local/etc/exim/exim.conf` with basic settings:

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
tls_certificate = /usr/local/etc/ssl/certs/exim.pem
tls_privatekey = /usr/local/etc/ssl/private/exim.key
tls_require_ciphers = HIGH

log_file_path = /usr/local/var/log/exim/mainlog
log_selector = +all
```


### Domain Configuration
To set up domain-specific configurations, edit the `/usr/local/etc/exim/exim.conf` file:

```ini
domainlist local_domains = @ : example.com
```

### SSL Configuration
To enable TLS, modify `/usr/local/etc/exim/exim.conf`:

```ini
tls_advertise_hosts = *
tls_certificate = /usr/local/etc/ssl/certs/exim.pem
tls_privatekey = /usr/local/etc/ssl/private/exim.key
```

### Virtual Alias Configuration
Create a virtual alias file at `/usr/local/etc/exim/virtual` and add your mappings:

```ini
admin@example.com: user1
info@example.com: user2
support@example.com: user3
@example.com: catchall
```

Add the following line to `/usr/local/etc/exim/exim.conf` to use the virtual alias file:

```ini
system_aliases:
  driver = redirect
  data = ${lookup{$local_part}lsearch{/usr/local/etc/exim/virtual}}
```

## Useful Commands
- **Start Exim:**
  ```shell
  sudo brew services start exim
  ```
- **Stop Exim:**
  ```shell
  sudo brew services stop exim
  ```
- **Restart Exim:**
  ```shell
  sudo brew services restart exim
  ```
- **Reload Configuration:**
  ```shell
  sudo kill -HUP $(pgrep exim)
  ```
- **Check Status:**
  ```shell
  sudo brew services list | grep exim
  ```

## Log Files for Debugging
- **View Mail Logs:**
  ```shell
  sudo tail -f /usr/local/var/log/exim/mainlog
  ```
- **View Rejection Logs:**
  ```shell
  sudo tail -f /usr/local/var/log/exim/rejectlog
  ```
- **View Panic Logs:**
  ```shell
  sudo tail -f /usr/local/var/log/exim/paniclog
  ```

This configuration document provides a structured approach for setting up Exim Mail Server on macOS. Adjust the settings as per your specific requirements and environment.