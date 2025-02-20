### Postfix Server Commands for Linux

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
  sudo systemctl restart postfix
  ```
