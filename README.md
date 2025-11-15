# ASG-PrettySite-Route53

A small but powerful AWS project that proves I can build a **highly available web app with Terraform**, wire it up to a **custom domain**, and make it actually look good on the front end.

The stack includes:

- **VPC** with public + private subnets across multiple AZs  
- **Internet Gateway + NAT Gateway**
- **Application Load Balancer (ALB)**
- **Auto Scaling Group (ASG)** with a Launch Template
- **Route 53** alias record pointing a real domain to the ALB
- A **pretty HTML/CSS landing page** that shows live EC2 metadata (private IP, AZ, VPC ID, etc.)

Live example (for this practice run):  
`http://app.tawanperry.top` (domain managed through Porkbun + Route 53)

---

## Architecture Overview

**Network**

- One **VPC** in `us-east-1`
- **Public subnets** in 3 AZs for:
  - Application Load Balancer  
  - NAT Gateway
- **Private subnets** in 3 AZs for:
  - EC2 instances managed by the Auto Scaling Group
- **Internet Gateway** attached to the VPC
- **NAT Gateway** in a public subnet so private instances can reach the internet for updates

**Compute & Load Balancing**

- **Launch Template**:
  - Amazon Linux 2023 (`t2.micro`)
  - Installs **Apache (httpd)**
  - Uses **IMDSv2** to pull EC2 metadata (IP, AZ, VPC ID, etc.)
  - Generates a styled `index.html` under `/var/www/html/`

- **Auto Scaling Group (ASG)**:
  - Uses the Launch Template
  - Spreads instances across multiple private subnets / AZs
  - Desired capacity can be adjusted (e.g., 2 instances)

- **Application Load Balancer (ALB)**:
  - Placed in public subnets
  - Listens on HTTP (port 80)
  - Forwards traffic to a **Target Group** with the ASG instances
  - Health checks to keep only healthy instances in rotation

**DNS / Route 53**

- **Public hosted zone** in Route 53 for the domain  
- **Alias A record**:
  - Name: `app.tawanperry.top`
  - Target: ALB DNS name (alias, not a CNAME)
- Registrar (Porkbun) delegates the domain to the Route 53 name servers.

---

## Repo Structure

```text
ASG-PrettySite-Route53/
├── index.html          # Standalone version of the pretty HTML page
├── style.css           # Standalone CSS file for the landing page
└── terraform/
    ├── 0-auth.tf
    ├── 1-vpc.tf
    ├── 2-subnets.tf
    ├── 3-igw.tf
    ├── 4-nat.tf
    ├── 5-route.tf
    ├── 6-sg01-all.tf
    ├── 7-launchtemplate.tf
    ├── 8-targetgroup.tf
    ├── 9-loadbalancer.tf
    ├── 10-autoscalinggroup.tf
    ├── 11-route53.tf
    ├── variables-route53.tf
    ├── terraform.tfvars        # (gitignored or example in repo)
    └── terraform.tfstate*      # (never committed)
