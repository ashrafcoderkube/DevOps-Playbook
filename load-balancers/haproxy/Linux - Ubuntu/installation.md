## HAProxy Load Balancer Installation & Usage on Linux

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing HAProxy, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install HAProxy**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y haproxy
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y haproxy
```

### **3. Start and Enable HAProxy Service**
```bash
sudo systemctl start haproxy
sudo systemctl enable haproxy
```

### **4. Verify Installation**
Check if HAProxy is running:
```bash
sudo systemctl status haproxy
```