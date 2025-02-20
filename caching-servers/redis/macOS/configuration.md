# Redis Caching Server Configuration on macOS

## **Configuration**

### **1. Modify Redis Configuration File**
The Redis configuration file is located at `/usr/local/etc/redis.conf`.

Edit the file using:
```bash
nano /usr/local/etc/redis.conf
```

### **2. Enable Redis as a Cache**
Find and modify these lines:
```ini
maxmemory 256mb
maxmemory-policy allkeys-lru
```
This ensures Redis evicts the least recently used (LRU) keys when it reaches the memory limit.

Save and restart Redis:
```bash
brew services restart redis
```

### **3. Enable Password Authentication (Optional for Security)**
Modify the configuration file:
```ini
requirepass mysecurepassword
```
Restart Redis:
```bash
brew services restart redis
```

## **Troubleshooting**

- **Redis Service Not Starting**:
  ```bash
  brew services restart redis
  ```
- **Connection Issues**:

  ```bash
  netstat -an | grep 6379
  ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting:
  
    ```bash
    redis-cli -a mysecurepassword
    ```