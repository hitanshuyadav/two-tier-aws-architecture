 ## 🏗️ Architecture Overview

This project demonstrates a production-level, highly scalable and highly available AWS architecture.  
It is designed following best practices for security, fault tolerance, and performance.

---

## ⚙️ Architecture Setup Steps

1. Created a custom VPC with CIDR block `10.0.0.0/16`

2. Created four subnets across multiple Availability Zones for high availability:
   - 2 Public Subnets  
   - 2 Private Subnets  

3. Attached an Internet Gateway (IGW) to the VPC to enable internet connectivity

4. Created two route tables:
   - Public Route Table (for public subnets)
   - Private Route Table (for private subnets)

5. Configured routes:
   - Public subnets → Internet Gateway  
   - Private subnets → NAT Gateway  

6. Deployed an Application Load Balancer (ALB) in public subnets

7. Created an Auto Scaling Group (ASG) in private subnets and attached it to a target group

8. Configured a NAT Gateway in public subnet to allow outbound internet access for private EC2 instances

9. Created an S3 bucket and uploaded static website files (HTML, CSS, JS)

10. Synced S3 content to EC2 instances using AWS CLI (inside launch template with NGINX)

11. Integrated CloudFront for fast global content delivery

---

## 🔄 Workflow of User Request

1. User sends request → reaches CloudFront  
2. CloudFront checks cache:
   - If cached → returns response immediately  
   - Else → forwards request to ALB  

3. ALB distributes request to target group (EC2 instances)

4. Target group performs health checks:
   - Healthy instances → receive traffic  
   - Unhealthy instances → replaced by Auto Scaling Group  

5. EC2 instances (running NGINX) serve the web content to users

---

## 🔐 Key Features

- High Availability using Multi-AZ deployment  
- Secure architecture with private subnets  
- Auto Scaling for fault tolerance  
- NAT Gateway for controlled outbound access  
- CloudFront CDN for low latency performance  

---
