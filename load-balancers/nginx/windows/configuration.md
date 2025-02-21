# Nginx Load Balancer Configuration on Windows

## **Configuration**

### **1. Modify Nginx Configuration File**
The main Nginx configuration file is located at `C:\nginx\conf\nginx.conf`.

Edit the file using Notepad or any text editor:
```powershell
notepad C:\nginx\conf\nginx.conf
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
```powershell
taskkill /F /IM nginx.exe
start nginx
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
```powershell
taskkill /F /IM nginx.exe
start nginx
```

## **Troubleshooting**

- **Nginx Service Not Starting**:
  ```powershell
taskkill /F /IM nginx.exe
start nginx
  ```
- **Check Nginx Configuration for Errors**:
  ```powershell
ginx -t
  ```
- **Clients Cannot Connect to Nginx**:
  - Ensure Nginx is listening:
    ```powershell
    netstat -ano | findstr :80
    ```
  - Check Windows Firewall rules:
    ```powershell
    netsh advfirewall firewall add rule name="Allow Nginx" dir=in action=allow protocol=TCP localport=80
    ```