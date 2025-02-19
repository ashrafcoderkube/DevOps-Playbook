# Elasticsearch Database Server Configuration on Windows

## **Configuration**

### **1. Modify Elasticsearch Configuration File**
Edit the configuration file `elasticsearch.yml` located in:
```
C:\Elasticsearch\config\elasticsearch.yml
```
To allow remote connections, modify this line:
```yaml
network.host: 0.0.0.0
```
Save the file and restart Elasticsearch.

### **2. Secure Elasticsearch with Authentication (Optional)**
Enable security features by adding this line to `elasticsearch.yml`:
```yaml
xpack.security.enabled: true
```
Restart Elasticsearch and set up a password:
```powershell
C:\Elasticsearch\bin\elasticsearch-setup-passwords interactive
```


## **Connecting to Elasticsearch**

### **1. Connect Locally**
Use `curl` to interact with Elasticsearch:
```powershell
curl -X GET "http://localhost:9200/"
```

### **2. Connect Remotely**
If Elasticsearch is running on a remote server, connect using:
```powershell
curl -X GET "http://<server-ip>:9200/"
```

### **3. Authenticate (If Security is Enabled)**
```powershell
curl -u elastic:yourpassword -X GET "http://localhost:9200/_cluster/health"
```


## **How to Use Elasticsearch**

### **1. Create an Index**
```powershell
curl -X PUT "http://localhost:9200/my_index"
```

### **2. Insert Data into an Index**
```powershell
curl -X POST "http://localhost:9200/my_index/_doc/1" -H "Content-Type: application/json" -d '{ "name": "John Doe", "age": 30, "city": "New York" }'
```

### **3. Retrieve Data from an Index**
```powershell
curl -X GET "http://localhost:9200/my_index/_doc/1"
```

### **4. Search Data**
```powershell
curl -X GET "http://localhost:9200/my_index/_search?q=name:John"
```

### **5. Delete an Index**
```powershell
curl -X DELETE "http://localhost:9200/my_index"
```


## **Backup and Restore Elasticsearch Data**

### **1. Backup an Index**
```powershell
curl -X PUT "http://localhost:9200/_snapshot/my_backup" -H "Content-Type: application/json" -d '{ "type": "fs", "settings": { "location": "C:/backups/elasticsearch/", "compress": true } }'
```

### **2. Restore an Index**
```powershell
curl -X POST "http://localhost:9200/_snapshot/my_backup/my_index/_restore"
```


## **Troubleshooting**

- **Elasticsearch Service Not Starting**:
  ```powershell
  C:\Elasticsearch\bin\elasticsearch.bat
  ```
- **Connection Issues**:
  ```powershell
  netstat -ano | findstr :9200
  ```
- **Authentication Issues**:
  ```powershell
  curl -u elastic:yourpassword -X GET "http://localhost:9200/_security/_authenticate"
  ```