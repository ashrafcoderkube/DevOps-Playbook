# **How to Use Squid Proxy**

### **1. Set Up a Web Browser to Use Squid**
- Open browser settings.
- Find **Proxy Settings** under **Network**.
- Set **HTTP Proxy** to `localhost`.
- Set **Port** to `3128`.
- Save and apply settings.

### **2. Configure a macOS Client to Use Squid**
Set the proxy environment variables:
```bash
export http_proxy="http://localhost:3128"
export https_proxy="http://localhost:3128"
```

### **3. Test the Proxy**
Check if traffic is passing through Squid:
```bash
curl -I --proxy http://localhost:3128 http://example.com
```

### **4. Block Specific Websites (Blacklist Mode)**
Create a blocklist file:
```bash
echo "www.blockedsite.com" | sudo tee /usr/local/etc/squid/blocked_sites.txt
```
Edit `/usr/local/etc/squid.conf` and add:
```ini
acl blocked_sites dstdomain "/usr/local/etc/squid/blocked_sites.txt"
http_access deny blocked_sites
```
Restart Squid:
```bash
brew services restart squid
```
