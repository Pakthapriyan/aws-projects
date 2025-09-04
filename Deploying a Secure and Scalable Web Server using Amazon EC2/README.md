# 🚀 Deploying a Secure and Scalable Web Server using Amazon EC2

This project demonstrates how to deploy, secure, monitor, and scale a **web server on Amazon EC2**.  
It is based on my AWS re/Start Lab exercise and highlights key cloud computing skills such as provisioning, automation, monitoring, and scaling.

---

## 🏗️ Architecture
- **Amazon EC2** → Linux instance hosting Apache HTTP server
- **Amazon EBS** → Resized from 8 GiB → 10 GiB for storage scalability
- **Security Group** → Configured to allow HTTP (port 80) access
- **CloudWatch** → Monitors instance health & performance
- **Termination Protection** → Prevents accidental deletion

![Architecture Diagram](architecture-diagram.png)

---

## ⚡ Key Features
1. Provision an EC2 instance with **User Data script** to auto-install Apache web server.
2. Enable **Termination Protection** for security.
3. Configure **Security Groups** for HTTP traffic (port 80).
4. Monitor health checks using **CloudWatch**.
5. **Resize EC2 instance type** → `t2.micro` → `t2.small`.
6. **Expand EBS storage volume** → 8 GiB → 10 GiB.
7. Validate successful scaling inside the instance.

---

## 🔧 User Data Script
```bash
#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
