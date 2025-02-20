# Redis Database Server Configuration on Linux

## **Configuration**

### **1. Modify Redis Configuration File**
The Redis configuration file is located at `/etc/redis/redis.conf` (Ubuntu/Debian) or `/etc/redis.conf` (CentOS/RHEL).

To allow remote connections, edit the configuration file:
```bash
sudo nano /etc/redis/redis.conf
```
Find and modify this line:
```ini
bind 0.0.0.0
```
Save the file and restart Redis:
```bash
sudo systemctl restart redis
```

### **2. Enable Authentication (Optional for Security)**
To set a password for Redis, edit the configuration file:
```bash
sudo nano /etc/redis/redis.conf
```
Find the line:
```ini
# requirepass foobared
```
Uncomment it and change it to:
```ini
requirepass mysecurepassword
```
Restart Redis:
```bash
sudo systemctl restart redis
```


## **Connecting to Redis**

### **1. Connect to Redis Locally**
To access the Redis CLI:
```bash
redis-cli
```

If authentication is enabled:
```bash
redis-cli -a mysecurepassword
```

### **2. Connect to Redis Remotely**
If Redis is running on a remote server, connect using:
```bash
redis-cli -h <server-ip> -p 6379 -a mysecurepassword
```



## **How to Use Redis**

### **1. Set and Get Key-Value Pairs**
```bash
SET mykey "Hello, Redis!"
GET mykey
```

### **2. Work with Lists**
```bash
LPUSH mylist "item1"
LPUSH mylist "item2"
LRANGE mylist 0 -1
```

### **3. Work with Hashes**
```bash
HSET user:1000 name "John Doe" email "john@example.com"
HGETALL user:1000
```

### **4. Work with Sets**
```bash
SADD myset "apple"
SADD myset "banana"
SMEMBERS myset
```

### **5. Work with Sorted Sets**
```bash
ZADD leaderboard 100 "player1"
ZADD leaderboard 200 "player2"
ZRANGE leaderboard 0 -1 WITHSCORES
```

### **6. Backup and Restore Redis Data**

#### **Backup Redis Database**
```bash
sudo cp /var/lib/redis/dump.rdb /backup/
```

#### **Restore Redis Database**
```bash
sudo systemctl stop redis
sudo cp /backup/dump.rdb /var/lib/redis/
sudo systemctl start redis
```



## **Troubleshooting**

- **Redis Service Not Starting**:
  ```bash
  sudo systemctl restart redis
  sudo journalctl -u redis --no-pager
  ```
- **Connection Issues**:
  - Ensure Redis is running with `sudo systemctl status redis`
  - Check if Redis is listening on the correct port:
    ```bash
    sudo netstat -tulnp | grep redis
    ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting