# Haproxy Load Balancer Configuration on Windows

## **Configuration**

### **1. Modify HAProxy Configuration File**
The HAProxy configuration file is located at `C:\haproxy\haproxy.cfg`.

Edit the file using Notepad:
```powershell
notepad C:\haproxy\haproxy.cfg
```

### **2. Basic Load Balancing Configuration**
Add the following configuration:
```ini
defaults
    log     global
    mode    http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend http_front
    bind *:80
    default_backend http_back

backend http_back
    balance roundrobin
    server server1 192.168.1.10:80 check
    server server2 192.168.1.11:80 check
```
Save the file and close Notepad.

### **3. Start HAProxy**
Run HAProxy with the configuration file:
```powershell
haproxy.exe -f C:\haproxy\haproxy.cfg
```

### **4. Configure Load Balancing Algorithm (Optional)**
- **Least Connections**:
  ```ini
  balance leastconn
  ```
- **Source IP Hashing**:
  ```ini
  balance source
  ```
Restart HAProxy after making changes:
```powershell
haproxy.exe -f C:\haproxy\haproxy.cfg
```

## **Troubleshooting**

- **HAProxy Service Not Starting**:
  ```powershell
taskkill /F /IM haproxy.exe
haproxy.exe -f C:\haproxy\haproxy.cfg
  ```
- **Check HAProxy Configuration for Errors**:
  ```powershell
haproxy.exe -c -f C:\haproxy\haproxy.cfg
  ```
- **Clients Cannot Connect to HAProxy**:
  - Ensure HAProxy is listening:
    ```powershell
    netstat -ano | findstr :80
    ```
  - Check Windows Firewall rules:
    ```powershell
    netsh advfirewall firewall add rule name="Allow HAProxy" dir=in action=allow protocol=TCP localport=80
    ```