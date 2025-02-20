# Redis Caching Server Configuration on Linux & Ubuntu

## **Configuration**

### **1. Modify Redis Configuration File**
The Redis configuration file is located at `/etc/redis/redis.conf` (Ubuntu/Debian) or `/etc/redis.conf` (CentOS/RHEL).

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
  ```bash
  sudo systemctl restart redis
  sudo journalctl -u redis --no-pager
  ```
- **Connection Issues**:

  ```bash
  sudo netstat -tulnp | grep 6379
  ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting:

    ```bash
    redis-cli -a mysecurepassword
    ```