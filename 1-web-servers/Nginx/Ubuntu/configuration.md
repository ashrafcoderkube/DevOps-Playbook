### Nginx Configuration on Ubuntu

#### Prerequisites
1. Ensure you have administrative privileges on your Ubuntu machine.
2. Install Nginx using the package manager:
   ```shell
   sudo apt update
   sudo apt install nginx
   ```

#### Basic Configuration File (`nginx.conf`)

Here’s a sample of what your `nginx.conf` might look like:

```nginx
# Define the user and worker processes
user  www-data;
worker_processes  auto;

# Error log and process ID
error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;

# Worker settings
events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    # Log settings
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';
    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    keepalive_timeout  65;

    # Server configuration
    server {
        listen       80;
        server_name  localhost;

        # Root and index files
        root   /var/www/html;
        index  index.html index.htm;

        location / {
            try_files $uri $uri/ =404;
        }

        # Error page handling
        error_page  500 502 503 504  /50x.html;
        location = /50x.html {
            root   /var/www/html;
        }
    }
}
```

#### Starting, Stopping, and Restarting Nginx

- **Start Nginx:**
  ```shell
  sudo systemctl start nginx
  ```
- **Stop Nginx:**
  ```shell
  sudo systemctl stop nginx
  ```
- **Restart Nginx:**
  ```shell
  sudo systemctl restart nginx
  ```

#### Virtual Hosts Configuration

To configure a virtual host, you need to update the `nginx.conf` file with the following example:

```nginx
http {
    ...

    server {
        listen       80;
        server_name  mywebsite.local;

        root   /var/www/mywebsite;
        index  index.html index.htm;

        location / {
            try_files $uri $uri/ =404;
        }

        error_page  500 502 503 504  /50x.html;
        location = /50x.html {
            root   /var/www/html;
        }
    }
}
```

#### SSL Configuration

To enable SSL, you need to update the `nginx.conf` file with the following example:

```nginx
http {
    ...

    server {
        listen       443 ssl;
        server_name  sslsite.local;

        root   /var/www/sslsite;
        index  index.html index.htm;

        ssl_certificate      /etc/nginx/ssl/server.crt;
        ssl_certificate_key  /etc/nginx/ssl/server.key;

        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;

        location / {
            try_files $uri $uri/ =404;
        }

        error_page  500 502 503 504  /50x.html;
        location = /50x.html {
            root   /var/www/html;
        }
    }
}
```

This basic configuration should help you set up Nginx on an Ubuntu environment. Adjust the settings as needed for your specific setup.
