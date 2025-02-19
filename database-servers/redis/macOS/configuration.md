# Redis Database Server Configuration on macOS

## **Configuration**

### **1. Modify Redis Configuration File**
The Redis configuration file is located at `/usr/local/etc/redis.conf`.

To allow remote connections, edit the configuration file:
```bash
nano /usr/local/etc/redis.conf
```
Find and modify this line:
```ini
bind 0.0.0.0
```
Save the file and restart Redis:
```bash
brew services restart redis
```

### **2. Enable Authentication (Optional for Security)**
To set a password for Redis, edit the configuration file:
```bash
nano /usr/local/etc/redis.conf
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
brew services restart redis
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
cp /usr/local/var/db/redis/dump.rdb /backup/
```

#### **Restore Redis Database**
```bash
brew services stop redis
cp /backup/dump.rdb /usr/local/var/db/redis/
brew services start redis
```


## **Troubleshooting**

- **Redis Service Not Starting**:
  ```bash
  brew services restart redis
  ```
- **Connection Issues**:
  - Ensure Redis is running with `brew services list`
  - Check if Redis is listening on the correct port:
    ```bash
    netstat -an | grep 6379
    ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting