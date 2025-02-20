## HAProxy Installation & Usage on Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu 20.04, 22.04, or later
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing HAProxy, update your system:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Install HAProxy**
```bash
sudo apt install -y haproxy
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