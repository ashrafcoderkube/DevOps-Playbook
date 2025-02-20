## PostgreSQL Database Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space


## **Installation Steps**

### **1. Download PostgreSQL**
- Visit the [official PostgreSQL website](https://www.postgresql.org/download/).
- Select **Windows** and download the latest version.
- Run the downloaded installer (`.exe`).

### **2. Install PostgreSQL**
- Select **Next** to proceed.
- Choose the installation directory (default: `C:\Program Files\PostgreSQL\`).
- Select components: **PostgreSQL Server, pgAdmin, Command Line Tools**.
- Set a password for the default PostgreSQL user (`postgres`).
- Choose the port number (default: `5432`).
- Finish installation and restart your computer if required.

### **3. Start PostgreSQL Service**
- PostgreSQL should start automatically as a Windows service.
- To manually start it:
  ```powershell
  net start postgresql-x64-14
  ```
- To stop PostgreSQL:
  ```powershell
  net stop postgresql-x64-14
  ```

### **4. Verify Installation**
Open **pgAdmin** from the Start menu or use the command line:

```powershell
psql -U postgres
```

Enter the password you set during installation.
