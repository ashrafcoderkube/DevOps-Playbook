## Sendmail Mail Server on macOS

### System Requirements

- **macOS** (any recent version with UNIX compatibility)
- Root or sudo privileges

- **Open ports**: 25 (SMTP), 587 (Submission), 465 (SMTPS, optional)

### Installation

Sendmail is pre-installed on macOS. To ensure it is active, run:

```sh
sudo launchctl load -w /System/Library/LaunchDaemons/org.postfix.master.plist
```

### Verify Installation:

```sh
sendmail -d0.1 -bv root
```

### Configuration

#### Defining the Relay Host

To configure a relay host, edit the configuration file:

```sh
sudo nano /System/Library/LaunchDaemons/org.postfix.master.plist
```

Add or modify the following line:

```sh
define(`SMART_HOST', `[smtp.your-relay.com]')dnl
```

Save and exit the file.

#### Enabling Authentication

To enable authentication, create or edit the authentication file:

```sh
sudo nano /etc/postfix/sasl_passwd
```

Add the following content (replace with actual credentials):

```
AuthInfo:smtp.your-relay.com "U:root" "I:your-username" "P:your-password"
```

Save and exit the file. Then, create the database:

```sh
sudo postmap /etc/postfix/sasl_passwd
sudo chmod 600 /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db
```

### Restart Sendmail Service

```sh
sudo launchctl stop org.postfix.master
sudo launchctl start org.postfix.master
```

### Sending Email

You can send a test email using:

```sh
echo "Test email from Sendmail" | mail -s "Test Subject" recipient@example.com
```

### Checking Logs

To troubleshoot issues, check the logs:

```sh
tail -f /var/log/mail.log
```

### Uninstalling Sendmail

Sendmail is a built-in component of macOS and cannot be fully removed. However, you can disable it with:

```sh
sudo launchctl unload -w /System/Library/LaunchDaemons/org.postfix.master.plist
```
