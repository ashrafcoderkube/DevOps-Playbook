### Caddy Server Configuration on Linux

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
Caddy is a powerful, open-source web server that provides automatic HTTPS and reverse proxy capabilities. It's known for its simplicity and ease of use.

## Prerequisites
1. Administrative privileges on your Linux machine.
2. Install Caddy using the package manager for your Linux distribution:
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt update
     sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
     curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo apt-key add -
     curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee -a /etc/apt/sources.list.d/caddy-stable.list
     sudo apt update
     sudo apt install caddy
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install yum-plugin-copr
     sudo yum copr enable @caddy/caddy
     sudo yum install caddy
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

2. **Install Caddy:**
   - For Debian/Ubuntu-based distributions:
     ```shell
     sudo apt install caddy
     ```
   - For Red Hat/CentOS-based distributions:
     ```shell
     sudo yum install caddy
     ```

## Basic Configuration
### `Caddyfile`
The main configuration file for Caddy is `Caddyfile`. Below are the basic settings:

```plaintext
localhost:2015 {
    respond "Hello, world!"
}
```

## Domain Configuration
### Non-SSL Configuration

```plaintext
example.com:80 {
    root * /var/www/mywebsite
    file_server
}
```

### SSL Configuration

```plaintext
example.com {
    root * /var/www/sslsite
    file_server
    tls /etc/ssl/certs/server.crt /etc/ssl/private/server.key
}
```

## Proxy Configuration
To set up a reverse proxy, you need to update the configuration file:

```plaintext
proxy.example.com {
    reverse_proxy localhost:2015
}
```

## Useful Commands
- **Start Caddy:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl start caddy
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl start caddy
    ```
- **Stop Caddy:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl stop caddy
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl stop caddy
    ```
- **Restart Caddy:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl restart caddy
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl restart caddy
    ```
- **Reload Configuration:**
  - For Debian/Ubuntu-based distributions:
    ```shell
    sudo systemctl reload caddy
    ```
  - For Red Hat/CentOS-based distributions:
    ```shell
    sudo systemctl reload caddy
    ```
- **Test Configuration:**
  ```shell
  sudo caddy validate
  ```
- **Show Version:**
  ```shell
  caddy version
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts by updating the `Caddyfile` with additional server blocks.

### Performance Tuning
1. **Enable KeepAlive:**
    ```plaintext
    localhost:2015 {
        header Connection keep-alive
    }
    ```
2. **Adjust Worker Processes and Connections:**
    ```plaintext
    workers {
        threads 4
    }
    ```

### Security Settings
1. **Hide Caddy Version:**
    ```plaintext
    caddy {
        hide_version
    }
    ```
2. **Restrict Access by IP:**
    ```plaintext
    example.com {
        @internal {
            remote_ip 192.168.1.0/24
        }
        reverse_proxy @internal
    }
    ```

This detailed document should provide comprehensive guidance for configuring Caddy on Linux. Adjust the settings and configurations according to your specific needs.
