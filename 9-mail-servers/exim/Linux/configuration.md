# Exim Configuration on Linux

## Prerequisites
1. Ensure you have administrative privileges on your Linux machine.
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

## Exim Configuration Directory
Exim typically stores its configuration files in `/etc/exim4` or `/etc/exim` for both Debian/Ubuntu-based and Red Hat/CentOS-based distributions.

#### Basic Configuration File (`exim4.conf`)

Here’s a sample of what your `exim4.conf` might look like:

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
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
tls_require_ciphers = HIGH

# Logging
log_file_path = /var/log/exim4/mainlog
log_selector = +all
``` 

## Commands to Start, Stop, and Restart Exim

- **Start Exim:**
  ```shell
  sudo systemctl start exim
  ```
- **Stop Exim:**
  ```shell
  sudo systemctl stop exim
  ```
- **Restart Exim:**
  ```shell
  sudo systemctl restart exim
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload exim
  ```
- **Check Exim:**
  ```shell
  sudo systemctl status exim
  ```

#### Virtual Alias Configuration (`virtual`)
Exim stores virtual alias mappings in `/etc/exim4/virtual`.

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

#### Enabling SSL (`exim4.conf`)

Modify `/etc/exim4/exim4.conf` to enable TLS support:

```ini
# Enable TLS encryption
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
tls_require_ciphers = HIGH
```

#### Log Files for Debugging

- **View Mail Logs:**
  ```shell
  sudo tail -f /var/log/exim4/mainlog
  ```
- **View Authentication Logs:**
  ```shell
  sudo tail -f /var/log/exim4/rejectlog
  ```

This configuration should help you set up Exim on a Linux environment. You can adjust the settings based on your specific distribution and requirements.
