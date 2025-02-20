# MySQL Database Server Configuration on macOS

## **Configuration**

### **1. Connect to MySQL**
To access MySQL, use:
```bash
mysql -u root -p
```
Enter your root password when prompted.


### **2. Configure MySQL to Start on Boot**
To automatically start MySQL when macOS boots:

```bash
brew services start mysql
```


### **3. Change MySQL Configuration (Optional)**
The MySQL configuration file is located at:

```bash
/usr/local/etc/my.cnf
```

You can edit it with:

```bash
nano /usr/local/etc/my.cnf
```

After making changes, restart MySQL:

```bash
brew services restart mysql
```

### How to Use MySQL on macOS

### **1. Create a New Database**
```sql
CREATE DATABASE example_database;
```

### **2. Create a New User and Grant Privileges**
```sql
CREATE USER 'example_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON example_database.* TO 'example_user'@'localhost';
FLUSH PRIVILEGES;
```

### **3. List All Databases**
```sql
SHOW DATABASES;
```

### **4. Use a Specific Database**
```sql
USE example_database;
```

### **5. Create a Table**
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

### **6. Insert Data into the Table**
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### **7. Retrieve Data**
```sql
SELECT * FROM users;
```

### **8. Backup and Restore MySQL Database**

**Backup Database**
```bash
mysqldump -u root -p example_database > backup.sql
```

**Restore Database**
```bash
mysql -u root -p example_database < backup.sql
```


## **Troubleshooting**

- **MySQL command not found:** Ensure /usr/local/bin is in your PATH or run:
  ```bash
  echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
  ```
  
- **MySQL not starting:** Check for errors with:
  ```bash
  tail -f /usr/local/var/mysql/*.err
  ```
  
- **Lost MySQL root password:** Reset the password by stopping MySQL and restarting it with a skip-grant option:
  
  ```bash
  brew services stop mysql
  mysqld_safe --skip-grant-tables &
  mysql -u root
  ```

Then reset the password:
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'newpassword';
FLUSH PRIVILEGES;
```
Restart MySQL:
```bash
brew services restart mysql
```