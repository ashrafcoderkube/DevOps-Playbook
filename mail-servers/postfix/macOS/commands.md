### Postfix Server Commands for macOS

- **Start Postfix:**
  ```shell
  sudo launchctl load -w /Library/LaunchDaemons/org.postfix.master.plist
  ```
- **Stop Postfix:**
  ```shell
  sudo launchctl unload -w /Library/LaunchDaemons/org.postfix.master.plist
  ```
- **Restart Postfix:**
  ```shell
  sudo launchctl unload -w /Library/LaunchDaemons/org.postfix.master.plist
  sudo launchctl load -w /Library/LaunchDaemons/org.postfix.master.plist
  ```
- **Reload Configuration:**
  ```shell
  sudo postfix reload
  ```
- **Check Status:**
  ```shell
  sudo postfix status
  ```
- **Test Configuration:**
  ```shell
  postfix check
  ```
- **Flush Mail Queue:**
  ```shell
  sudo postfix flush
  ```
- **View Mail Queue:**
  ```shell
  mailq
  ```
- **Remove All Emails from Queue:**
  ```shell
  sudo postsuper -d ALL
  ```
- **Remove Deferred Emails from Queue:**
  ```shell
  sudo postsuper -d ALL deferred
  ```
- **Show Active Configuration Parameters:**
  ```shell
  postconf -n
  ```
- **Edit Main Configuration File:**
  ```shell
  sudo nano /etc/postfix/main.cf
  ```
- **Edit Master Configuration File:**
  ```shell
  sudo nano /etc/postfix/master.cf
  ```
- **Restart Postfix After Configuration Change:**
  ```shell
  sudo launchctl unload -w /Library/LaunchDaemons/org.postfix.master.plist
  sudo launchctl load -w /Library/LaunchDaemons/org.postfix.master.plist
  ```
  
