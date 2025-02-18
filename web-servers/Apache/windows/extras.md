### Apache Server Configuration on Windows

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
Apache HTTP Server is a powerful, flexible, and widely-used open-source web server. It supports a wide range of features, including module-based extension capabilities, secure SSL/TLS support, and robust configuration options. This document provides detailed steps to configure Apache on a Windows environment.

## Prerequisites
1. Administrative privileges on your Windows machine.
2. Download and install Apache HTTP Server from the official [Apache website](https://httpd.apache.org/download.cgi).

## Installation Steps
1. **Download Apache:** Download the Apache HTTP Server binary for Windows from the official Apache website.
2. **Install Apache:** Run the downloaded installer and follow the instructions to install Apache in your desired directory (e.g., `C:\Apache24`).

## Basic Configuration
### `httpd.conf`
The main configuration file for Apache is `httpd.conf`. Below are the basic settings:

```apache
# Server Root Directory
ServerRoot "C:/Apache24"

# Listen for requests on port 80
Listen 80

# Load Modules
LoadModule mpm_winnt_module modules/mod_mpm_winnt.so
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule dir_module modules/mod_dir.so
LoadModule mime_module modules/mod_mime.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule alias_module modules/mod_alias.so

# Define Server Admin and Server Name
ServerAdmin admin@example.com
ServerName localhost:80

# Document Root
DocumentRoot "C:/Apache24/htdocs"

# Directory Settings
<Directory "C:/Apache24/htdocs">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

# Log Settings
ErrorLog "logs/error.log"
CustomLog "logs/access.log" common

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
    DocumentRoot "C:/Apache24/htdocs/mywebsite"
    ServerName mywebsite.local

    <Directory "C:/Apache24/htdocs/mywebsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "logs/mywebsite-error.log"
    CustomLog "logs/mywebsite-access.log" common
</VirtualHost>
```

### SSL Configuration

```apache
<VirtualHost _default_:443>
    DocumentRoot "C:/Apache24/htdocs/sslsite"
    ServerName sslsite.local:443

    <Directory "C:/Apache24/htdocs/sslsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "logs/sslsite-error.log"
    CustomLog "logs/sslsite-access.log" common

    SSLEngine on
    SSLCertificateFile "conf/ssl/server.crt"
    SSLCertificateKeyFile "conf/ssl/server.key"
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
  ```shell
  httpd -k start
  ```
- **Stop Apache:**
  ```shell
  httpd -k stop
  ```
- **Restart Apache:**
  ```shell
  httpd -k restart
  ```
- **Reload Configuration:**
  ```shell
  httpd -k graceful
  ```
- **Test Configuration:**
  ```shell
  httpd -t
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
    Adjust the `mpm_winnt` settings in the `httpd.conf` file to optimize performance.

### Security Settings
1. **Hide Apache Version:**
    ```apache
    ServerSignature Off
    ServerTokens Prod
    ```
2. **Restrict Access by IP:**
    ```apache
    <Directory "C:/Apache24/htdocs/secure">
        Require ip 192.168.1.0/24
    </Directory>
    ```

This detailed document should provide comprehensive guidance for configuring Apache on Windows. Adjust the settings and configurations according to your specific needs.
