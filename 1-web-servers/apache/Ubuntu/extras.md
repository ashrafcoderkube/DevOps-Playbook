### Apache Server Configuration on Ubuntu

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
Apache HTTP Server is a powerful, flexible, and widely-used open-source web server. It supports a wide range of features, including module-based extension capabilities, secure SSL/TLS support, and robust configuration options. This document provides detailed steps to configure Apache on an Ubuntu environment.

## Prerequisites
1. Administrative privileges on your Ubuntu machine.
2. Install Apache using the package manager:
   ```shell
   sudo apt update
   sudo apt install apache2
   ```

## Installation Steps
1. **Update Package Index:**
   ```shell
   sudo apt update
   ```

2. **Install Apache:**
   ```shell
   sudo apt install apache2
   ```

## Basic Configuration
### `apache2.conf`
The main configuration file for Apache is `apache2.conf`. Below are the basic settings:

```apache
# Global configuration
Mutex file:${APACHE_LOCK_DIR} default
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 5

# Server Root Directory
ServerRoot "/etc/apache2"

# Listen for requests on port 80
Listen 80

# Load Modules
LoadModule mpm_event_module /usr/lib/apache2/modules/mod_mpm_event.so
LoadModule authn_core_module /usr/lib/apache2/modules/mod_authn_core.so
LoadModule authz_core_module /usr/lib/apache2/modules/mod_authz_core.so
LoadModule dir_module /usr/lib/apache2/modules/mod_dir.so
LoadModule mime_module /usr/lib/apache2/modules/mod_mime.so
LoadModule log_config_module /usr/lib/apache2/modules/mod_log_config.so
LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so

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
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

# MIME Types
TypesConfig /etc/mime.types

# Include other configuration files
IncludeOptional conf-enabled/*.conf
IncludeOptional sites-enabled/*.conf
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

    ErrorLog ${APACHE_LOG_DIR}/mywebsite-error.log
    CustomLog ${APACHE_LOG_DIR}/mywebsite-access.log combined
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

    ErrorLog ${APACHE_LOG_DIR}/sslsite-error.log
    CustomLog ${APACHE_LOG_DIR}/sslsite-access.log combined

    SSLEngine on
    SSLCertificateFile "/etc/ssl/certs/server.crt"
    SSLCertificateKeyFile "/etc/ssl/private/server.key"
</VirtualHost>
```

## Proxy Configuration
1. **Enable Proxy Modules:**
    Add the following lines to your `apache2.conf` file:
    ```apache
    LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
    LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
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
  sudo systemctl start apache2
  ```
- **Stop Apache:**
  ```shell
  sudo systemctl stop apache2
  ```
- **Restart Apache:**
  ```shell
  sudo systemctl restart apache2
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload apache2
  ```
- **Test Configuration:**
  ```shell
  sudo apache2ctl configtest
  ```
- **Show Version:**
  ```shell
  apache2 -v
  ```
- **Show Compile Settings:**
  ```shell
  apache2 -V
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts in the `sites-enabled` directory.

### Performance Tuning
1. **Enable KeepAlive:**
    ```apache
    KeepAlive On
    MaxKeepAliveRequests 100
    KeepAliveTimeout 5
    ```
2. **Configure Multi-Processing Modules (MPM):**
    Adjust the `mpm_event` settings in the `apache2.conf` file to optimize performance.

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

This detailed document should provide comprehensive guidance for configuring Apache on Ubuntu. Adjust the settings and configurations according to your specific needs.
