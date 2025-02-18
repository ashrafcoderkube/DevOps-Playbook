### Caddy Server Configuration on macOS

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
1. Administrative privileges on your macOS machine.
2. Install Caddy using Homebrew:
   ```shell
   brew install caddy
   ```

## Installation Steps
1. **Install Homebrew:** If you don't have Homebrew installed, you can install it by running the following command in Terminal:
   ```shell
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Caddy:** Run the command `brew install caddy`.

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
    root * /path/to/your/site
    file_server
}
```

### SSL Configuration

```plaintext
example.com {
    root * /path/to/your/site
    file_server
    tls /path/to/your/certificates/cert.crt /path/to/your/private/key.key
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
  ```shell
  sudo caddy run
  ```
- **Stop Caddy:**
  ```shell
  sudo caddy stop
  ```
- **Restart Caddy:**
  ```shell
  sudo caddy restart
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

This detailed document should provide comprehensive guidance for configuring Caddy on macOS. Adjust the settings and configurations according to your specific needs.
