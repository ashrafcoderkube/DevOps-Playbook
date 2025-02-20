## Memcached Caching Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download Memcached for Windows**
1. Download the latest Memcached binary for Windows from [Northscale](https://github.com/northscale/memcached).
2. Extract the downloaded `.zip` file to `C:\Memcached`.

### **2. Install Memcached as a Windows Service**
Open Command Prompt as Administrator and run:
```powershell
C:\Memcached\memcached.exe -d install
net start memcached
```

### **3. Verify Installation**
Check if Memcached is running:
```powershell
memcached.exe -d stats
```
If Memcached is working correctly, it should return statistics.