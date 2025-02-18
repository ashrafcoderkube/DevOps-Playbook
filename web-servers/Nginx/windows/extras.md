### Nginx Server Configuration on Windows

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
Nginx (pronounced "engine-x") is a high-performance HTTP server and reverse proxy, as well as an IMAP/POP3 proxy server. It is known for its stability, rich feature set, simple configuration, and low resource consumption. This document provides detailed steps to configure Nginx on a Windows environment.

## Prerequisites
1. Administrative privileges on your Windows machine.
2. Download and install Nginx from the official [Nginx website](https://nginx.org/en/download.html).

## Installation Steps
1. **Download Nginx:** Download the Nginx binary for Windows from the official Nginx website.
2. **Install Nginx:** Extract the downloaded archive to your desired directory (e.g., `C:\nginx`).

## Basic Configuration
### `nginx.conf`
The main configuration file for Nginx is `nginx.conf`. Below are the basic settings:

```nginx
# Define the user and worker processes
user  nginx;
worker_processes  1;

# Error log and process ID
error_log  logs/error.log;
pid        logs/nginx.pid;

# Worker settings
events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    # Log settings
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';
    access_log  logs/access.log  main;

    sendfile        on;
    keepalive_timeout  65;

    # Server configuration
    server {
        listen       80;
        server_name  localhost;

        # Root and index files
        root   html;
        index  index.html index.htm;

        location / {
            try_files $uri $uri/ =404;
        }

        # Error page handling
        error_page  500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }
}
```

## Domain Configuration
### Non-SSL Configuration

```nginx
server {
    listen       80;
    server_name  mywebsite.local;

    root   C:/nginx/html/mywebsite;
    index  index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page  500 502 503 504  /50x.html;
    location = /50x.html {
        root   html;
    }
}
```

### SSL Configuration

```nginx
server {
    listen       443 ssl;
    server_name  sslsite.local;

    root   C:/nginx/html/sslsite;
    index  index.html index.htm;

    ssl_certificate      C:/nginx/conf/ssl/server.crt;
    ssl_certificate_key  C:/nginx/conf/ssl/server.key;

    ssl_session_cache    shared:SSL:1m;
    ssl_session_timeout  5m;

    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page  500 502 503 504  /50x.html;
    location = /50x.html {
        root   html;
    }
}
```

## Proxy Configuration
To set up a reverse proxy, you need to update the configuration file:

1. **Configure Proxy:**
    ```nginx
    server {
        listen       80;
        server_name  proxy.local;

        location / {
            proxy_pass http://backend.local;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
    ```

## Useful Commands
- **Start Nginx:**
  ```shell
  start nginx
  ```
- **Stop Nginx:**
  ```shell
  nginx -s stop
  ```
- **Restart Nginx:**
  ```shell
  nginx -s reload
  ```
- **Test Configuration:**
  ```shell
  nginx -t
  ```
- **Show Version:**
  ```shell
  nginx -v
  ```
- **Show Compile Settings:**
  ```shell
  nginx -V
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts by updating the `nginx.conf` file with additional server blocks.

### Performance Tuning
1. **Enable KeepAlive:**
    ```nginx
    keepalive_timeout  65;
    ```
2. **Adjust Worker Processes and Connections:**
    ```nginx
    worker_processes  auto;
    worker_connections  1024;
    ```

### Security Settings
1. **Hide Nginx Version:**
    ```nginx
    server_tokens off;
    ```
2. **Restrict Access by IP:**
    ```nginx
    location /secure {
        allow 192.168.1.0/24;
        deny all;
    }
    ```

This detailed document should provide comprehensive guidance for configuring Nginx on Windows. Adjust the settings and configurations according to your specific needs.
