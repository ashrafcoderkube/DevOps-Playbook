# Squid Proxy Server Configuration on macOS

## **Configuration**

### **1. Modify Squid Configuration File**
The Squid configuration file is located at `/usr/local/etc/squid.conf`.

Edit the file using:
```bash
nano /usr/local/etc/squid.conf
```

### **2. Allow Specific IPs to Use Squid Proxy**
Add the following lines:
```ini
acl my_network src 192.168.1.0/24
http_access allow my_network
```

Restart Squid for changes to take effect:
```bash
brew services restart squid
```

### **3. Configure Squid as an Anonymous Proxy**
To hide the client’s IP address, add these lines:
```ini
forwarded_for off
request_header_access Via deny all
request_header_access X-Forwarded-For deny all
request_header_access Referer deny all
```
Restart Squid:
```bash
brew services restart squid
```

## **Troubleshooting**

- **Squid Service Not Starting**:
  ```bash
  brew services restart squid
  ```
- **Clients Cannot Connect to Squid**:
  - Check if Squid is listening:
    ```bash
    netstat -an | grep 3128
    ```
  - Ensure firewall allows Squid traffic:
    ```bash
    sudo pfctl -sr | grep 3128
    ```
- **Test if Squid is Working**:
  ```bash
  curl -I --proxy http://localhost:3128 http://example.com
  ```
