# Nginx Load Balancer Installation & Usage on Linux

## **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing Nginx, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install Nginx**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y nginx
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y nginx
```

### **3. Start and Enable Nginx Service**
```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### **4. Verify Installation**
Check if Nginx is running:
```bash
sudo systemctl status nginx
```