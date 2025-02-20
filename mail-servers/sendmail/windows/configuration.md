## Sendmail Mail Server on Windows

### System Requirements

- **Windows** 10/11 or Windows Server
- Administrator privileges
- **Open ports:** 25 (SMTP), 587 (Submission), 465 (SMTPS, optional)

### Installation

1. Download a Windows-compatible version of Sendmail, such as **Fake Sendmail** (a commonly used lightweight alternative).

2. Extract the downloaded package to `C:\sendmail`.
3. Open the `sendmail.ini` file located in `C:\sendmail` and configure the SMTP settings.

### Verify Installation:

To verify that Sendmail is correctly installed, open Command Prompt and run:

```cmd
sendmail -v
```

### Configuration

### Defining the Relay Host

Edit the `sendmail.ini` configuration file:

```ini
smtp_server=smtp.your-relay.com
smtp_port=587
```

Save and exit the file.

### Enabling Authentication

To enable authentication, modify `sendmail.ini`:

```ini
auth_username=your-username
auth_password=your-password
```

Save and restart Sendmail.

### Restart Sendmail Service

If using a Windows service wrapper, restart Sendmail using:

```cmd
net stop sendmail
net start sendmail
```

### Sending Email

To send a test email, create a text file `email.txt`:

```
To: recipient@example.com
From: sender@example.com
Subject: Test Email

This is a test email from Sendmail on Windows.
```

Then send it using:

```cmd
sendmail -t < email.txt
```

### Checking Logs

To troubleshoot issues, check the Sendmail log file:

```cmd
type C:\sendmail\sendmail.log
```

## Uninstalling Sendmail

To remove Sendmail from Windows, delete the `C:\sendmail` directory and remove any related services.

