## Varnish Cache Proxy Server Installation & Usage on Linux & Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing Varnish, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install Varnish**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y varnish
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y varnish
```

### **3. Start and Enable Varnish Service**

```bash
sudo systemctl start varnish
sudo systemctl enable varnish
```

### **4. Verify Installation**
Check if Varnish is running:
```bash
sudo systemctl status varnish
```