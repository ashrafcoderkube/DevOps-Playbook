### Domain Configuration for Postfix Mail Server on Ubuntu

## Prerequisites
- A Ubuntu server with administrative (root) privileges.
- A valid domain name (e.g., example.com).
- Postfix installed on your system.
- A valid SSL/TLS certificate (for SSL configuration).

#### Non-SSL Configuration

Edit the main Postfix configuration file located at `/etc/postfix/main.cf`.

```ini
# Basic Postfix configuration for mail delivery
myhostname = mail.example.com
mydomain = example.com
myorigin = $mydomain

# Mailbox settings
home_mailbox = Maildir/
mail_spool_directory = /var/mail

# Network settings
inet_interfaces = all
inet_protocols = ipv4

# Relay settings
relayhost = 

# Restrict mail relay
smtpd_recipient_restrictions = \
    permit_mynetworks, \
    reject_unauth_destination

# Logging
maillog_file = /var/log/mail.log
``` 

#### SSL Configuration

To enable SSL/TLS encryption for Postfix, modify the following configuration files.

`/etc/postfix/main.cf`:

```ini
# Enable TLS encryption
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.key
smtpd_use_tls = yes
smtpd_tls_security_level = encrypt
``` 

Make sure the paths to the certificate and private key files are correct.

`/etc/postfix/master.cf`:

```ini
# Enable secure SMTP
smtps     inet  n       -       n       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes

```

#### Virtual Alias Configuration

Create the `/etc/postfix/virtual` file with mappings:

```ini
# Virtual alias mappings
admin@example.com    user1
info@example.com     user2
support@example.com  user3
@example.com        catchall
```

Run the following command to update the virtual alias database:
```shell
sudo postmap /etc/postfix/virtual
```

#### Commands to Manage Postfix

- **Start Postfix:**
  ```shell
  sudo systemctl start postfix
  ```
- **Stop Postfix:**
  ```shell
  sudo systemctl stop postfix
  ```
- **Restart Postfix:**
  ```shell
  sudo systemctl restart postfix
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload postfix
  ```
- **Check Status:**
  ```shell
  sudo systemctl status postfix
  ```

#### Log Files for Debugging

- **View Mail Logs:**
  ```shell
  sudo tail -f /var/log/mail.log
  ```
- **View Authentication Logs:**
  ```shell
  sudo tail -f /var/log/mail.err
  ```

#### Test Email Sending and Receiving

After configuring Postfix, test the server by sending and receiving emails.

To send a test email using the `mail` command:

  ```shell
  echo "Test message body" | mail -s "Test Subject" user@example.com
  ```

This configuration should help you set up Postfix on an Ubuntu environment. Adjust the settings according to your specific requirements and environment.
