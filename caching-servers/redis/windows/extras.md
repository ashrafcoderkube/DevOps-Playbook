# **How to Use Redis**

### **1. Set and Get Key-Value Pairs**
```powershell
redis-cli SET mykey "Hello, Redis!"
redis-cli GET mykey
```

### **2. Work with Lists**
```powershell
redis-cli LPUSH mylist "item1"
redis-cli LPUSH mylist "item2"
redis-cli LRANGE mylist 0 -1
```

### **3. Work with Hashes**
```powershell
redis-cli HSET user:1000 name "John Doe" email "john@example.com"
redis-cli HGETALL user:1000
```

### **4. Work with Sets**
```powershell
redis-cli SADD myset "apple"
redis-cli SADD myset "banana"
redis-cli SMEMBERS myset
```

### **5. Work with Sorted Sets**
```powershell
redis-cli ZADD leaderboard 100 "player1"
redis-cli ZADD leaderboard 200 "player2"
redis-cli ZRANGE leaderboard 0 -1 WITHSCORES
```

### **6. Backup and Restore Redis Data**

#### **Backup Redis Database (Memurai)**
```powershell
copy C:\ProgramData\Memurai\dump.rdb C:\backup\
```

#### **Restore Redis Database**
```powershell
copy C:\backup\dump.rdb C:\ProgramData\Memurai\
net stop memurai
net start memurai
```