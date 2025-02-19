## MySQL Database Server Installation & Usage on Linux

### **System Requirements**

- **Operating System**: Linux-based systems (Ubuntu, CentOS, Debian, etc.)
- **Processor**: 1.4 GHz or higher.
- **Memory**: Minimum 1 GB of RAM (2 GB recommended for production environments).
- **Disk Space**: Minimum 2 GB of free disk space (more depending on the size of the databases).
- **Network**: Stable network connection.


## **Installation Steps**

### **1. Install MySQL Database Server**

#### **On Ubuntu/Debian-based Systems**

Run the following commands to install MySQL on Ubuntu or Debian-based systems:

```bash
sudo apt update
sudo apt install mysql-server
```

#### **On CentOS/RHEL-based Systems**

Run the following commands to install MySQL on CentOS or RHEL:

```bash
sudo yum update
sudo yum install mysql-server
```

### **2. Start MySQL Service**
Once MySQL is installed, start the MySQL service using the following command:
```bash
sudo systemctl start mysql
```

### **3. Enable MySQL to Start on Boot**

To ensure MySQL starts automatically on system boot, run the following command:
```bash
sudo systemctl enable mysql
```

### **4. Secure MySQL Installation**

Run the MySQL secure installation script to configure the root password and remove insecure default settings:
```bash
sudo mysql_secure_installation
```