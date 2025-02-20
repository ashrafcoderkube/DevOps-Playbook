# Redis Database Server Configuration on Windows

## **Configuration**

### **1. Modify Redis Configuration File**
The Redis configuration file is located at:
```
C:\Program Files\Redis\redis.windows.conf
```
To allow remote connections, modify:
```ini
bind 0.0.0.0
```
Restart Redis:
```powershell
net stop Redis
net start Redis
```

### **2. Enable Authentication (Optional for Security)**
To set a password for Redis, edit the configuration file:
```ini
requirepass mysecurepassword
```
Restart Redis:
```powershell
net stop Redis
net start Redis
```

## **Connecting to Redis**

### **1. Connect to Redis Locally**
To access the Redis CLI:
```powershell
redis-cli
```

If authentication is enabled:
```powershell
redis-cli -a mysecurepassword
```

### **2. Connect to Redis Remotely**
If Redis is running on a remote Windows server, connect using:
```powershell
redis-cli -h <server-ip> -p 6379 -a mysecurepassword
```


## **How to Use Redis**

### **1. Set and Get Key-Value Pairs**
```powershell
SET mykey "Hello, Redis!"
GET mykey
```

### **2. Work with Lists**
```powershell
LPUSH mylist "item1"
LPUSH mylist "item2"
LRANGE mylist 0 -1
```

### **3. Work with Hashes**
```powershell
HSET user:1000 name "John Doe" email "john@example.com"
HGETALL user:1000
```

### **4. Work with Sets**
```powershell
SADD myset "apple"
SADD myset "banana"
SMEMBERS myset
```

### **5. Work with Sorted Sets**
```powershell
ZADD leaderboard 100 "player1"
ZADD leaderboard 200 "player2"
ZRANGE leaderboard 0 -1 WITHSCORES
```

### **6. Backup and Restore Redis Data**

#### **Backup Redis Database**
```powershell
copy C:\ProgramData\Redis\dump.rdb C:\backup\
```

#### **Restore Redis Database**
```powershell
net stop Redis
copy C:\backup\dump.rdb C:\ProgramData\Redis\
net start Redis
```

## **Troubleshooting**

- **Redis Service Not Starting**:
  ```powershell
  net start Redis
  ```
- **Connection Issues**:
  ```powershell
  netstat -ano | findstr :6379
  ```
- **Authentication Issues**:
  - Ensure the correct password is used when connecting