### LiteSpeed Server Configuration on Linux

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
LiteSpeed Web Server is a high-performance, secure, and easy-to-use server known for its advanced features and compatibility with Apache. This document provides detailed steps to configure LiteSpeed on a Linux environment.

## Prerequisites
1. Administrative privileges on your Linux machine.
2. Install LiteSpeed Web Server by downloading the installer from the official [LiteSpeed website](https://www.litespeedtech.com/products/litespeed-web-server/download).

## Installation Steps
1. **Download LiteSpeed:** Download the LiteSpeed installer for Linux from the official LiteSpeed website.
2. **Install LiteSpeed:** Extract the downloaded archive and run the installer:
   ```shell
   tar -xzvf lsws-<version>.tgz
   cd lsws-<version>
   sudo ./install.sh
   ```

## Basic Configuration
### `httpd_config.xml`
The main configuration file for LiteSpeed is `httpd_config.xml`. Below are the basic settings:

```xml
<httpServer>
    <general>
        <serverName>MyLiteSpeedServer</serverName>
        <adminRoot>/usr/local/lsws/admin</adminRoot>
        <serverRoot>/usr/local/lsws</serverRoot>
    </general>
    <listener>
        <address>*:80</address>
        <name>Default</name>
        <secure>0</secure>
    </listener>
    <virtualHost>
        <name>MyVirtualHost</name>
        <root>/usr/local/lsws/Example/html</root>
        <docRoot>/usr/local/lsws/Example/html</docRoot>
    </virtualHost>
</httpServer>
```

## Domain Configuration
### Non-SSL Configuration

```xml
<virtualHost>
    <name>mywebsite.local</name>
    <root>/usr/local/lsws/mywebsite/html</root>
    <docRoot>/usr/local/lsws/mywebsite/html</docRoot>
</virtualHost>
```

### SSL Configuration

```xml
<listener>
    <address>*:443</address>
    <name>SSLListener</name>
    <secure>1</secure>
    <sslCert>/usr/local/lsws/ssl/server.crt</sslCert>
    <sslKey>/usr/local/lsws/ssl/server.key</sslKey>
</listener>

<virtualHost>
    <name>sslsite.local</name>
    <root>/usr/local/lsws/sslsite/html</root>
    <docRoot>/usr/local/lsws/sslsite/html</docRoot>
</virtualHost>
```

## Proxy Configuration
To set up a reverse proxy, you need to update the configuration file:

```xml
<virtualHost>
    <name>proxy.local</name>
    <root>/usr/local/lsws/proxy/html</root>
    <docRoot>/usr/local/lsws/proxy/html</docRoot>
    <context>
        <type>proxy</type>
        <uri>/*</uri>
        <address>http://backend.local</address>
    </context>
</virtualHost>
```

## Useful Commands
- **Start LiteSpeed:**
  ```shell
  sudo /usr/local/lsws/bin/lswsctrl start
  ```
- **Stop LiteSpeed:**
  ```shell
  sudo /usr/local/lsws/bin/lswsctrl stop
  ```
- **Restart LiteSpeed:**
  ```shell
  sudo /usr/local/lsws/bin/lswsctrl restart
  ```
- **Test Configuration:**
  ```shell
  sudo /usr/local/lsws/bin/lswsctrl configtest
  ```
- **Show Version:**
  ```shell
  sudo /usr/local/lsws/bin/lswsctrl version
  ```

## Additional Details
### Setting Up Virtual Hosts
To set up multiple websites on the same server, you can configure Virtual Hosts by updating the `httpd_config.xml` file with additional virtual host blocks.

### Performance Tuning
1. **Enable KeepAlive:**
    ```xml
    <tuning>
        <keepAlive>1</keepAlive>
        <keepAliveTimeout>15</keepAliveTimeout>
    </tuning>
    ```
2. **Adjust Worker Processes and Connections:**
    ```xml
    <tuning>
        <maxConnections>500</maxConnections>
    </tuning>
    ```

### Security Settings
1. **Hide LiteSpeed Version:**
    ```xml
    <security>
        <serverSignature>0</serverSignature>
    </security>
    ```
2. **Restrict Access by IP:**
    ```xml
    <accessControl>
        <allow>192.168.1.0/24</allow>
        <deny>*</deny>
    </accessControl>
    ```

This detailed document should provide comprehensive guidance for configuring LiteSpeed on Linux. Adjust the settings and configurations according to your specific needs.