# MongoDB Database Server Configuration on Linux

## **Configuration**

### **1. Modify MongoDB Configuration File**
By default, MongoDB listens on `localhost (127.0.0.1)`. To allow remote connections, edit the configuration file:

```bash
sudo nano /etc/mongod.conf
```

Find the following line under `net:` and modify it:

```yaml
bindIp: 0.0.0.0
```

Save the file and restart MongoDB:

```bash
sudo systemctl restart mongod
```

### **2. Create an Admin User**
Log into the MongoDB shell:

```bash
mongosh
```

Switch to the `admin` database and create an admin user:

```javascript
use admin
db.createUser({
  user: "admin",
  pwd: "securepassword",
  roles: [{ role: "root", db: "admin" }]
})
```

Exit the MongoDB shell:

```javascript
exit
```


## **How to Use MongoDB**

### **1. Connect to MongoDB Shell**
```bash
mongosh
```

### **2. Connect to MongoDB Database from Application**
You can connect to MongoDB using different programming languages. Below are examples for Node.js and Python:

#### **Node.js Connection**
Install MongoDB driver:
```bash
npm install mongodb
```

Connect to MongoDB in Node.js:
```javascript
const { MongoClient } = require('mongodb');
const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function connectDB() {
    try {
        await client.connect();
        console.log("Connected to MongoDB");
        const db = client.db("my_database");
    } catch (error) {
        console.error("Connection error:", error);
    } finally {
        await client.close();
    }
}
connectDB();
```

#### **Python Connection**
Install pymongo:
```bash
pip install pymongo
```

Connect to MongoDB in Python:
```python
from pymongo import MongoClient

client = MongoClient("mongodb://localhost:27017/")
db = client["my_database"]
print("Connected to MongoDB")
```

### **3. Create a New Database**
```javascript
use my_database
```

### **4. Create a Collection and Insert Data**
```javascript
db.users.insertOne({ name: "John Doe", email: "john.doe@example.com" })
```

### **5. Retrieve Data**
```javascript
db.users.find().pretty()
```

### **6. List All Databases**
```javascript
show dbs
```

### **7. Create a User for Authentication**
```javascript
use my_database
db.createUser({
  user: "dbuser",
  pwd: "mypassword",
  roles: [{ role: "readWrite", db: "my_database" }]
})
```


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
  sudo journalctl -u mongod --no-pager
  ```
- **Connection Refused Error**:
  - Ensure MongoDB is running with `sudo systemctl status mongod`
  - Check if firewall allows connections on port `27017`
    ```bash
    sudo ufw allow 27017
    ```
- **Authentication Issues**:
  - Ensure the user has proper roles and `authorization: enabled` is set in `mongod.conf`
