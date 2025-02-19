# MongoDB Database Server Configuration on Ubuntu

## **Configuration**

### **1. Modify MongoDB Configuration File**
Edit the configuration file to allow remote connections:
```bash
sudo nano /etc/mongod.conf
```
Find and modify this line:
```yaml
bindIp: 0.0.0.0
```
Save the file and restart MongoDB:
```bash
sudo systemctl restart mongod
```


## **How to Use MongoDB**

### **1. Connect to MongoDB Shell**
```bash
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

---

## **Backup and Restore MongoDB Database**

### **1. Backup a Database**
```bash
mongodump --db=my_database --out=/backup/
```

### **2. Restore a Database**
```bash
mongorestore --db=my_database /backup/my_database/
```


## **Troubleshooting**

- **MongoDB Service Not Starting**:
  ```bash
  sudo systemctl restart mongod
  ```
- **Connection Refused Error**:
  ```bash
  sudo ufw allow 27017
  ```