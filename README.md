# AWS VPC + ALB Multi-AZ Architecture

## 📌 Overview
Designed and implemented a highly available, secure, and scalable AWS architecture using a multi-AZ VPC with Application Load Balancer (ALB), private EC2 instances, and controlled outbound internet access.

---

## 🚀 Project Impact
- Designed a **highly available multi-AZ architecture** eliminating single point of failure
- Improved **application reliability** using ALB-based traffic distribution
- Implemented **secure private subnet architecture** with no direct internet exposure
- Enabled **secure admin access without SSH** using AWS Systems Manager (SSM)

---

## 🏗️ Architecture Components

### 🌐 Network Layer
- VPC: `192.168.0.0/24`
- Region: `ap-south-1`
- 2 Availability Zones:
  - ap-south-1a
  - ap-south-1b

### 🌍 Public Subnets
- ALB deployed across both AZs
- NAT Gateway in each public subnet
- Route Table:
  - `0.0.0.0/0 → Internet Gateway`

### 🔒 Private Subnets
- EC2 instances hosted (Web Server 1 & 2)
- No public IP assigned
- Route Table:
  - `0.0.0.0/0 → NAT Gateway`

---

## ⚙️ Core Services Used
- Amazon VPC
- Application Load Balancer (ALB)
- EC2 (Amazon Linux)
- NAT Gateway
- Internet Gateway
- AWS Systems Manager (SSM)
- Security Groups
- Route Tables
- CloudWatch (basic monitoring)

---

## 🔁 Traffic Flow

1. User → Internet → Internet Gateway  
2. Internet Gateway → Application Load Balancer (public subnets)  
3. ALB → Target Group → EC2 instances (private subnets)  
4. EC2 outbound traffic → NAT Gateway → Internet  
5. Admin access → SSM Session Manager → EC2 (no SSH required)  

---

## 🔐 Security Design

- EC2 instances deployed in **private subnets** (no direct internet access)
- **Security Group chaining**:
  - ALB-SG → allows HTTP (port 80) from internet
  - Web-SG → allows HTTP (port 80) only from ALB-SG
- No SSH (port 22) exposed
- Secure admin access via **SSM Session Manager (HTTPS 443)**
- Controlled outbound internet via NAT Gateway

---

## 📊 Architecture Explanation

- ALB is deployed across multiple AZs for **high availability**
- EC2 instances distributed across AZs for **fault tolerance**
- NAT Gateways enable **secure outbound internet access**
- Internet Gateway allows inbound traffic only via ALB
- SSM replaces traditional SSH-based access

---

## 🖼️ Architecture Diagram

<img width="1536" height="1024" alt="AWS VPC + ALB Multi-AZ Architectur_diagram" src="https://github.com/user-attachments/assets/5b707d52-d2c9-4397-80c9-f0757d9bf0db" />



---

## 🧪 Live Result

### Web Server 1
<img width="807" height="781" alt="image" src="https://github.com/user-attachments/assets/c03c1173-db71-4150-b209-e8e0a12dffce" />



### Web Server 2
<img width="910" height="820" alt="image" src="https://github.com/user-attachments/assets/d61862d3-f6cb-41ad-a649-330a20d6532f" />

---

## 📚 Key Learnings

- Designed real-world **multi-AZ production architecture**
- Understood **VPC networking, subnet isolation, and routing**
- Implemented **load balancing and high availability patterns**
- Learned **secure access patterns using SSM (no SSH)**
- Practiced **Infrastructure design thinking over just service usage**



## 👤 Author

**Ashutosh Chaudhary**  
Cloud Operations Engineer | AWS | Terraform | Linux | 
