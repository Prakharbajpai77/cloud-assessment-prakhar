# Prakhar_Bajpai_AWS_Assessment

**Cloud Engineer Internship — Technical Assessment**

This repository contains Terraform templates, user-data scripts, architecture diagrams and evidence (screenshots) for the Cloud Engineer Internship technical assessment.  
All resources were created with the prefix `FirstName_Lastname_` — replace with your actual first and last name before applying any infrastructure.

---

## Repository Structure

/
├─ Q1_VPC_Setup/
│ ├─ main.tf
│ ├─ README.md
│ └─ screenshots/ # VPC, Subnets, Route tables, IGW, NAT Gateway screenshots
├─ Q2_EC2_Static_Website/
│ ├─ main.tf
│ ├─ user_data_nginx.sh
│ ├─ README.md
│ └─ screenshots/ # EC2, Security Group, Browser screenshot
├─ Q3_HA_AutoScaling/
│ ├─ main.tf
│ ├─ user_data_nginx.sh
│ ├─ README.md
│ └─ screenshots/ # ALB, Target groups, ASG, Instances
├─ Q4_Billing_Alerts/
│ ├─ README.md
│ └─ screenshots/ # Billing alarm, Free Tier alerts
├─ Q5_Architecture_Diagram/
│ ├─ diagram.drawio
│ ├─ diagram.png
│ └─ README.md
├─ Prakhar_Bajpai_Resume.pdf
└─ README.md

markdown
Copy code

---

## Assessment Summary (Quick)

- **Author:** Prakhar Bajpai  
- **Email:** prakharbajpai727504@gmail.com  
- **Tasks included:** VPC/Subnets, EC2 static website (Nginx), HA architecture with ALB + ASG, Billing & Free Tier alerts, draw.io architecture diagram.  
- **Terraform:** One `main.tf` per question (Q1–Q3). Q4 contains instructions (billing alarms often require console or specific permissions).  
- **Naming convention:** All created resources use prefix `FirstName_Lastname_` (please replace before deploying).

---

## How to run (local machine with Terraform)

> ⚠️ **Important safety**: Do **not** apply these templates in a production account. Use a Free Tier account and delete all resources after validation. Replace `FirstName_Lastname` and any `YOUR_IP/32` placeholders.

1. **Install prerequisites**
   - Terraform v1.0+  
   - AWS CLI configured with your AWS Free Tier account (`aws configure`)  
   - (Optional) jq

2. **Initialize & plan**
```bash
cd Q1_VPC_Setup
terraform init
terraform plan -var="aws_region=us-east-1" -out=q1.plan
Apply

bash
Copy code
terraform apply q1.plan
Destroy (cleanup)

bash
Copy code
terraform destroy -auto-approve
Repeat the same steps for Q2_EC2_Static_Website and Q3_HA_AutoScaling. Ensure var values (vpc_id, subnet ids, your IP for SSH) are set either in terraform.tfvars or via CLI.

What I included for each question
Q1 — VPC & Subnets
main.tf creating: VPC (/16), 2 public subnets, 2 private subnets, IGW, NAT Gateway, route tables and associations.

README.md describes CIDR choices and rationale.

screenshots/ with VPC, Subnets, Route Tables, NAT + IGW.

CIDR choices used (example):

VPC: 10.0.0.0/16

Public A: 10.0.1.0/24

Public B: 10.0.2.0/24

Private A: 10.0.11.0/24

Private B: 10.0.12.0/24

Q2 — EC2 Static Website (Nginx)
main.tf for EC2, SG allowing HTTP and restricted SSH.

user_data_nginx.sh to install nginx & deploy index.html.

screenshots/ for EC2, Security Group, website in browser.

Q3 — High Availability + Auto Scaling
main.tf for ALB, Target Group, Launch Template, Auto Scaling Group across private subnets.

user_data_nginx.sh reused for the web content.

screenshots/ for ALB config, Target group, ASG, instances.

Q4 — Billing & Free Tier Alerts
README gives manual steps for creating a CloudWatch Billing Alarm (EstimatedCharges) and enabling Free Tier usage alerts from the Billing Console.

screenshots/ folder contains Billing Alarm and Free Tier pages.

Q5 — Architecture Diagram
diagram.drawio and diagram.png illustrating a scalable architecture (ALB, ASG, RDS/Aurora, ElastiCache, Security Groups, WAF, CloudWatch).

Evidence & Screenshots
Each question folder contains a screenshots/ folder with the required console screenshots:

VPC, Subnets, Route Tables, NAT & IGW

EC2 instance, Security Groups, website screenshot

ALB, Target Group, ASG, instances

Billing alarm & Free Tier alerts

draw.io diagram exported as PNG

Security notes & best practices
Do not commit AWS credentials or sensitive data. Add terraform.tfvars to .gitignore if it contains secrets.

Use IAM roles for instances where possible (do not embed long-lived credentials).

Restrict SSH access to your IP (YOUR_IP/32) and prefer key-based SSH only.

Use terraform destroy to tear down resources and avoid unexpected billing.

Tag resources clearly with FirstName_Lastname_... to identify and remove them easily.

Cleanup checklist (must do after validation)
Delete EC2 instances and ASG.

Delete ALB and target groups.

Release Elastic IP used for NAT.

Delete NAT Gateway, internet gateway.

Delete subnets and VPC.

Confirm AWS Billing shows no active charge-generating resources.

Contact
If you find issues or want me to perform a repo review, share your GitHub repository URL and I will:

Review folder/file structure

Check for secrets and .gitignore

Validate Terraform usage and provide improvements

Suggest README / CI improvements

Good luck — Prakhar!

markdown
Copy code

---

# 2) Quick repository review checklist (use this to self-audit now)

1. **README** — clear, root README present (use the file above) and per-folder README for Q1–Q5.  
2. **Folder structure** — each question in a separate folder with `main.tf`, `README.md`, and a `screenshots/` folder.  
3. **No secrets committed** — verify no AWS keys, `.pem`, or `terraform.tfvars` with secrets. (`git grep -n "AKIA"`, check `.gitignore`)  
4. **Variables & docs** — `main.tf` should use `variables.tf` or clear `var` placeholders and instructions for replacement (YOUR_IP, vpc_id, etc.).  
5. **Replace placeholders** — Ensure placeholder names `FirstName_Lastname` are documented and instruct the reviewer to replace them before `apply`.  
6. **Screenshots present & named** — VPC, subnets, route tables, ALB, ASG, website screenshot, billing alarm, draw.io PNG.  
7. **Terraform best practices** — use `terraform fmt`, avoid hard-coded region or AMI where possible, provide `outputs.tf` for important IDs/IPs.  
8. **Cleanup instructions** — include `terraform destroy` commands and a cleanup checklist.  
9. **License & contact** — include a simple `LICENSE` (MIT) and `CONTRIBUTING.md` if required.  
10. **Commit history** — commits should be atomic and have meaningful messages (one feature per commit).  
11. **Optional CI** — add a GitHub Action to run `terraform fmt` or `tflint` on PRs.

---

If you want me to **review the repo now**, paste the GitHub repository URL (for example `https://github.com/yourusername/Prakhar_Bajpai_AWS_Assessment`) and I’ll inspect it and give a line-by-line checklist and suggested edits (README, terraform, security, screenshots, diagram, and final submission packaging).

Which do you want next — (A) I post the README directly to your repo (I’ll need access), (B) I review your repo now (paste link), or (C) anything else?






