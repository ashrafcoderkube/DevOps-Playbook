## MySQL Database Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022.
- **Processor**: 64-bit, 1.4 GHz or higher.
- **Memory**: Minimum 2 GB of RAM (4 GB recommended for production).
- **Disk Space**: Minimum 2 GB of free disk space.

---

## **Installation Steps**

### **1. Download MySQL Installer**
- Go to the [MySQL official website](https://dev.mysql.com/downloads/installer/).
- Download the **MySQL Installer for Windows** (Choose the "Full" or "Custom" setup option based on your needs).

### **2. Run the MySQL Installer**
- Double-click the downloaded `mysql-installer.exe` file.
- Select the **MySQL Server** along with other components if needed (Workbench, Shell, Router).
- Click **Next** and follow the on-screen instructions.

### **3. Configure MySQL Server**
- Select the **Standalone MySQL Server**.
- Choose the **server type**: Development, Server, or Dedicated Computer.
- Set the authentication method (**Use Strong Password Encryption** recommended).
- Create and confirm the **root password**.
- Configure MySQL as a Windows service (recommended).

### **4. Complete the Installation**
- Click **Execute** to install the selected components.
- Once the installation finishes, click **Finish** to exit the installer.