### Apache Server Configuration on macOS

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
Apache HTTP Server is a powerful, flexible, and widely-used open-source web server. It supports a wide range of features, including module-based extension capabilities, secure SSL/TLS support, and robust configuration options. This document provides detailed steps to configure Apache on macOS.

## Prerequisites
1. Administrative privileges on your macOS machine.
2. Apache comes pre-installed on macOS. You can verify this by running the following command in Terminal:
   ```shell
   httpd -v
   ```
3. If Apache is not installed, you can install it using Homebrew:
   ```shell
   brew install httpd
   ```

## Installation Steps
1. **Check Apache Installation:** Verify if Apache is already installed by running `httpd -v`.
2. **Install Apache via Homebrew (if needed):** Run the command `brew install httpd`.

## Basic Configuration
### `httpd.conf`
The main configuration file for Apache is `httpd.conf`. Below are the basic settings:

```apache
# Server Root Directory
ServerRoot "/usr/local/opt/httpd"

# Listen for requests on port 80
Listen 80

# Load Modules
LoadModule mpm_event_module libexec/mod_mpm_event.so
LoadModule authn_core_module libexec/mod_authn_core.so
LoadModule authz_core_module libexec/mod_authz_core.so
LoadModule dir_module libexec/mod_dir.so
LoadModule mime_module libexec/mod_mime.so
LoadModule log_config_module libexec/mod_log_config.so
LoadModule alias_module libexec/mod_alias.so

# Define Server Admin and Server Name
ServerAdmin admin@example.com
ServerName localhost:80

# Document Root
DocumentRoot "/usr/local/var/www"

# Directory Settings
<Directory "/usr/local/var/www">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

# Log Settings
ErrorLog "/usr/local/var/log/httpd/error_log"
CustomLog "/usr/local/var/log/httpd/access_log" common

# MIME Types
TypesConfig conf/mime.types

# Include other configuration files
Include conf/extra/httpd-vhosts.conf
Include conf/extra/httpd-ssl.conf
```

## Domain Configuration
### Non-SSL Configuration

```apache
<VirtualHost *:80>
    DocumentRoot "/usr/local/var/www/mywebsite"
    ServerName mywebsite.local

    <Directory "/usr/local/var/www/mywebsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/usr/local/var/log/httpd/mywebsite-error.log"
    CustomLog "/usr/local/var/log/httpd/mywebsite-access.log" common
</VirtualHost>
```

### SSL Configuration

```apache
<VirtualHost _default_:443>
    DocumentRoot "/usr/local/var/www/sslsite"
    ServerName sslsite.local:443

    <Directory "/usr/local/var/www/sslsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/usr/local/var/log/httpd/sslsite-error.log"
    CustomLog "/usr/local/var/log/httpd/sslsite-access.log" common

    SSLEngine on
    SSLCertificateFile "/usr/local/etc/httpd/ssl/server.crt"
    SSLCertificateKeyFile "/usr/local/etc/httpd/ssl/server.key"
</VirtualHost>
```

## Proxy Configuration
1. **Enable Proxy Modules:**
    Add the following lines to your `httpd.conf` file:
    ```apache
    LoadModule proxy_module libexec/mod_proxy.so
    LoadModule proxy_http_module libexec/mod_proxy_http.so
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
  ```shell
  sudo apachectl start
  ```
- **Stop Apache:**
  ```shell
  sudo apachectl stop
  ```
- **Restart Apache:**
  ```shell
  sudo apachectl restart
  ```
- **Reload Configuration:**
  ```shell
  sudo apachectl graceful
  ```
- **Test Configuration:**
  ```shell
  sudo apachectl configtest
  ```
- **Show Version:**
  ```shell
  httpd -v
  ```
- **Show Compile Settings:**
  ```shell
  httpd -V
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts in the `httpd-vhosts.conf` file.

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
    <Directory "/usr/local/var/www/secure">
        Require ip 192.168.1.0/24
    </Directory>
    ```

This detailed document should provide comprehensive guidance for configuring Apache on macOS. Adjust the settings and configurations according to your specific needs.
