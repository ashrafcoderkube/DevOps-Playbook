### Exim Server Commands for macOS

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
  sudo nano /usr/local/etc/exim/exim.conf
  ```
- **Edit Master Configuration File:**
  ```shell
  sudo nano /usr/local/etc/exim/exim4.conf.template
  ```
- **Restart exim After Configuration Change:**
  ```shell
  sudo brew services restart exim
  ```
  
