## MySQL Database Server Installation & Usage on Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu 20.04, 22.04, or later
- **Processor**: 1.4 GHz or higher
- **Memory**: Minimum 1 GB of RAM (2 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection for installation


## **Installation Steps**

### **1. Update System Packages**
Before installing MySQL, update the system packages:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Install MySQL Server**
Run the following command to install MySQL on Ubuntu:

```bash
sudo apt install mysql-server -y
```

### **3. Start and Enable MySQL Service**
After installation, start MySQL and enable it to launch on system boot:

```bash
sudo systemctl start mysql
sudo systemctl enable mysql
```

### **4. Secure MySQL Installation**
To improve security, run the following command and follow the on-screen prompts:

```bash
sudo mysql_secure_installation
```

- Set a root password
- Remove anonymous users
- Disable remote root login
- Remove test database
- Reload privilege tables

