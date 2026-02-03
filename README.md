# Terraform EC2 Demo

This project demonstrates how to provision an **AWS EC2 instance** manually and using **Terraform**, simulating a **real-time DevOps workflow**.

---

## Table of Contents

1. [Overview](#overview)  
2. [Folder Structure](#folder-structure)  
3. [Manual vs Terraform](#manual-vs-terraform)  
4. [Terraform Steps](#terraform-steps)  
5. [Commands Used](#commands-used)  
6. [Real-Time Scenario](#real-time-scenario)  
7. [Clean Up](#clean-up)  

---

## Overview

- **Goal:** Learn AWS core concepts and Terraform automation.  
- **Manual EC2:** Launching EC2 via AWS console.  
- **Terraform EC2:** Automating EC2 provisioning using Terraform configuration files.  
- **Skills Gained:** AWS EC2, Terraform, GitHub version control, DevOps workflow simulation.

---
## AWS Networking Details

While provisioning EC2 instances, the following AWS networking components were considered:

- **VPC (Virtual Private Cloud):** Default VPC is used to host EC2 instances.  
- **Subnet:** Instances are launched in a public subnet to allow SSH access.  
- **Security Group:** A security group was configured to allow:
  - SSH (port 22) from my IP  
  - HTTP/HTTPS (if required by application)  
- **Key Pair:** Used to securely connect (SSH) to EC2 instance.  

Note: For simplicity, Terraform used AWS default VPC and subnet. In a real company scenario, you would create a separate VPC, custom subnets, and stricter security rules.

## Folder Structure
terraform-ec2-demo/
├── main.tf # Terraform configuration file
├── README.md # Project documentation
├── .gitignore # Ignore sensitive files
└── A_comparison_infographic_infographic_illustration_.png # Manual vs Terraform diagram


---

## Manual vs Terraform

### Diagram

![Manual vs Terraform](A_comparison_infographic_infographic_illustration_.png)

### Step-by-Step Comparison

| Manual Process                  | Terraform Process           |
|---------------------------------|----------------------------|
| Open AWS Console                 | Write `main.tf` code       |
| Login to AWS                     | Run `terraform init`       |
| Click Launch EC2                 | Run `terraform plan`       |
| Select AMI & Instance Type       | Run `terraform apply`      |
| Click Next / Configure           | EC2 automatically created |
| Click Launch                     | Check EC2 in AWS Console   |
| EC2 Running                      | EC2 Running                |
| Repeat manually for new EC2      | Repeat anytime (idempotent)|

---

## Terraform Steps

1. **Install Terraform** on EC2 or local machine  
2. **Configure AWS credentials** (IAM Role attached to EC2 or `aws configure`)  
3. Create `main.tf` with EC2 configuration  
4. Initialize Terraform:

```bash
--terraform init

5. review execution plan:

--terraform plan

6.Apply configuration to create EC2:

---terraform apply

 7.Verify EC2 instance in AWS console
 Commands Used
cd ~/terraform-ec2-demo
git init
git add .
git commit -m "Add Terraform EC2 demo with README and diagram"
git remote add origin https://github.com/urviumesh11-star/terraform-ec2-demo.git
git branch -M main
git push -u origin main

Real-Time Scenario
 Launch multiple EC2 instances for a new feature:
--2 EC2s for backend

--1 EC2 for Jenkins

Workflow:
Requirement → DevOps writes Terraform code → Push to GitHub → Review → terraform apply → EC2 ready

1.Fully automated
2.No manual clicks
3.State file ensures idempotency

Clean Up

To remove resources and avoid AWS charges:
--terraform destroy

Notes
.terraform/ and terraform.tfstate are ignored in Git
Only essential files (main.tf, README.md, diagram, .gitignore`) are pushed to GitHub







