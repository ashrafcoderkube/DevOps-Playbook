### Postfix Server Commands for Windows

#### Install Cygwin:
  - Visit the Cygwin website.
  - Download the setup executable and install Cygwin.
  - During the installation, make sure to select the Postfix package.

- **Start Postfix:**
  ```shell
  cygrunsrv -S postfix
  ```
- **Stop Postfix:**
  ```shell
  cygrunsrv -E postfix
  ```
- **Restart Postfix:**
  ```shell
  cygrunsrv -R postfix
  ```
- **Reload Configuration:**
  ```shell
  postfix reload
  ```
- **Check Status:**
  ```shell
  cygrunsrv -Q postfix
  ```
- **Test Configuration:**
  ```shell
  postfix check
  ```
- **Flush Mail Queue:**
  ```shell
  postfix flush
  ```
- **View Mail Queue:**
  ```shell
  mailq
  ```
- **Remove All Emails from Queue:**
  ```shell
  postsuper -d ALL
  ```
- **Remove Deferred Emails from Queue:**
  ```shell
  postsuper -d ALL deferred
  ```
- **Show Active Configuration Parameters:**
  ```shell
  postconf -n
  ```
- **Edit Main Configuration File:**
  ```shell
  nano /etc/postfix/main.cf
  ```
- **Edit Master Configuration File:**
  ```shell
  nano /etc/postfix/master.cf
  ```
- **Restart Postfix After Configuration Change:**
  ```shell
  cygrunsrv -R postfix
  ```
  
