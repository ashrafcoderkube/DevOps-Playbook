## Redis Database Server Installation & Usage on macOS

### **System Requirements**

- **Operating System**: macOS Monterey, Big Sur, or later
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space


## **Installation Steps**

### **1. Install Homebrew (If Not Installed)**
If Homebrew is not installed, install it with:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **2. Install Redis**
```bash
brew install redis
```

### **3. Start and Enable Redis Service**
```bash
brew services start redis
```

### **4. Verify Installation**
Check Redis service status:
```bash
brew services list
```

To check if Redis is working properly, run:
```bash
redis-cli ping
```
If Redis is running correctly, it should return:
```
PONG
```