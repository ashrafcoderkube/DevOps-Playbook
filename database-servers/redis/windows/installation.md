## Redis Database Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space


## **Installation Steps**

### **1. Download Redis for Windows**
Redis is not officially supported on Windows, but a maintained version is available. Download the latest Redis MSI installer from:

[https://github.com/microsoftarchive/redis/releases](https://github.com/microsoftarchive/redis/releases)

### **2. Install Redis**
- Run the downloaded `.msi` file.
- Follow the installation wizard and select the default options.
- Set Redis to run as a Windows service during installation.

### **3. Start Redis Service**
After installation, start Redis from the Command Prompt:
```powershell
redis-server
```

Alternatively, if installed as a service, start it with:
```powershell
net start Redis
```

To stop Redis:
```powershell
net stop Redis
```

### **4. Verify Installation**
To check if Redis is running, open another Command Prompt and run:
```powershell
redis-cli ping
```
If Redis is working correctly, it should return:
```
PONG
```