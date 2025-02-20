# MongoDB Database Server Configuration on Windows

## **Configuration**

### **1. Modify MongoDB Configuration (Optional)**
MongoDB configuration file is located at:
```
C:\Program Files\MongoDB\Server\6.0\bin\mongod.cfg
```
To allow remote connections, modify:
```yaml
bindIp: 0.0.0.0
```
Restart MongoDB:
```powershell
net stop MongoDB
net start MongoDB
```


## **How to Use MongoDB**

### **1. Connect to MongoDB Shell**
```powershell
mongosh
```

### **2. Create a New Database**
```javascript
use my_database
```

### **3. Insert Data into a Collection**
```javascript
db.users.insertOne({ name: "John Doe", email: "john.doe@example.com" })
```

### **4. Retrieve Data**
```javascript
db.users.find().pretty()
```


## **Backup and Restore MongoDB Database**

### **1. Backup a Database**
```powershell
mongodump --db=my_database --out=C:\backup\
```

### **2. Restore a Database**
```powershell
mongorestore --db=my_database C:\backup\my_database\
```


## **Troubleshooting**

- **MongoDB Service Not Starting**:
  ```powershell
  net start MongoDB
  ```
- **Connection Refused Error**:
  ```powershell
  netstat -ano | findstr :27017
  ```
