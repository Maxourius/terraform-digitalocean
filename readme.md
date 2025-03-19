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
git clone https://github.com/your-repo/terraform-digitalocean.git
cd terraform-digitalocean
```

### 2. Configure Environment Variables

Export your DigitalOcean API token as an environment variable:

```sh
export DIGITALOCEAN_TOKEN="your_api_token_here"
```

Alternatively, you can define it in a Terraform variables file.

### 3. Initialize Terraform

Run the following command to initialize Terraform and download the necessary providers:

```sh
terraform init
```

### 4. Plan the Deployment

Check what changes Terraform will make before applying them:

```sh
terraform plan
```

### 5. Apply the Configuration

Deploy the infrastructure to DigitalOcean:

```sh
terraform apply -auto-approve
```

### 6. Destroy the Infrastructure (if needed)

To tear down the infrastructure:

```sh
terraform destroy -auto-approve
```

## GitHub Integration

### Storing Terraform Configurations in GitHub

- Commit your Terraform files to a GitHub repository for version control.
- Use `.gitignore` to exclude sensitive files like `terraform.tfstate`.
- Create a GitHub Actions workflow to automate Terraform deployments.

### Example GitHub Actions Workflow

```yaml
name: Terraform Deployment
on:
  push:
    branches:
      - main
jobs:
  terraform:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Setup Terraform
        uses: hashicorp/setup-terraform@v2
      - name: Initialize Terraform
        run: terraform init
      - name: Plan Terraform Changes
        run: terraform plan
      - name: Apply Terraform Changes
        run: terraform apply -auto-approve
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
│── main.tf          # Main Terraform configuration file
│── variables.tf     # Variables used in Terraform
│── outputs.tf       # Output values
│── provider.tf      # Provider configuration
│── terraform.tfvars # User-specific variable values
│── .github/workflows/terraform.yml # GitHub Actions workflow
└── README.md        # Documentation
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

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

[Your Name](https://github.com/your-github-profile)

