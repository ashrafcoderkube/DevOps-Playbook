### Domain Configuration File for Nginx on macOS

#### Non-SSL Configuration

```nginx
server {
    listen       80;
    server_name  mywebsite.local;

    root   /usr/local/var/www/mywebsite;
    index  index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page  500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/local/var/www;
    }
}
```

#### SSL Configuration

```nginx
server {
    listen       443 ssl;
    server_name  sslsite.local;

    root   /usr/local/var/www/sslsite;
    index  index.html index.htm;

    ssl_certificate      /usr/local/etc/nginx/ssl/server.crt;
    ssl_certificate_key  /usr/local/etc/nginx/ssl/server.key;

    ssl_session_cache    shared:SSL:1m;
    ssl_session_timeout  5m;

    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page  500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/local/var/www;
    }
}
```

#### Enabling Proxy Configuration (Optional)

If you want to set up a reverse proxy, you need to update the configuration file:

```nginx
server {
    listen       80;
    server_name  proxy.local;

    location / {
        proxy_pass http://backend.local;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

This configuration file includes settings for both non-SSL and SSL domains on an Nginx server running on macOS. Adjust the paths and settings as needed for your specific setup.
