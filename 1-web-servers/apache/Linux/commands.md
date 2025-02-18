### Apache Server Commands for Linux

- **Start Apache:**
  ```shell
  sudo systemctl start apache2  # For Debian/Ubuntu-based distributions
  sudo systemctl start httpd    # For Red Hat/CentOS-based distributions
  ```
- **Stop Apache:**
  ```shell
  sudo systemctl stop apache2  # For Debian/Ubuntu-based distributions
  sudo systemctl stop httpd    # For Red Hat/CentOS-based distributions
  ```
- **Restart Apache:**
  ```shell
  sudo systemctl restart apache2  # For Debian/Ubuntu-based distributions
  sudo systemctl restart httpd    # For Red Hat/CentOS-based distributions
  ```
- **Reload Configuration:**
  ```shell
  sudo systemctl reload apache2  # For Debian/Ubuntu-based distributions
  sudo systemctl reload httpd    # For Red Hat/CentOS-based distributions
  ```
- **Test Configuration:**
  ```shell
  sudo apache2ctl configtest  # For Debian/Ubuntu-based distributions
  sudo httpd -t               # For Red Hat/CentOS-based distributions
  ```
- **Show Version:**
  ```shell
  apache2 -v  # For Debian/Ubuntu-based distributions
  httpd -v    # For Red Hat/CentOS-based distributions
  ```
- **Show Compile Settings:**
  ```shell
  apache2 -V  # For Debian/Ubuntu-based distributions
  httpd -V    # For Red Hat/CentOS-based distributions
  ```
