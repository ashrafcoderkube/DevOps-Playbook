# Memcached Caching Server Configuration on macOS

## **Configuration**

### **1. Modify Memcached Configuration File**
Memcached does not have a default configuration file on macOS, but you can create one manually:
```bash
nano /usr/local/etc/memcached.conf
```

Add the following configuration:
```ini
-m 256  # Allocates 256MB of memory to Memcached
-l 127.0.0.1  # Listen only on localhost
```
Save and restart Memcached:
```bash
brew services restart memcached
```

### **2. Allow Remote Connections (Optional, for external access)**
To allow connections from other devices, modify the configuration:
```ini
-l 0.0.0.0
```
Save and restart Memcached:
```bash
brew services restart memcached
```

## **Troubleshooting**

- **Memcached Service Not Starting**:
  ```bash
  brew services restart memcached
  ```
- **Connection Issues**:
  ```bash
  netstat -an | grep 11211
  ```
- **Check Memory Usage**:
  ```bash
  echo stats | nc localhost 11211 | grep bytes
  ```