## MongoDB Database Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space


## **Installation Steps**

### **1. Download MongoDB Installer**
- Visit the [MongoDB Download Center](https://www.mongodb.com/try/download/community).
- Select **Windows**, choose the latest version, and download the MSI installer.

### **2. Install MongoDB**
- Run the downloaded `.msi` file.
- Select **Complete Installation**.
- Ensure **Install MongoDB as a Windows Service** is checked.

### **3. Start MongoDB Service**
MongoDB should start automatically. To manually start it:
```powershell
net start MongoDB
```

To stop MongoDB:
```powershell
net stop MongoDB
```

### **4. Verify Installation**
Open Command Prompt and run:
```powershell
mongosh
```
If the MongoDB shell opens, the installation is successful.