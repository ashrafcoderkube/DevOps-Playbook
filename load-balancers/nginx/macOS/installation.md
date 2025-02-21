## Nginx Load Balancer Installation & Usage on macOS

### **System Requirements**

- **Operating System**: macOS Monterey, Big Sur, or later
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Install Homebrew (If Not Installed)**
If Homebrew is not installed, install it with:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **2. Install Nginx**
```bash
brew install nginx
```

### **3. Start and Enable Nginx Service**
```bash
brew services start nginx
```

### **4. Verify Installation**
Check if Nginx is running:
```bash
brew services list
```