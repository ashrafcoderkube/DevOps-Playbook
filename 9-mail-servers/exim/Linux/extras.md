# Exim Mail Server Configuration on Linux

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
Exim is a highly configurable open-source Mail Transfer Agent (MTA) used for routing and delivering email messages. It is known for its flexibility, efficiency, and extensive configuration options. This document provides detailed steps to configure Exim on a Linux environment.

## Prerequisites
1. Administrative privileges on your Linux machine.
2. Install Exim using the package manager for your Linux distribution:
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt update
     sudo apt install exim4
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install exim
     ```

## Installation Steps
1. **Update Package Index:**
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt update
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum update
     ```

2. **Install Exim:**
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt install exim4
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install exim
     ```

## Basic Configuration
Modify `/etc/exim4/update-exim4.conf.conf` with basic settings:

```ini
dc_eximconfig_configtype='internet'
dc_other_hostnames='mail.example.com'
dc_local_interfaces='0.0.0.0'
dc_readhost='example.com'
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost=''
CFILEMODE='644'
```

### After modifying the configuration file, run the following command to apply the changes:

```Shell
  sudo update-exim4.conf
```

## Domain Configuration
To set up domain-specific configurations, edit the `/etc/exim4/exim4.conf.template` file:

```ini
domainlist local_domains = @ : example.com
```

## SSL Configuration
To enable TLS, modify `/etc/exim4/exim4.conf.template`:

```ini
tls_advertise_hosts = *
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
```

## Virtual Alias Configuration
Create a virtual alias file at  `/etc/exim4/virtual` and add your mappings:

```ini
admin@example.com: user1
info@example.com: user2
support@example.com: user3
@example.com: catchall
```

Add the following line to `/etc/exim4/exim4.conf.template` to use the virtual alias file:
```ini
system_aliases:
  driver = redirect
  data = ${lookup{$local_part}lsearch{/etc/exim4/virtual}}
```

## Useful Commands
- **Start Exim:**
  ```shell
  sudo systemctl start exim4
  ```
- **Stop Exim:**
  ```shell
  sudo systemctl stop exim4
  ```
- **Restart Exim:**
  ```shell
  sudo systemctl restart exim4
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload exim4
  ```
- **Check Status:**
  ```shell
  sudo systemctl status exim4
  ```

## Log Files for Debugging
- **View Mail Logs:**
  ```shell
  sudo tail -f /var/log/exim4/mainlog
  ```
- **View Rejection Logs:**
  ```shell
  sudo tail -f /var/log/exim4/rejectlog
  ```
- **View Panic Logs:**
  ```shell
sudo tail -f /var/log/exim4/paniclog
  ```

This configuration document provides a structured approach for setting up Postfix Mail Server on Linux. Adjust the settings as per your specific requirements and environment.