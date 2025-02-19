## MongoDB Database Server Installation & Usage on Linux

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection

## **Installation Steps**

### **1. Update System Packages**
Before installing MongoDB, update the system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install MongoDB**
#### **On Ubuntu/Debian-based Systems**
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
sudo apt update
sudo apt install -y mongodb-org
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo tee /etc/yum.repos.d/mongodb-org-6.0.repo <<EOF
[mongodb-org-6.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/6.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-6.0.asc
EOF
sudo yum install -y mongodb-org
```

### **3. Start and Enable MongoDB Service**

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

### **4. Verify Installation**
Check MongoDB service status:

```bash
sudo systemctl status mongod
```
