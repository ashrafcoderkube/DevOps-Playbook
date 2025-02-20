# **How to Use Squid Proxy**

### **1. Set Up a Web Browser to Use Squid**
- Open browser settings.
- Find **Proxy Settings** under **Network**.
- Set **HTTP Proxy** to `192.168.1.1` (replace with your Squid server IP).
- Set **Port** to `3128` (default Squid port).
- Save and apply settings.

### **2. Configure a Linux Client to Use Squid**
Set the proxy environment variables:
```bash
export http_proxy="http://192.168.1.1:3128"
export https_proxy="http://192.168.1.1:3128"
```

### **3. Test the Proxy**
Check if traffic is passing through Squid:
```bash
curl -I --proxy http://192.168.1.1:3128 http://example.com
```

### **4. Allow Specific Websites Only (Whitelist Mode)**
Edit `/etc/squid/squid.conf` and add:
```ini
acl allowed_sites dstdomain .example.com .testsite.com
http_access allow allowed_sites
http_access deny all
```
Restart Squid:
```bash
sudo systemctl restart squid
```

### **5. Block Specific Websites (Blacklist Mode)**
Create a blocklist file:
```bash
echo "www.blockedsite.com" | sudo tee /etc/squid/blocked_sites.txt
```
Edit `/etc/squid/squid.conf` and add:
```ini
acl blocked_sites dstdomain "/etc/squid/blocked_sites.txt"
http_access deny blocked_sites
```
Restart Squid:
```bash
sudo systemctl restart squid
```
