# MySQL Database Server Configuration on Windows

## **Configuration**

### **1. Start and Stop MySQL Service**
To start the MySQL service, open Command Prompt as Administrator and run:

```cmd
net start mysql
```

To stop the MySQL service:

```cmd
net stop mysql
```

Alternatively, you can manage MySQL from **Windows Services**:
- Press `Win + R`, type `services.msc`, and hit Enter.
- Find **MySQL Server**, right-click, and choose **Start** or **Stop**.

### **2. Configure MySQL Server Settings**
- MySQL configuration file (`my.ini`) is located at:
  ```
  C:\ProgramData\MySQL\MySQL Server 8.0\my.ini
  ```
- To allow remote connections, open `my.ini` and modify:
  ```ini
  bind-address = 0.0.0.0
  ```
- Restart MySQL for changes to take effect:
  ```cmd
  net stop mysql && net start mysql
  ```

---

## **How to Use MySQL**

### **1. Open MySQL Command Line**
- Open Command Prompt (`cmd`) and log in to MySQL:
  ```cmd
  mysql -u root -p
  ```
  Enter the root password when prompted.

### **2. Create a Database**
```sql
CREATE DATABASE my_database;
```

### **3. Create a User and Grant Permissions**
```sql
CREATE USER 'my_user'@'localhost' IDENTIFIED BY 'mypassword';
GRANT ALL PRIVILEGES ON my_database.* TO 'my_user'@'localhost';
FLUSH PRIVILEGES;
```

### **4. Show Available Databases**
```sql
SHOW DATABASES;
```

### **5. Use a Specific Database**
```sql
USE my_database;
```

### **6. Create a Table**
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

### **7. Insert Data into a Table**
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### **8. Retrieve Data**
```sql
SELECT * FROM users;
```

### **9. Backup and Restore MySQL Database**

#### **Backup Database**
```cmd
mysqldump -u root -p my_database > backup.sql
```

#### **Restore Database**
```cmd
mysql -u root -p my_database < backup.sql
```

---

## **Troubleshooting**

- **MySQL Command Not Recognized**:
  - Ensure MySQL is added to the system PATH:
    ```cmd
    setx PATH "%PATH%;C:\Program Files\MySQL\MySQL Server 8.0\bin"
    ```
- **MySQL Service Not Starting**:
  - Check the MySQL error log located in:
    ```
    C:\ProgramData\MySQL\MySQL Server 8.0\Data\
    ```
  - Restart the MySQL service manually.

- **Forgot MySQL Root Password**:
  1. Stop MySQL Service:
     ```cmd
     net stop mysql
     ```
  2. Start MySQL in Safe Mode:
     ```cmd
     mysqld --skip-grant-tables --skip-networking
     ```
  3. Open MySQL and reset the password:
     ```sql
     ALTER USER 'root'@'localhost' IDENTIFIED BY 'newpassword';
     FLUSH PRIVILEGES;
     ```
  4. Restart MySQL:
     ```cmd
     net start mysql
     ```