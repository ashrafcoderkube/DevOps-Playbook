## Redis Database Server Installation & Usage on Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu 20.04, 22.04, or later
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing Redis, update the system:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Install Redis**
```bash
sudo apt install -y redis-server
```

### **3. Start and Enable Redis Service**

```bash
sudo systemctl start redis
sudo systemctl enable redis
```

### **4. Verify Installation**
Check Redis service status:

```bash
sudo systemctl status redis
```

To check if Redis is working properly, run:
```bash
redis-cli ping
```
If Redis is running correctly, it should return:
```
PONG
```