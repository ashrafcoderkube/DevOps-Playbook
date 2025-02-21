## AWS Elastic Load Balancer (ELB) Setup & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **AWS Account**: Required for creating ELB
- **AWS CLI**: Installed on your Windows machine
- **IAM Permissions**: Ensure you have the necessary IAM permissions to create and manage ELB

## **Installation Steps**

### **1. Install AWS CLI**
If AWS CLI is not installed, install it using the official installer:

1. Download the AWS CLI installer from [AWS CLI official website](https://aws.amazon.com/cli/).
2. Run the installer and follow the setup instructions.
3. Verify installation by running the following command in PowerShell:
   ```powershell
   aws --version
   ```

### **2. Configure AWS CLI**
Set up AWS CLI with your credentials:
```powershell
aws configure
```
You will be prompted to enter:
- AWS Access Key ID
- AWS Secret Access Key
- Default region (e.g., `us-east-1`)
- Output format (default: `json`)

### **3. Create an ELB**
Run the following command to create an Application Load Balancer (ALB):
```powershell
aws elbv2 create-load-balancer --name my-load-balancer `
    --subnets subnet-abc123 subnet-def456 `
    --security-groups sg-12345678 `
    --scheme internet-facing `
    --type application
```
For a Network Load Balancer (NLB), use `--type network`.

### **4. Create Target Group**
```powershell
aws elbv2 create-target-group --name my-target-group `
    --protocol HTTP --port 80 --vpc-id vpc-12345678
```

### **5. Register EC2 Instances with Target Group**
```powershell
aws elbv2 register-targets --target-group-arn arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789 `
    --targets Id=i-0abcdef1234567890 Id=i-0abcdef1234567891
```

### **6. Create Listener for ELB**
```powershell
aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:region:account-id:loadbalancer/app/my-load-balancer/123456789 `
    --protocol HTTP --port 80 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789
```

## **Troubleshooting**

- **ELB Not Routing Traffic**:
  ```powershell
  aws elbv2 describe-target-health --target-group-arn arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789
  ```
- **Security Group Issues**:
  Ensure that the ELB security group allows inbound traffic on port 80 and 443.
  ```powershell
  aws ec2 describe-security-groups --group-ids sg-12345678
  ```
- **Instances Unhealthy in Target Group**:
  Verify if the health check settings match the application endpoint:
  ```powershell
  aws elbv2 describe-target-groups --names my-target-group
  ```