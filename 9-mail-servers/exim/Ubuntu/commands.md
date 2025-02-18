## Exim Server Commands for Ubuntu

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
- **Test Configuration:**
  ```shell
  sudo exim -bV
  ```
- **Flush Mail Queue:**
  ```shell
  sudo exim -qff
  ```
- **View Mail Queue:**
  ```shell
  exim -bp
  ```
- **Remove All Emails from Queue:**
  ```shell
  sudo exim -Mrm <message-id>
  ```
- **Remove Deferred Emails from Queue:**
  ```shell
  sudo exim -Mrm <message-id>
  ```
- **Show Active Configuration Parameters:**
  ```shell
  exim -bP
  ```
- **Edit Main Configuration File:**
  ```shell
  sudo nano /etc/exim/exim.conf
  ```
- **Edit Master Configuration File:**
  ```shell
  sudo nano /etc/exim/exim4.conf.template
  ```
- **Restart exim After Configuration Change:**
  ```shell
  sudo systemctl restart exim
  
