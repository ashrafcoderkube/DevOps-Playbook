### IIS (Internet Information Services) Commands for Windows

- **Start IIS:**
  ```shell
  iisreset /start
  ```
- **Stop IIS:**
  ```shell
  iisreset /stop
  ```
- **Restart IIS:**
  ```shell
  iisreset /restart
  ```
- **Reload Configuration:**
  ```shell
  iisreset
  ```
- **Recycle Application Pool:**
  ```shell
  appcmd recycle apppool /apppool.name:YourAppPoolName
  ```
- **Show IIS Version:**
  ```shell
  reg query HKLM\Software\Microsoft\InetStp /v VersionString
  ```
