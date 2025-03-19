# Terraform Infrastructure on DigitalOcean (GitHub)

## Overview

This project provides Infrastructure as Code (IaC) for provisioning resources on DigitalOcean using Terraform. It allows users to define and manage cloud infrastructure in a repeatable and scalable way. The repository is hosted on GitHub to enable version control and collaboration.

## Prerequisites

Before using this project, ensure you have the following:

- [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.
- A [DigitalOcean](https://www.digitalocean.com/) account.
- A DigitalOcean API token with write permissions.
- A GitHub account and repository for storing Terraform configurations.

## Setup

### 1. Clone the Repository

```sh
git clone https://github.com/Maxourius/terraform-digitalocean.git
mkdir terraform-digitalocean
cd terraform-digitalocean
```

### 2. Configure Environment Variables

Export your DigitalOcean API token as an environment variable:

```sh
export DO_PAT="your_personal_access_token"
```

This will make using it in subsequent commands easier and keep it separate from your code.

### 3. Initialize Terraform

Run the following command to initialize Terraform and download the necessary providers:

```sh
terraform init
```

### 4. Plan the Deployment

Check what changes Terraform will make before applying them:

```sh
    terraform plan \
      -var "do_token=${DO_PAT}" \
      -var "pvt_key=$HOME/.ssh/id_rsa" 
```
Warning: The terraform plan command supports an -out parameter to save the plan. However, the plan will store API keys, and Terraform does not encrypt this data. When using this option, you should explore encrypting this file if you plan to send it to others or leave it at rest for an extended period of time.

### 5. Apply the Configuration

Deploy the infrastructure to DigitalOcean:

```sh
    terraform apply \
      -var "do_token=${DO_PAT}" \
      -var "pvt_key=$HOME/.ssh/id_rsa"
```

### 6. Destroy the Infrastructure (if needed)

To tear down the infrastructure:

```sh
terraform destroy -auto-approve
```

## Terraform Configuration

This project typically includes:

- **Droplets** (Virtual Machines)
- **VPC** for network isolation
- **Load Balancer** for distributing traffic
- **Firewall** rules
- **Volumes** for persistent storage

## File Structure

```
terraform-digitalocean/
│── provider.tf   # Main Terraform configuration file
│── www-1.tf      # Variables used in Terraform
|── README.md     # Documentation
```

## Best Practices

- Use [Terraform Cloud](https://www.terraform.io/cloud) or remote backends for state management.
- Leverage modules to organize and reuse configurations.
- Store sensitive data securely using Terraform variables and GitHub Secrets.
- Follow DigitalOcean best practices for security and performance.

## Troubleshooting

If you encounter issues:

- Verify your DigitalOcean API token is correct.
- Ensure Terraform is properly installed and updated.
- Check for any quota limits in your DigitalOcean account.
- Run `terraform validate` to check for syntax errors.

## Resources

- [Terraform DigitalOcean Provider](https://registry.terraform.io/providers/digitalocean/digitalocean/latest/docs)
- [DigitalOcean API Documentation](https://docs.digitalocean.com/reference/api/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
