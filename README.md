# Production-Level-EKS-Clusters-with-Terraform-and-GitHub-Actions

# Overview

This repository demonstrates the practical steps to set up and automate an EKS cluster.

 - Infrastructure as Code (IaC): Use Terraform to define and manage your EKS cluster.
 - CI/CD Automation: Leverage GitHub Actions to automate deployments.

# Architecture
![EKS](https://github.com/user-attachments/assets/7b1ed61b-7295-4d3d-a22e-e0dfd61d8c29)

## Directory Structure

```bash
EKS-Terraform-GitHub-Actions/
├── .github/
│   └── workflows/
│       └── terraform.yml
├── eks/
│   ├── main.tf
│   ├── variables.tf
│   ├── backend.tf
│   └── dev.tfvars
├── module/
│   ├── eks.tf
│   ├── gather.tf 
│   ├── iam.tf  
│   ├── variables.tf  
│   ├── vpc.tf         
└── README.md
```
# GitHub Actions for CI/CD

## terraform-ci.yml (Runs on PRs)
•	Formats and validates Terraform code.

•	Runs security checks with tfsec and checkov.

## terraform-deploy.yml (Runs on merge to main)
•	Applies Terraform changes automatically.

•	Ensures infrastructure is always in sync with the repository.

# Security Best Practices
- Remote state storage: Uses backend.tf to store Terraform state securely in S3/Azure Storage.
- IAM Role Authentication: Uses OIDC for GitHub Actions instead of storing AWS credentials.
- Automated security checks: tfsec & checkov scan Terraform for misconfigurations.
- Least privilege access: Follows the Principle of Least Privilege for Terraform IAM roles.
