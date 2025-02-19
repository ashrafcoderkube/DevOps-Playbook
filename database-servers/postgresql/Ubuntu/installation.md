## PostgreSQL Database Server Installation & Usage on Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu 20.04, 22.04, or later
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing PostgreSQL, update the system:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Install PostgreSQL**
```bash
sudo apt install postgresql postgresql-contrib -y
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