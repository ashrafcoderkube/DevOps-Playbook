# **ELB Commands**

### **List All Load Balancers**
```bash
aws elbv2 describe-load-balancers
```

### **Describe a Specific Load Balancer**
```bash
aws elbv2 describe-load-balancers --names my-load-balancer
```

### **List Target Groups**
```bash
aws elbv2 describe-target-groups
```

### **Check Registered Targets**
```bash
aws elbv2 describe-target-health --target-group-arn arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789
```

### **Deregister EC2 Instance from Target Group**
```bash
aws elbv2 deregister-targets --target-group-arn arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789 \
    --targets Id=i-0abcdef1234567890
```

### **Delete Load Balancer**
```bash
aws elbv2 delete-load-balancer --load-balancer-arn arn:aws:elasticloadbalancing:region:account-id:loadbalancer/app/my-load-balancer/123456789
```