## HAProxy Load Balancer Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection

## **Installation Steps**

### **1. Download and Install HAProxy**
1. Download the latest HAProxy binary for Windows from the [official HAProxy repository](https://github.com/haproxy/haproxy/releases).
2. Extract the ZIP file to `C:\haproxy`.
3. Open Command Prompt as Administrator and navigate to the extracted folder:
   ```powershell
   cd C:\haproxy
   ```

### **2. Verify Installation**
Check if HAProxy runs correctly:
```powershell
haproxy.exe -v
```