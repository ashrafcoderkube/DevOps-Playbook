## Redis Caching Server Installation & Usage on Linux

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection

---

## **Installation Steps**

### **1. Update System Packages**
Before installing Redis, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install Redis**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y redis-server
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y redis
```

### **3. Start and Enable Redis Service**
```bash
sudo systemctl start redis
sudo systemctl enable redis
```

### **4. Verify Installation**
Check if Redis is running:
```bash
redis-cli ping
```
If Redis is working correctly, it should return:
```
PONG
```

