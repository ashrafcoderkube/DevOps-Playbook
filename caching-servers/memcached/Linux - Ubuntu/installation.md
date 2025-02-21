## Memcached Caching Server Installation & Usage on Linux & Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing Memcached, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install Memcached**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y memcached libmemcached-tools
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y memcached libmemcached
```

### **3. Start and Enable Memcached Service**
```bash
sudo systemctl start memcached
sudo systemctl enable memcached
```

### **4. Verify Installation**
Check if Memcached is running:
```bash
sudo systemctl status memcached
```