## MongoDB Database Server Installation & Usage on macOS

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

### **2. Install MongoDB**
```bash
brew tap mongodb/brew
brew install mongodb-community@6.0
```

### **3. Start MongoDB Service**
```bash
brew services start mongodb-community@6.0
```

### **4. Verify Installation**
```bash
mongosh
```
If you see the MongoDB shell prompt, MongoDB is running.