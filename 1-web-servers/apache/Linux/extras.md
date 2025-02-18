### Apache Server Configuration on Linux

## Table of Contents
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Installation Steps](#installation-steps)
4. [Basic Configuration](#basic-configuration)
5. [Domain Configuration](#domain-configuration)
6. [SSL Configuration](#ssl-configuration)
7. [Proxy Configuration](#proxy-configuration)
8. [Useful Commands](#useful-commands)
9. [Additional Details](#additional-details)

## Overview
Apache HTTP Server is a powerful, flexible, and widely-used open-source web server. It supports a wide range of features, including module-based extension capabilities, secure SSL/TTLS support, and robust configuration options. This document provides detailed steps to configure Apache on a Linux environment.

## Prerequisites
1. Administrative privileges on your Linux machine.
2. Install Apache using the package manager for your Linux distribution:
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt update
     sudo apt install apache2
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install httpd
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

2. **Install Apache:**
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt install apache2
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install httpd
     ```

## Basic Configuration
### `httpd.conf` or `apache2.conf`
The main configuration file for Apache is `httpd.conf` or `apache2.conf` depending on your distribution. Below are the basic settings:

```apache
# Server Root Directory
ServerRoot "/etc/apache2"  # For Debian/Ubuntu
# ServerRoot "/etc/httpd"  # For Red Hat/CentOS

# Listen for requests on port 80
Listen 80

# Load Modules
LoadModule mpm_event_module modules/mod_mpm_event.so
LoadModule authn_core_module modules/mod_authn_core.so
LoadModule authz_core_module modules/mod_authz_core.so
LoadModule dir_module modules/mod_dir.so
LoadModule mime_module modules/mod_mime.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule alias_module modules/mod_alias.so

# Define Server Admin and Server Name
ServerAdmin admin@example.com
ServerName localhost:80

# Document Root
DocumentRoot "/var/www/html"

# Directory Settings
<Directory "/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

# Log Settings
ErrorLog "/var/log/apache2/error_log"  # For Debian/Ubuntu
# ErrorLog "/var/log/httpd/error_log"  # For Red Hat/CentOS
CustomLog "/var/log/apache2/access_log" common  # For Debian/Ubuntu
# CustomLog "/var/log/httpd/access_log" common  # For Red Hat/CentOS

# MIME Types
TypesConfig /etc/mime.types

# Include other configuration files
Include /etc/apache2/sites-enabled/*.conf  # For Debian/Ubuntu
# Include /etc/httpd/conf.d/*.conf  # For Red Hat/CentOS
```

## Domain Configuration
### Non-SSL Configuration

```apache
<VirtualHost *:80>
    DocumentRoot "/var/www/html/mywebsite"
    ServerName mywebsite.local

    <Directory "/var/www/html/mywebsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/var/log/apache2/mywebsite-error.log"  # For Debian/Ubuntu
    # ErrorLog "/var/log/httpd/mywebsite-error.log"  # For Red Hat/CentOS
    CustomLog "/var/log/apache2/mywebsite-access.log" common  # For Debian/Ubuntu
    # CustomLog "/var/log/httpd/mywebsite-access.log" common  # For Red Hat/CentOS
</VirtualHost>
```

### SSL Configuration

```apache
<VirtualHost _default_:443>
    DocumentRoot "/var/www/html/sslsite"
    ServerName sslsite.local:443

    <Directory "/var/www/html/sslsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/var/log/apache2/sslsite-error.log"  # For Debian/Ubuntu
    # ErrorLog "/var/log/httpd/sslsite-error.log"  # For Red Hat/CentOS
    CustomLog "/var/log/apache2/sslsite-access.log" common  # For Debian/Ubuntu
    # CustomLog "/var/log/httpd/sslsite-access.log" common  # For Red Hat/CentOS

    SSLEngine on
    SSLCertificateFile "/etc/ssl/certs/server.crt"
    SSLCertificateKeyFile "/etc/ssl/private/server.key"
</VirtualHost>
```

## Proxy Configuration
1. **Enable Proxy Modules:**
    Add the following lines to your `httpd.conf` file:
    ```apache
    LoadModule proxy_module modules/mod_proxy.so
    LoadModule proxy_http_module modules/mod_proxy_http.so
    ```

2. **Configure Proxy:**
    ```apache
    <VirtualHost *:80>
        ServerName proxy.local
        ProxyRequests Off
        ProxyPass / http://backend.local/
        ProxyPassReverse / http://backend.local/
    </VirtualHost>
    ```

## Useful Commands
- **Start Apache:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl start apache2
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl start httpd
    ```
- **Stop Apache:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl stop apache2
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl stop httpd
    ```
- **Restart Apache:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl restart apache2
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl restart httpd
    ```
- **Reload Configuration:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl reload apache2
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl reload httpd
    ```
- **Test Configuration:**
  ```shell
  sudo apache2ctl configtest  # For Debian/Ubuntu
  sudo httpd -t               # For Red Hat/CentOS
  ```
- **Show Version:**
  ```shell
  apache2 -v  # For Debian/Ubuntu
  httpd -v    # For Red Hat/CentOS
  ```
- **Show Compile Settings:**
  ```shell
  apache2 -V  # For Debian/Ubuntu
  httpd -V    # For Red Hat/CentOS
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts in the `sites-enabled` directory for Debian/Ubuntu or the `conf.d` directory for Red Hat/CentOS.

### Performance Tuning
1. **Enable KeepAlive:**
    ```apache
    KeepAlive On
    MaxKeepAliveRequests 100
    KeepAliveTimeout 5
    ```
2. **Configure Multi-Processing Modules (MPM):**
    Adjust the `mpm_event` settings in the `httpd.conf` file to optimize performance.

### Security Settings
1. **Hide Apache Version:**
    ```apache
    ServerSignature Off
    ServerTokens Prod
    ```
2. **Restrict Access by IP:**
    ```apache
    <Directory "/var/www/html/secure">
        Require ip 192.168.1.0/24
    </Directory>
    ```

This detailed document should provide comprehensive guidance for configuring Apache on Linux. Adjust the settings and configurations according to your specific needs.
