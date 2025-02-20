# Memcached Caching Server Configuration on Linux & Ubuntu

## **Configuration**

### **1. Modify Memcached Configuration File**
The Memcached configuration file is located at `/etc/memcached.conf` (Ubuntu/Debian) or `/etc/sysconfig/memcached` (CentOS/RHEL).

Edit the file using:
```bash
sudo nano /etc/memcached.conf
```

### **2. Adjust Memory Allocation**
Find the following line and modify the value as needed:
```ini
-m 256  # Allocates 256MB of memory to Memcached
```
Save and restart Memcached:
```bash
sudo systemctl restart memcached
```

### **3. Allow Remote Connections (Optional, for external access)**
Find this line:
```ini
-l 127.0.0.1
```
Change it to:
```ini
-l 0.0.0.0
```
Save and restart Memcached:
```bash
sudo systemctl restart memcached
```

## **Troubleshooting**

- **Memcached Service Not Starting**:
  ```bash
  sudo systemctl restart memcached
  sudo journalctl -u memcached --no-pager
  ```
- **Connection Issues**:
  ```bash
  sudo netstat -tulnp | grep 11211
  ```
- **Check Memory Usage**:

  ```bash
  echo stats | nc localhost 11211 | grep bytes
  ```