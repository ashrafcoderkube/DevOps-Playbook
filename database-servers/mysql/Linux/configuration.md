# MySQL Database Server Configuration on Linux

## **Configuration**

### **1. Configure MySQL User Access**

By default, MySQL allows the root user to access the database only from the localhost. To configure MySQL to allow remote access, you need to modify the MySQL configuration file.

**Edit MySQL Configuration File**

Open the MySQL configuration file (`my.cnf`) for editing:
```bash
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf  # Ubuntu/Debian-based
```
or
```bash
sudo nano /etc/my.cnf  # CentOS/RHEL-based
```

Find the line with `bind-address` and change it from `127.0.0.1` to `0.0.0.0` to allow remote connections:

```ini
bind-address = 0.0.0.0
```
#### Save the file and restart MySQL:

```bash
sudo systemctl restart mysql
```


### **2. Create MySQL Database and User**

You can create databases and users from the MySQL command-line client. First, log in as the root user:
```bash
sudo mysql -u root -p
```

Then, run the following SQL commands to create a new database and user:

```sql
CREATE DATABASE example_database;
CREATE USER 'example_user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON example_database.* TO 'example_user'@'%';
FLUSH PRIVILEGES;
```

Exit the MySQL client:
```sql
exit
```


### How to Use MySQL Database Server

### **1. Connect to MySQL Database**
To connect to the MySQL server, use the following command:
```bash
mysql -u example_user -p
```
Enter the password when prompted.

### **2. Show Existing Databases**
To list all databases:
```sql
SHOW DATABASES;
```

### **3. Select and Use a Database**
To select a database to work with:
```sql
USE example_database;
```

### **4. Create Tables**
To create a table inside the selected database:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

### **5. Insert Data into Tables**
To insert data into the table:
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### **6. Query Data**
To select data from a table:
```sql
SELECT * FROM users;
```

### **7. Backup and Restore Databases**

**Backup Database**
To back up a MySQL database, use the mysqldump command:
```bash
mysqldump -u example_user -p example_database > backup.sql
```

**Restore Database**
To restore a database from a backup file:
```bash
mysql -u example_user -p example_database < backup.sql
```