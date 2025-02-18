### Exim Configuration on macOS

#### Prerequisites
1. Ensure you have administrative privileges on your macOS machine.
2. Install Exim using Homebrew:
     ```shell
     brew install exim
     ```

#### Exim Configuration Directory
Exim stores its configuration files in `/usr/local/etc/exim`.
Basic Configuration File (`exim.conf`)
Here’s a sample of what your `exim.conf` might look like:

```ini
# Network settings
primary_hostname = mail.example.com
domainlist local_domains = @ : example.com
smarthost = 

# Relay settings
interface_list = *
host_lookup = *
transport_smtp = smtp

# Mailbox settings
message_spool_directory = /var/mail
delivery_mode = smtp

# Restrict mail relay
acl_check_rcpt = acl_check_rcpt_local

# TLS encryption settings
tls_on_connect_ports = 465
tls_certificate = /usr/local/etc/ssl/certs/exim.pem
tls_privatekey = /usr/local/etc/ssl/private/exim.key
tls_require_ciphers = HIGH

# Logging
log_file_path = /usr/local/var/log/exim/mainlog
log_selector = +all
``` 

#### Commands to Start, Stop, and Restart Exim

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
- **Check Exim:**
  ```shell
  sudo brew services list | grep exim
  ```

#### Virtual Alias Configuration (`virtual`)
Exim stores virtual alias mappings in `/usr/local/etc/exim/virtual`.
```ini
# Virtual alias mappings
admin@example.com    user1
info@example.com     user2
support@example.com  user3
@example.com         catchall
```

Run the following command to update the virtual alias database:
```shell
sudo exim -bV
```

#### Enabling SSL (`exim.conf`)

Modify `/usr/local/etc/exim/exim.conf` to enable TLS support:

```ini
# Enable TLS encryption
tls_certificate = /usr/local/etc/ssl/certs/exim.pem
tls_privatekey = /usr/local/etc/ssl/private/exim.key
tls_require_ciphers = HIGH
```

#### Log Files for Debugging

- **View Mail Logs:**
  ```shell
  sudo tail -f /usr/local/var/log/exim/mainlog
  ```
- **View Authentication Logs:**
  ```shell
  sudo tail -f /usr/local/var/log/exim/rejectlog
  ```

This configuration should help you set up Exim on a macOS environment. You can adjust the settings based on your specific requirements and environment.