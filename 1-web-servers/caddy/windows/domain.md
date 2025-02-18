### Domain Configuration File for Caddy on Windows

#### Non-SSL Configuration

```plaintext
example.com:80 {
    root * C:/path/to/your/site
    file_server
}
```

#### SSL Configuration

```plaintext
example.com {
    root * C:/path/to/your/site
    file_server
    tls /path/to/your/certificates/cert.crt /path/to/your/private/key.key
}
```

#### Enabling Proxy Configuration (Optional)

If you want to set up a reverse proxy, you need to update the configuration file:

```plaintext
proxy.example.com {
    reverse_proxy localhost:2015
}
```

This configuration file includes settings for both non-SSL and SSL domains on a Caddy server running on Windows. Adjust the paths and settings as needed for your specific setup.?
