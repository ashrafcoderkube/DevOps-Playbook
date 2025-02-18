# Domain Configuration for Exim Mail Server on Ubuntu

## Prerequisites
- A Linux server with administrative (root) privileges.
- A valid domain name (e.g., example.com).
- Exim installed on your system.
- A valid SSL/TLS certificate (for SSL configuration).

## Non-SSL Configuration
Edit the main Exim configuration file located at `/etc/exim4/exim4.conf`.

```ini
# Basic Exim configuration for mail delivery
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

# Logging
log_file_path = /var/log/exim4/mainlog
log_selector = +all

``` 

## SSL Configuration

To enable SSL/TLS encryption for Exim, modify the following configuration files.

`/etc/exim4/exim4.conf`:

```ini
# Enable TLS encryption
tls_certificate = /etc/ssl/certs/exim.pem
tls_privatekey = /etc/ssl/private/exim.key
tls_require_ciphers = HIGH
``` 

Make sure the paths to the certificate and private key files are correct.

`/etc/exim4/exim4.conf`:

### Enable secure SMTP:

```ini
# Enable secure SMTP
smtp_accept_max = 100
tls_on_connect_ports = 465
```

#### Virtual Alias Configuration

Exim stores virtual alias mappings in the `/etc/exim4/virtual` file.

```ini
# Virtual alias mappings
admin@example.com    user1
info@example.com     user2
support@example.com  user3
@example.com         catchall
```

After updating the `virtual` file, run the following command to apply the changes:

```shell
sudo exim -bV
```

#### Commands to Manage Exim

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
- **Check Status:**
  ```shell
  sudo systemctl status exim
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

#### Test Email Sending and Receiving

After configuring Exim, test the server by sending and receiving emails.

To send a test email using the `mail` command:

  ```shell
  echo "Test message body" | mail -s "Test Subject" user@example.com
  ```