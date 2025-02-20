# Redis Caching Server Configuration on Windows

## **Configuration**

### **1. Modify Redis Configuration File**
If using WSL, the Redis configuration file is located at `/etc/redis/redis.conf`. If using Memurai, modify `memurai.conf`.

Edit the file using:
```bash
sudo nano /etc/redis/redis.conf
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
sudo systemctl restart redis
```

### **3. Enable Password Authentication (Optional for Security)**
Modify the configuration file:
```ini
requirepass mysecurepassword
```
Restart Redis:
```bash
sudo systemctl restart redis
```

## **Troubleshooting**

- **Redis Service Not Starting**:
  ```powershell
  net start memurai
  ```
- **Connection Issues**:

  ```powershell
  netstat -ano | findstr :6379
  ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting:

    ```powershell
    redis-cli -a mysecurepassword
    ```