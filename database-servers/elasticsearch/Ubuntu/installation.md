## Elasticsearch Database Server Installation & Usage on Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu 20.04, 22.04, or later
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 10 GB of free disk space
- **Network**: Stable internet connection



## **Installation Steps**

### **1. Update System Packages**
Before installing Elasticsearch, update the system:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Install Java (Required for Elasticsearch)**
Elasticsearch requires Java to run. Install OpenJDK with:

```bash
sudo apt install -y openjdk-11-jdk
```

Verify Java installation:
```bash
java -version
```

### **3. Install Elasticsearch**
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
sudo apt update
sudo apt install -y elasticsearch
```

### **4. Start and Enable Elasticsearch Service**
```bash
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
```

### **5. Verify Installation**
Check if Elasticsearch is running:
```bash
curl -X GET "http://localhost:9200/"
```
If Elasticsearch is working correctly, it should return JSON output with cluster details.