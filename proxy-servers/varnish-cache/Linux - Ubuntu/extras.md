# **How to Use Varnish**

### **1. Test if Varnish is Working**
Run the following command:
```bash
curl -I http://localhost
```
Check the response headers for `X-Varnish`, which confirms Varnish is caching responses.

### **2. Clear the Cache (Purge Requests)**
To purge cached content for a specific URL:
```bash
curl -X PURGE http://localhost/somepage.html
```

### **3. Set Cache TTL (Time-to-Live)**
Modify `/etc/varnish/default.vcl` to control cache duration:
```vcl
sub vcl_backend_response {
    set beresp.ttl = 1h;
}
```
Restart Varnish for changes to take effect:
```bash
sudo systemctl restart varnish
```

### **4. Monitor Varnish Cache Performance**
Check real-time cache hits and misses:
```bash
varnishstat
```