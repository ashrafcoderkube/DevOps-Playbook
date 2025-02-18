<img src="assets/image.png" alt="MNIO"  width="120" >

MinIO is a high-performance, distributed object storage system that is compatible with the Amazon S3 API. It is often used for building high-performance, scalable cloud-native applications or as a private cloud storage solution. MinIO is lightweight, open-source, and offers high availability, scalability, and security.

---

### **Key Features**

- **S3 Compatibility**: MinIO supports the S3 API, which allows it to be used in place of Amazon S3 for storage.
- **High Performance**: Optimized for high-throughput and low-latency, suitable for demanding applications.
- **Distributed Mode**: MinIO can run in distributed mode for scalability and high availability.
- **Data Protection**: Supports erasure coding and data redundancy to prevent data loss.
- **Security**: Offers server-side encryption, TLS support, and access policies.
- **Easy Deployment**: Can be deployed on any cloud, on-premises, or in a containerized environment.
- **Cross-Platform**: Works across Linux, macOS, and Windows systems.

---

### **Setting Up MinIO**

#### 1. **Install MinIO (Linux)**

MinIO can be installed easily on Linux using the following steps:

1. Download the MinIO binary:
    ```bash
    wget https://dl.min.io/server/minio/release/linux-amd64/minio
    ```

2. Give it execute permissions:
    ```bash
    chmod +x minio
    ```

3. Move the binary to a system-wide directory:
    ```bash
    sudo mv minio /usr/local/bin
    ```

4. Start the MinIO server:
    ```bash
    minio server /data
    ```
    This will start MinIO and store data in the `/data` directory.

#### 2. **Install MinIO (macOS)**

For macOS, you can install MinIO using `brew`:

```bash
brew install minio
```

Then, start the MinIO server:

```bash
minio server /data
```

#### 3. **Install MinIO (Windows)**

For Windows, download the MinIO executable from the [MinIO download page](https://min.io/download) and run it via Command Prompt:

```bash
minio.exe server C:\data
```

---

### **MinIO Commands**

MinIO provides a set of commands for managing the server and interacting with object storage. The MinIO client (`mc`) is used to interact with the server.

#### 1. **Start MinIO Server**

To start the MinIO server in single-node mode:

```bash
minio server /data
```

To start the server in distributed mode (with multiple nodes):

```bash
minio server http://node{1...4}/mnt/data
```

#### 2. **Configure MinIO Client (`mc`)**

The MinIO client (`mc`) allows you to manage objects in your MinIO server.

1. Download and install the MinIO client (`mc`):
    ```bash
    wget https://dl.min.io/client/mc/release/linux-amd64/mc
    chmod +x mc
    sudo mv mc /usr/local/bin
    ```

2. Configure the client to connect to your MinIO server:
    ```bash
    mc alias set myminio http://localhost:9000 minioadmin minioadmin
    ```

#### 3. **MinIO Client Commands**

Here are some basic commands to interact with your MinIO server:

- **List Buckets**:
    ```bash
    mc ls myminio
    ```

- **Create a Bucket**:
    ```bash
    mc mb myminio/mybucket
    ```

- **Upload a File**:
    ```bash
    mc cp myfile.txt myminio/mybucket/
    ```

- **Download a File**:
    ```bash
    mc cp myminio/mybucket/myfile.txt ./downloaded_file.txt
    ```

- **List Files in a Bucket**:
    ```bash
    mc ls myminio/mybucket
    ```

- **Remove a File**:
    ```bash
    mc rm myminio/mybucket/myfile.txt
    ```

- **Remove a Bucket**:
    ```bash
    mc rb myminio/mybucket
    ```

#### 4. **Start MinIO in Distributed Mode**

To run MinIO in distributed mode (across multiple nodes):

```bash
minio server http://node{1...4}/mnt/data
```

This command will run MinIO with 4 nodes, storing data in `/mnt/data` on each node.

#### 5. **Access MinIO Web Interface**

Once the MinIO server is running, you can access the web interface at:

```bash
http://localhost:9000
```

The default credentials are:
- **Access Key**: `minioadmin`
- **Secret Key**: `minioadmin`

---

### **MinIO Configuration**

1. **Environment Variables**: You can set the access and secret keys using environment variables before starting the MinIO server:
    ```bash
    export MINIO_ACCESS_KEY=myaccesskey
    export MINIO_SECRET_KEY=mysecretkey
    minio server /data
    ```

2. **TLS Encryption**: For encrypted communication, configure MinIO with SSL certificates:
    ```bash
    minio server --certs-dir /path/to/certs /data
    ```

---

### **Useful Links**

- **MinIO Documentation**: [https://docs.min.io/](https://docs.min.io/)
- **MinIO GitHub Repository**: [https://github.com/minio/minio](https://github.com/minio/minio)
- **MinIO Client (mc) Documentation**: [https://docs.min.io/docs/minio-client-quickstart-guide.html](https://docs.min.io/docs/minio-client-quickstart-guide.html)
- **MinIO Docker Image**: [https://hub.docker.com/r/minio/minio](https://hub.docker.com/r/minio/minio)

