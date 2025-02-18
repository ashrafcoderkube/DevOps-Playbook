### Domain Configuration for Exim Mail Server on macOS

## Prerequisites
- A macOS server with administrative (root) privileges.
- A valid domain name (e.g., example.com).
- Exim installed on your system.
- A valid SSL/TLS certificate (for SSL configuration).

#### Non-SSL Configuration
Edit the main Exim configuration file located at `/usr/local/etc/exim/exim.conf`.

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
log_file_path = /usr/local/var/log/exim/mainlog
log_selector = +all
``` 

#### SSL Configuration

To enable SSL/TLS encryption for Exim, modify the following configuration files.

`/usr/local/etc/exim/exim.conf`:

```ini
# Enable TLS encryption
tls_certificate = /usr/local/etc/ssl/certs/exim.pem
tls_privatekey = /usr/local/etc/ssl/private/exim.key
tls_require_ciphers = HIGH
``` 

Make sure the paths to the certificate and private key files are correct.

`/usr/local/etc/exim/exim.conf`:

#### Enable secure SMTP:

```ini
# Enable secure SMTP
smtp_accept_max = 100
tls_on_connect_ports = 465
```

#### Virtual Alias Configuration

Exim stores virtual alias mappings in the `/usr/local/etc/exim/virtual` file.

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
- **Check Status:**
  ```shell
  sudo brew services list | grep exim
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

#### Test Email Sending and Receiving

After configuring Exim, test the server by sending and receiving emails.

To send a test email using the `mail` command:

  ```shell
  echo "Test message body" | mail -s "Test Subject" user@example.com
  ```

  This configuration should help you set up Exim on a macOS environment. Adjust the settings according to your specific requirements and environment.