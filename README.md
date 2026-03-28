# AWS VPC + ALB Architecture

## What I Built
- Multi-AZ VPC in ap-south-1
- 2 Public Subnets — ALB lives here
- 2 Private Subnets — EC2 instances live here
- ALB Security Group — Port 80 from internet
- Web Security Group — Port 80 from ALB only
- Load balancing across 2 private EC2 servers

## Architecture Diagram
<img width="1536" height="1024" alt="AWS VPC + ALB Multi-AZ Architectur_diagram" src="https://github.com/user-attachments/assets/3a8e15cc-169a-4f62-a0af-f749c6f3c60b" />

## Live Result
### Web Server 1
<img width="807" height="781" alt="image" src="https://github.com/user-attachments/assets/27cecccb-79e3-4cd9-8bdc-149cf3898a93" />


### Web Server 2
<img width="910" height="820" alt="image" src="https://github.com/user-attachments/assets/162f6b9e-4185-47c6-9736-f99966eab221" />


## Key Learnings
- EC2 private subnet mein rakha — direct internet access nahi
- ALB public subnet mein — internet traffic receive karta hai
- Security Groups chained — ALB SG → Web SG
- Multi-AZ — high availability
