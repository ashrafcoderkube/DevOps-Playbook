## Nginx Load Balancer Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection

## **Installation Steps**

### **1. Download Nginx for Windows**
1. Visit the official [Nginx website](https://nginx.org/en/download.html).
2. Download the latest stable Windows build (`nginx-*.zip`).
3. Extract the ZIP file to `C:\nginx`.

### **2. Start Nginx**
Open a Command Prompt as Administrator and run:
```powershell
cd C:\nginx
start nginx
```

### **3. Verify Installation**
Open a web browser and go to:
```
http://localhost
```
You should see the default Nginx welcome page.