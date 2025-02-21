# Nginx Load Balancer Configuration on Linux & Ubuntu

## **Configuration**

### **1. Modify Nginx Configuration File**
The main Nginx configuration file is located at `/etc/nginx/nginx.conf`.

Edit the file using:
```bash
sudo nano /etc/nginx/nginx.conf
```

### **2. Configure Nginx as a Load Balancer**
Add the following configuration inside the `http` block:
```nginx
upstream backend_servers {
    server 192.168.1.10:80;
    server 192.168.1.11:80;
    server 192.168.1.12:80;
}

server {
    listen 80;
    location / {
        proxy_pass http://backend_servers;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```
Save and restart Nginx:
```bash
sudo systemctl restart nginx
```

### **3. Configure Load Balancing Algorithm (Optional)**
By default, Nginx uses round-robin load balancing. You can specify different algorithms:
- **Least Connections**:
  ```nginx
  upstream backend_servers {
      least_conn;
      server 192.168.1.10:80;
      server 192.168.1.11:80;
  }
  ```
- **IP Hashing (Clients always hit the same backend server)**:
  ```nginx
  upstream backend_servers {
      ip_hash;
      server 192.168.1.10:80;
      server 192.168.1.11:80;
  }
  ```
Restart Nginx after making changes:
```bash
sudo systemctl restart nginx
```

## **Troubleshooting**

- **Nginx Service Not Starting**:
  ```bash
  sudo systemctl restart nginx
  sudo journalctl -u nginx --no-pager
  ```
- **Check Nginx Configuration for Errors**:

  ```bash
  sudo nginx -t
  ```
- **Clients Cannot Connect to Nginx**:
  - Ensure Nginx is listening:
    ```bash
    sudo netstat -tulnp | grep nginx
    ```
  - Check firewall rules:
    ```bash
    sudo ufw allow 80/tcp
    ```