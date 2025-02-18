<img src="assets/image.png" alt="AWS - s3 " width="250" >

Here are the essential AWS S3 commands for managing buckets and objects using the AWS CLI:

### **1. Configuring AWS CLI**

Before using AWS CLI, configure it with your credentials and default settings:

```bash
aws configure
```
You'll be prompted to provide:
- AWS Access Key ID
- AWS Secret Access Key
- Default region name (e.g., `us-west-1`)
- Default output format (e.g., `json`)

### **2. Bucket Management Commands**

- **Create a Bucket:**

```bash
aws s3 mb s3://my-bucket-name --region us-west-1
```
Creates a new bucket `my-bucket-name` in the specified region.

- **List Buckets:**

```bash
aws s3 ls
```
Lists all the buckets in your AWS account.

- **Delete a Bucket (with Force Option to Empty Bucket):**

```bash
aws s3 rb s3://my-bucket-name --force
```
Deletes the bucket after removing its contents.

- **Get Bucket Information:**

```bash
aws s3api get-bucket-location --bucket my-bucket-name
```
Retrieves the region where the bucket is located.

### **3. Object Management Commands**

- **Upload a File to a Bucket:**

```bash
aws s3 cp myfile.txt s3://my-bucket-name/
```
Uploads `myfile.txt` to the specified bucket.

- **Download a File from a Bucket:**

```bash
aws s3 cp s3://my-bucket-name/myfile.txt ./myfile.txt
```
Downloads `myfile.txt` from the S3 bucket to the local directory.

- **Copy a File from One Bucket to Another:**

```bash
aws s3 cp s3://source-bucket/myfile.txt s3://destination-bucket/
```
Copies `myfile.txt` from the source bucket to the destination bucket.

- **Delete a File from a Bucket:**

```bash
aws s3 rm s3://my-bucket-name/myfile.txt
```
Deletes `myfile.txt` from the specified bucket.

- **List Objects in a Bucket:**

```bash
aws s3 ls s3://my-bucket-name/
```
Lists the objects in the `my-bucket-name` bucket.

### **4. Directory Sync Commands**

- **Sync a Local Directory to an S3 Bucket:**

```bash
aws s3 sync ./local-dir s3://my-bucket-name/
```
Syncs a local directory `./local-dir` with the S3 bucket.

- **Sync an S3 Bucket to a Local Directory:**

```bash
aws s3 sync s3://my-bucket-name/ ./local-dir
```
Syncs the contents of the S3 bucket to a local directory.

### **5. Permissions and Access Control**

- **Set Bucket Policy:**

```bash
aws s3api put-bucket-policy --bucket my-bucket-name --policy file://policy.json
```
Applies a policy from the `policy.json` file to the specified bucket.

- **Get Bucket Policy:**

```bash
aws s3api get-bucket-policy --bucket my-bucket-name
```
Retrieves the current policy applied to the specified bucket.

- **Grant Permissions (ACLs):**

```bash
aws s3api put-object-acl --bucket my-bucket-name --key myfile.txt --acl public-read
```
Grants `public-read` access to `myfile.txt` in the bucket.

### **6. Versioning and Lifecycle**

- **Enable Versioning on a Bucket:**

```bash
aws s3api put-bucket-versioning --bucket my-bucket-name --versioning-configuration Status=Enabled
```
Enables versioning on the S3 bucket.

- **Apply a Lifecycle Policy to a Bucket:**

```bash
aws s3api put-bucket-lifecycle-configuration --bucket my-bucket-name --lifecycle-configuration file://lifecycle.json
```
Applies a lifecycle configuration from `lifecycle.json` to manage object transitions or deletions.

### **7. Transfer Acceleration**

- **Enable Transfer Acceleration:**

```bash
aws s3api put-bucket-accelerate-configuration --bucket my-bucket-name --accelerate-configuration Status=Enabled
```
Enables transfer acceleration to speed up uploads to S3.

### **8. Logging and Analytics**

- **Enable Access Logging on a Bucket:**

```bash
aws s3api put-bucket-logging --bucket my-bucket-name --bucket-logging-status file://logging.json
```
Enables access logging on the bucket with settings from `logging.json`.

### **9. Other Utility Commands**

- **Check if a Bucket Exists:**

```bash
aws s3api head-bucket --bucket my-bucket-name
```
Returns metadata for the bucket. If the bucket does not exist, it will throw an error.

---

### **Useful AWS S3 CLI Options**

- `--dryrun`: Simulates the operation without actually performing it (useful for testing).
- `--recursive`: Used with commands like `cp` and `sync` to operate on directories recursively.
- `--exclude` and `--include`: Used in sync or copy operations to filter files based on pattern matching.

---

### **Official AWS S3 Documentation Links**

- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [AWS CLI S3 Command Reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
- [S3 Best Practices](https://aws.amazon.com/s3/best-practices/)
- [S3 Security Best Practices](https://aws.amazon.com/s3/security/)

