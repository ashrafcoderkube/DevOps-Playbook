# Elasticsearch Database Server Configuration on Linux

## **Configuration**

### **1. Modify Elasticsearch Configuration File**
The Elasticsearch configuration file is located at `/etc/elasticsearch/elasticsearch.yml`.

To allow remote connections, edit the configuration file:
```bash
sudo nano /etc/elasticsearch/elasticsearch.yml
```
Find and modify this line:
```yaml
network.host: 0.0.0.0
```
Save the file and restart Elasticsearch:
```bash
sudo systemctl restart elasticsearch
```

### **2. Secure Elasticsearch with Authentication (Optional)**
Elasticsearch security features require user authentication. Enable security by modifying:
```yaml
xpack.security.enabled: true
```
Restart Elasticsearch and set up a password:
```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
```

## **Connecting to Elasticsearch**

### **1. Connect Locally**
Use `curl` to interact with Elasticsearch:
```bash
curl -X GET "http://localhost:9200/"
```

### **2. Connect Remotely**
If Elasticsearch is on a remote server, use:
```bash
curl -X GET "http://<server-ip>:9200/"
```

### **3. Authenticate (If Security is Enabled)**
```bash
curl -u elastic:yourpassword -X GET "http://localhost:9200/_cluster/health"
```


## **How to Use Elasticsearch**

### **1. Create an Index**
```bash
curl -X PUT "http://localhost:9200/my_index"
```

### **2. Insert Data into an Index**
```bash
curl -X POST "http://localhost:9200/my_index/_doc/1" -H "Content-Type: application/json" -d '{ "name": "John Doe", "age": 30, "city": "New York" }'
```

### **3. Retrieve Data from an Index**
```bash
curl -X GET "http://localhost:9200/my_index/_doc/1"
```

### **4. Search Data**
```bash
curl -X GET "http://localhost:9200/my_index/_search?q=name:John"
```

### **5. Delete an Index**
```bash
curl -X DELETE "http://localhost:9200/my_index"
```


## **Backup and Restore Elasticsearch Data**

### **1. Backup an Index**
```bash
curl -X PUT "http://localhost:9200/_snapshot/my_backup" -H "Content-Type: application/json" -d '{ "type": "fs", "settings": { "location": "/var/backups/elasticsearch/", "compress": true } }'
```

### **2. Restore an Index**
```bash
curl -X POST "http://localhost:9200/_snapshot/my_backup/my_index/_restore"
```


## **Troubleshooting**

- **Elasticsearch Service Not Starting**:
  ```bash
  sudo systemctl restart elasticsearch
  sudo journalctl -u elasticsearch --no-pager
  ```
- **Connection Issues**:
  ```bash
  sudo netstat -tulnp | grep 9200
  ```
- **Authentication Issues**:

  ```bash
  curl -u elastic:yourpassword -X GET "http://localhost:9200/_security/_authenticate"
  ```
