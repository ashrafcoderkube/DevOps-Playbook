## PostgreSQL Database Server Installation & Usage on Linux

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing PostgreSQL, update the system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install PostgreSQL**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install postgresql postgresql-contrib -y
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install postgresql-server postgresql-contrib -y
```

### **3. Start and Enable PostgreSQL Service**

```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

### **4. Verify Installation**
Check PostgreSQL service status:

```bash
sudo systemctl status postgresql
```
