# Squid Proxy Server Configuration on Windows

## **Configuration**

### **1. Modify Squid Configuration File**
To allow remote connections, edit `C:\Squid\etc\squid.conf` and modify:
```ini
http_port 3128
acl all src all
http_access allow all
```
Restart Squid:
```powershell
net stop squid
net start squid
```

### **2. Set Up Squid as an Anonymous Proxy**
To hide the client’s IP address, add these lines to `squid.conf`:
```ini
forwarded_for off
request_header_access Via deny all
request_header_access X-Forwarded-For deny all
request_header_access Referer deny all
```
Restart Squid:
```powershell
net stop squid
net start squid
```

## **Troubleshooting**

- **Squid Service Not Starting**:
  ```powershell
  net start squid
  ```
- **Clients Cannot Connect to Squid**:
  - Check if Squid is listening:
    ```powershell
    netstat -ano | findstr :3128
    ```
  - Ensure Windows Firewall allows Squid traffic:
    ```powershell
    netsh advfirewall firewall add rule name="Allow Squid" dir=in action=allow protocol=TCP localport=3128
    ```
- **Test if Squid is Working**:
  ```powershell
  curl -I --proxy http://localhost:3128 http://example.com
  ```