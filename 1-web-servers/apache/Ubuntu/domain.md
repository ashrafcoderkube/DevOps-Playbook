### Domain Configuration File for Apache on Ubuntu

#### Non-SSL Configuration

```apache
<VirtualHost *:80>
    DocumentRoot "/var/www/html/mywebsite"
    ServerName mywebsite.local

    <Directory "/var/www/html/mywebsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/mywebsite-error.log
    CustomLog ${APACHE_LOG_DIR}/mywebsite-access.log combined
</VirtualHost>
```

#### SSL Configuration

```apache
<VirtualHost _default_:443>
    DocumentRoot "/var/www/html/sslsite"
    ServerName sslsite.local:443

    <Directory "/var/www/html/sslsite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/sslsite-error.log
    CustomLog ${APACHE_LOG_DIR}/sslsite-access.log combined

    SSLEngine on
    SSLCertificateFile "/etc/ssl/certs/server.crt"
    SSLCertificateKeyFile "/etc/ssl/private/server.key"
</VirtualHost>
```

#### Enabling Proxy Configuration (Optional)

If you want to set up a reverse proxy, you need to enable the necessary modules and update the configuration file:

1. **Enable Proxy Modules:**
    Add the following lines to your `apache2.conf` file:
    ```apache
    LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
    LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
    ```

2. **Configure Proxy:**
    ```apache
    <VirtualHost *:80>
        ServerName proxy.local
        ProxyRequests Off
        ProxyPass / http://backend.local/
        ProxyPassReverse / http://backend.local/
    </VirtualHost>
    ```

This configuration file includes settings for both non-SSL and SSL domains on an Apache server running on Ubuntu. Adjust the paths and settings as needed for your specific setup.
