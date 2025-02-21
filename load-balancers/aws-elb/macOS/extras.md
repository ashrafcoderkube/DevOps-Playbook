# **How to Use AWS ELB**

### **1. Test Load Balancer**
Access the ELB DNS name from a web browser or use `curl`:
```bash
curl -I http://my-load-balancer-1234567890.region.elb.amazonaws.com
```

### **2. Monitor Load Balancing in Real-Time**
Check ELB logs and metrics using AWS CloudWatch:
```bash
aws cloudwatch describe-alarms --alarm-name-prefix my-load-balancer
```

### **3. Enable Access Logs**
To enable ELB access logs:
```bash
aws elbv2 modify-load-balancer-attributes --load-balancer-arn arn:aws:elasticloadbalancing:region:account-id:loadbalancer/app/my-load-balancer/123456789 \
    --attributes Key=access_logs.s3.enabled,Value=true Key=access_logs.s3.bucket,Value=my-log-bucket
```

### **4. Enable HTTPS on ELB**
To add an HTTPS listener:
```bash
aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:region:account-id:loadbalancer/app/my-load-balancer/123456789 \
    --protocol HTTPS --port 443 --certificates CertificateArn=arn:aws:acm:region:account-id:certificate/1234abcd-12ab-34cd-56ef-1234567890ab \
    --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:region:account-id:targetgroup/my-target-group/123456789
```
