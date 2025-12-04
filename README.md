🚀 AWS Cloud Engineer Internship – Technical Assessment

Author: Prakhar Bajpai
Email: prakharbajpai727504@gmail.com

This repository contains all deliverables for the Cloud Engineer Internship – Technical Assessment, including Terraform code, architecture explanation, diagrams, and screenshots instructions.
Each question is placed in its own folder with the required files.
├── Q1_VPC_Setup
│   ├── main.tf
│   ├── README.md
│
├── Q2_EC2_Static_Website
│   ├── main.tf
│   ├── user_data_nginx.sh
│   ├── README.md
│
├── Q3_HA_AutoScaling
│   ├── main.tf
│   ├── user_data_nginx.sh
│   ├── README.md
│
├── Q4_Billing_Alerts
│   ├── README.md
│
├── Q5_Architecture_Diagram
│   ├── README.md
│   ├── architecture.png  (Upload your draw.io file or PNG here)
│


📌 Overview of Tasks

This assessment includes 5 major AWS tasks:

✅ 1. Networking & Subnetting – AWS VPC Setup

Deliverables included:

Terraform code to create:

1 VPC

2 Public Subnets

2 Private Subnets

Internet Gateway (IGW)

NAT Gateway

Route Tables

Explanation of VPC Design

CIDR breakdown

Add AWS screenshots in Q1_VPC_Setup/README.md after deploying

✅ 2. EC2 Static Resume Website Hosting

Deliverables included:

Terraform code to launch a Free Tier EC2 instance

Security group for HTTP/SSH

Nginx installation via user-data

Static resume website hosting

Hardening steps explanation

Add AWS screenshots in Q2_EC2_Static_Website/README.md

✅ 3. High Availability (HA) + Auto Scaling Architecture

Deliverables included:

Internet-facing Application Load Balancer (ALB)

Auto Scaling Group (ASG) across 2 AZs

Target Group

Private subnets for backend EC2 instances

Traffic flow explanation

Add AWS screenshots in Q3_HA_AutoScaling/README.md

✅ 4. Billing & Free Tier Cost Monitoring

Deliverables included:

Explanation of cost alerts

Steps for setting a Billing Alarm

Importance of cost monitoring

Add screenshots of Billing Alert + Free Tier alerts in Q4_Billing_Alerts/README.md

✅ 5. AWS Architecture Diagram (draw.io)

Deliverables included:

Complete architecture diagram showing:

ALB

ASG

Public & Private Subnets

RDS / Aurora

ElastiCache (Redis)

Security Layers (SG, NACL, WAF)

CloudWatch

Explanation in README

Upload PNG/PDF to Q5_Architecture_Diagram/

🧩 How to Use This Repository
🔹 Step 1: Clone the repository
git clone https://github.com/<your-username>/<repo-name>.git

🔹 Step 2: Navigate to each folder

Each folder contains:

Terraform code

README.md with explanation

Placeholders for screenshots

🔹 Step 3: Add AWS screenshots

Upload them where instructed in each folder’s README.md.

🔹 Step 4: Test and clean up

After deployment:

Destroy all resources to avoid charges:

terraform destroy

📌 Notes

All resource names follow the required prefix format:
FirstName_Lastname_...

Terraform files are modular and easy to run.

All resources are Free Tier–compatible.
├── Prakhar_Bajpai_Resume.pdf
├── README.md (this file)
