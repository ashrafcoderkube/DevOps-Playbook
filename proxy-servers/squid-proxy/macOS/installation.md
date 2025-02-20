## Squid Proxy Server Installation & Usage on macOS

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

### **2. Install Squid**
```bash
brew install squid
```

### **3. Start and Enable Squid Service**
```bash
brew services start squid
```

### **4. Verify Installation**
Check if Squid is running:
```bash
brew services list
```

To check if Squid is working, run:
```bash
curl -I --proxy http://localhost:3128 http://example.com
```

