# **How to Use Memcached**

### **1. Test Connection to Memcached**
```bash
echo stats | nc localhost 11211
```

### **2. Store and Retrieve Data Using Telnet**
```bash
telnet localhost 11211
```
Inside Telnet, run:
```
set mykey 0 900 11
Hello World
STORED
```
Retrieve the stored value:
```
get mykey
```
Expected output:
```
VALUE mykey 0 11
Hello World
END
```

### **3. Store and Retrieve Data Using Python**
```python
import memcache
mc = memcache.Client(['127.0.0.1:11211'], debug=True)
mc.set("greeting", "Hello, Memcached!")
print(mc.get("greeting"))
```

### **4. Store and Retrieve Data Using PHP**
```php
<?php
$mem = new Memcached();
$mem->addServer("127.0.0.1", 11211);
$mem->set("message", "Hello, Memcached!");
echo $mem->get("message");
?>
```

---