## Sendmail Mail Server on Linux & Ubuntu

### System Requirements
- **Linux Distribution:** Ubuntu, CentOS, Debian, RHEL, or other Unix-like OS
- Root or sudo privileges

- **Open ports:** 25 (SMTP), 587 (Submission), 465 (SMTPS, optional)

### Installation

#### Ubuntu/Debian:
  ```shell
sudo apt update
sudo apt install sendmail sendmail-bin
  ```
#### CentOS/RHEL:
  ```shell
sudo yum install sendmail sendmail-cf
  ```
#### Verify Installation:
  ```shell
sendmail -d0.1 -bv root
  ```


### Configuration

#### Editing the Configuration File
The main configuration file for Sendmail is located at:
  ```shell
/etc/mail/sendmail.mc
  ```   
To edit:
  ```shell
sudo nano /etc/mail/sendmail.mc
  ```      
  Make necessary changes, such as defining the relay host or enabling authentication.


#### Defining the Relay Host
To configure a relay host, edit the `sendmail.mc` file:
  ```shell
sudo nano /etc/mail/sendmail.mc
  ```
Add or modify the following line:
  ```
define(`SMART_HOST', `[smtp.your-relay.com]')dnl  
```
Save and exit the file.

#### Enabling Authentication
To enable authentication, add the following lines to `sendmail.mc`:  
  ```
define(`confAUTH_MECHANISMS', `LOGIN PLAIN')dnl
TRUST_AUTH_MECH(`LOGIN PLAIN')dnl
define(`confAUTH_OPTIONS', `A p')dnl
FEATURE(`authinfo', `hash -o /etc/mail/authinfo.db')dnl
  ```

Create the authinfo file:
  ```shell
sudo nano /etc/mail/authinfo
```

Add the following content (replace with actual credentials):  
```
AuthInfo:smtp.your-relay.com "U:root" "I:your-username" "P:your-password"
```

Save and exit the file. Then, create the database:
```shell
sudo makemap hash /etc/mail/authinfo < /etc/mail/authinfo
```


#### Generate sendmail.cf
After editing `sendmail.mc`, generate `sendmail.cf`:
  ```shell
sudo make -C /etc/mail
  ```

#### Restart Sendmail Service
  ```shell
sudo systemctl restart sendmail
sudo systemctl enable sendmail
  ```

### Sending Email
You can send a test email using:
  ```
echo "Test email from Sendmail" | sendmail -v recipient@example.com
  ```
### Checking Logs
To troubleshoot issues, check the logs:
  ```shell
tail -f /var/log/mail.log  # Debian/Ubuntu
tail -f /var/log/maillog   # RHEL/CentOS
  ```


### Uninstalling Sendmail

#### Ubuntu/Debian:
  ```shell
sudo apt remove --purge sendmail sendmail-bin
  ```
#### CentOS/RHEL:
  ```shell
sudo yum remove sendmail sendmail-cf
  ```