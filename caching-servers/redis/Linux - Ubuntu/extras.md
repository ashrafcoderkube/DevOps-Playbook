# **How to Use Redis**

### **1. Set and Get Key-Value Pairs**
```bash
redis-cli SET mykey "Hello, Redis!"
redis-cli GET mykey
```

### **2. Work with Lists**
```bash
redis-cli LPUSH mylist "item1"
redis-cli LPUSH mylist "item2"
redis-cli LRANGE mylist 0 -1
```

### **3. Work with Hashes**
```bash
redis-cli HSET user:1000 name "John Doe" email "john@example.com"
redis-cli HGETALL user:1000
```

### **4. Work with Sets**
```bash
redis-cli SADD myset "apple"
redis-cli SADD myset "banana"
redis-cli SMEMBERS myset
```

### **5. Work with Sorted Sets**
```bash
redis-cli ZADD leaderboard 100 "player1"
redis-cli ZADD leaderboard 200 "player2"
redis-cli ZRANGE leaderboard 0 -1 WITHSCORES
```

### **6. Backup and Restore Redis Data**

#### **Backup Redis Database**
```bash
cp /var/lib/redis/dump.rdb /backup/
```

#### **Restore Redis Database**
```bash
sudo systemctl stop redis
cp /backup/dump.rdb /var/lib/redis/
sudo systemctl start redis
```
