### Domain Configuration for Postfix Mail Server on Linux

#### Non-SSL Configuration

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

Modify `/etc/postfix/main.cf` to enable TLS:

```ini
# Enable TLS encryption
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.key
smtpd_use_tls = yes
smtpd_tls_security_level = encrypt
``` 

Modify `/etc/postfix/master.cf` to enable secure SMTP:

```ini
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

This domain configuration provides settings for both non-SSL and SSL-based email services using Postfix on Linux. Adjust the paths and settings according to your environment and security requirements.
