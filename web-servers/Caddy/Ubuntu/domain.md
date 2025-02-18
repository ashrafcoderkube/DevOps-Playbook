### Domain Configuration File for Caddy on Ubuntu

#### Non-SSL Configuration

```plaintext
example.com:80 {
    root * /var/www/mywebsite
    file_server
}
```

#### SSL Configuration

```plaintext
example.com {
    root * /var/www/sslsite
    file_server
    tls /etc/ssl/certs/server.crt /etc/ssl/private/server.key
}
```

#### Enabling Proxy Configuration (Optional)

If you want to set up a reverse proxy, you need to update the configuration file:

```plaintext
proxy.example.com {
    reverse_proxy localhost:2015
}
```

This configuration file includes settings for both non-SSL and SSL domains on a Caddy server running on Ubuntu. Adjust the paths and settings as needed for your specific setup.
