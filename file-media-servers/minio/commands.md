<img src="assets/image.png" alt="MNIO"  width="120" >

### **1. MinIO Server Commands**

- **Start MinIO Server in Single Node Mode**:
    ```bash
    minio server /data
    ```

- **Start MinIO Server in Distributed Mode** (with multiple nodes):
    ```bash
    minio server http://node{1...4}/mnt/data
    ```

- **Start MinIO Server with TLS/SSL Encryption**:
    ```bash
    minio server --certs-dir /path/to/certs /data
    ```

---

### **2. MinIO Client (`mc`) Commands**

The MinIO Client (`mc`) allows you to interact with the MinIO server and manage your data.

#### **Configuration and Setup**

- **Add a MinIO Server Alias**:
    ```bash
    mc alias set <alias> <url> <access-key> <secret-key>
    ```

    Example:
    ```bash
    mc alias set myminio http://localhost:9000 minioadmin minioadmin
    ```

#### **Bucket Operations**

- **List Buckets**:
    ```bash
    mc ls <alias>
    ```

    Example:
    ```bash
    mc ls myminio
    ```

- **Create a Bucket**:
    ```bash
    mc mb <alias>/<bucket-name>
    ```

    Example:
    ```bash
    mc mb myminio/mybucket
    ```

- **Remove a Bucket**:
    ```bash
    mc rb <alias>/<bucket-name>
    ```

    Example:
    ```bash
    mc rb myminio/mybucket
    ```

#### **File Operations**

- **Upload a File to a Bucket**:
    ```bash
    mc cp <local-file> <alias>/<bucket-name>/
    ```

    Example:
    ```bash
    mc cp myfile.txt myminio/mybucket/
    ```

- **Download a File from a Bucket**:
    ```bash
    mc cp <alias>/<bucket-name>/<file-name> <local-file>
    ```

    Example:
    ```bash
    mc cp myminio/mybucket/myfile.txt ./downloaded_file.txt
    ```

- **List Files in a Bucket**:
    ```bash
    mc ls <alias>/<bucket-name>
    ```

    Example:
    ```bash
    mc ls myminio/mybucket
    ```

- **Remove a File from a Bucket**:
    ```bash
    mc rm <alias>/<bucket-name>/<file-name>
    ```

    Example:
    ```bash
    mc rm myminio/mybucket/myfile.txt
    ```

#### **Metadata Operations**

- **Get Object Metadata**:
    ```bash
    mc stat <alias>/<bucket-name>/<file-name>
    ```

    Example:
    ```bash
    mc stat myminio/mybucket/myfile.txt
    ```

---

### **3. MinIO Server Configuration**

- **Set Custom Access and Secret Keys via Environment Variables**:
    ```bash
    export MINIO_ACCESS_KEY=myaccesskey
    export MINIO_SECRET_KEY=mysecretkey
    minio server /data
    ```

- **Enable Event Notifications** (e.g., for S3-compatible services):
    ```bash
    mc event add <alias>/<bucket-name> arn:minio:sqs:us-east-1:123456789012:sqs --event "s3:ObjectCreated:*"
    ```

---

### **4. MinIO Docker Commands**

If you want to run MinIO in Docker, you can use the following commands:

- **Run MinIO Server in Docker**:
    ```bash
    docker run -p 9000:9000 -p 9001:9001 --name minio \
      -e "MINIO_ACCESS_KEY=minioadmin" -e "MINIO_SECRET_KEY=minioadmin" \
      minio/minio server /data
    ```

- **Run MinIO Server with TLS in Docker**:
    ```bash
    docker run -p 9000:9000 -p 9001:9001 --name minio \
      -e "MINIO_ACCESS_KEY=minioadmin" -e "MINIO_SECRET_KEY=minioadmin" \
      -v /path/to/certs:/certs minio/minio server --certs-dir /certs /data
    ```

---

### **5. Other Useful Commands**

- **View MinIO Logs**:
    ```bash
    tail -f /var/log/minio/minio.log
    ```

- **Check MinIO Server Status**:
    ```bash
    systemctl status minio
    ```

- **Stop MinIO Server**:
    ```bash
    systemctl stop minio
    ```
