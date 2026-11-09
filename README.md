# Terraform: EC2 Web Server on AWS

Infrastructure as code for an Ubuntu EC2 instance running Nginx, behind a security group that allows HTTP only.
Codifies the manual EC2 + Nginx deployment from my [aws-ec2-nodejs-deployment](https://github.com/Temi-ee/aws-ec2-nodejs-deployment) project.

## What it creates
- Security group: inbound HTTP (80) only, no SSH exposed
- EC2 instance (t3.micro, latest Ubuntu 24.04 LTS AMI looked up dynamically)
- Nginx installed and started at boot via `user_data`

## Usage
```bash
terraform init
terraform plan
terraform apply
curl $(terraform output -raw url)
terraform destroy   # clean up
```

## Notes
- Deploys into the account's default VPC. State is local.
- Next steps: custom VPC with public/private subnets, S3 remote state, GitHub Actions `plan` on pull requests.
