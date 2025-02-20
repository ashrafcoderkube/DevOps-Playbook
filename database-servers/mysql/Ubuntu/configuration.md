# MySQL Database Server Configuration on Ubuntu

## **Configuration**

### **1. Allow Remote Access (Optional)**
By default, MySQL only allows connections from `localhost`. To allow remote access, edit the configuration file:

```bash
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

Find the following line and change `127.0.0.1` to `0.0.0.0`:

```ini
bind-address = 0.0.0.0
```

Save the file and restart MySQL:

```bash
sudo systemctl restart mysql
```

### **2. Create a New Database and User**
Log in to MySQL as the root user:

```bash
sudo mysql -u root -p
```

Create a new database and user:

```sql
CREATE DATABASE my_database;
CREATE USER 'my_user'@'%' IDENTIFIED BY 'mypassword';
GRANT ALL PRIVILEGES ON my_database.* TO 'my_user'@'%';
FLUSH PRIVILEGES;
EXIT;
```


### **How to Use MySQL Database Server**

### **1. Connect to MySQL**
To connect to MySQL, use the following command:

```bash
mysql -u my_user -p
```

Enter the password when prompted.

### **2. Show Databases**
To list all available databases:

```sql
SHOW DATABASES;
```

### **3. Select and Use a Database**
To select a specific database:

```sql
USE my_database;
```

### **4. Create a Table**
To create a table inside the database:

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

### **5. Insert Data into a Table**
To insert data into the table:

```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### **6. Retrieve Data**
To fetch data from the table:

```sql
SELECT * FROM users;
```

### **7. Backup and Restore Databases**

#### **Backup a Database**
To create a backup of a MySQL database:

```bash
mysqldump -u my_user -p my_database > backup.sql
```

#### **Restore a Database**
To restore a database from a backup file:

```bash
mysql -u my_user -p my_database < backup.sql
```

## **Troubleshooting**

- **MySQL Service Not Running**: Restart the service:
  
  ```bash
  sudo systemctl restart mysql
  ```
  
- **Permission Issues**: Ensure correct user privileges:
  
  ```sql
  FLUSH PRIVILEGES;
  ```
  
- **Connection Issues**: Check if MySQL is listening on the correct port:
  
  ```bash
  sudo netstat -tulnp | grep mysql
  ```
  
