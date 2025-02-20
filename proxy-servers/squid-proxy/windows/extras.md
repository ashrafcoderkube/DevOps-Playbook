## **How to Use Squid Proxy**

### **1. Set Up a Web Browser to Use Squid**
- Open browser settings.
- Find **Proxy Settings** under **Network**.
- Set **HTTP Proxy** to `localhost`.
- Set **Port** to `3128`.
- Save and apply settings.

### **2. Configure a Windows Client to Use Squid**
Set the proxy environment variables in PowerShell:
```powershell
$env:http_proxy="http://localhost:3128"
$env:https_proxy="http://localhost:3128"
```

### **3. Test the Proxy**
Check if traffic is passing through Squid:
```powershell
curl -I --proxy http://localhost:3128 http://example.com
```

### **4. Block Specific Websites (Blacklist Mode)**
Create a blocklist file:
```powershell
echo "www.blockedsite.com" > C:\Squid\etc\blocked_sites.txt
```
Edit `squid.conf` and add:
```ini
acl blocked_sites dstdomain "/etc/blocked_sites.txt"
http_access deny blocked_sites
```
Restart Squid:
```powershell
net stop squid
net start squid
```