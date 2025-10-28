# Infrastructure as Code Examples

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Repository](https://img.shields.io/badge/GitHub-nolecram%2Fiac_examples-blue)](https://github.com/nolecram/iac_examples)
[![Last Updated](https://img.shields.io/badge/Last%20Updated-Oct%202025-brightgreen)](#)

A comprehensive collection of Infrastructure as Code (IaC) examples and templates for AWS, Azure, and Terraform. This repository demonstrates best practices for deploying and managing cloud infrastructure using modern IaC tools.

## Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Examples](#examples)
  - [AWS Examples](#aws-examples)
  - [Azure Examples](#azure-examples)
  - [Terraform Examples](#terraform-examples)
- [Environment Configuration](#environment-configuration)
- [Getting Started](#getting-started)
- [Contributing](#contributing)
- [Resources](#resources)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Overview

This repository provides practical examples and templates for:

- **AWS Infrastructure**: CloudFormation templates for deploying containerized applications and services
- **Azure Infrastructure**: ARM templates and YAML configurations for Azure resource deployment
- **Terraform**: Infrastructure definitions for multi-cloud environments
- **Automation**: JavaScript utilities for API interactions and custom deployment tasks

## Repository Structure

```
.
├── README.md                      # Main documentation
├── LICENSE                        # MIT License
├── CONTRIBUTING.md                # Contribution guidelines
├── .env.example                   # Environment variables template
├── .gitignore                     # Git ignore rules
├── Basic/                         # Basic infrastructure examples
│   ├── README.md
│   ├── azure_vm.yml              # Azure VM basic template
│   ├── azuredeploy.json          # Azure ARM template
│   ├── main.tf                   # Terraform configuration
│   └── server.js                 # Node.js server automation
├── Examples/                      # Advanced examples
│   ├── README.md
│   ├── api_call.js               # GitHub API integration example
│   ├── azure_vm.yml              # Advanced Azure VM template
│   ├── azuredeploy.json          # Advanced ARM template
│   └── main.tf                   # Advanced Terraform configuration
├── AWS/                           # AWS-specific examples
│   ├── README.md
│   └── aws_nginx_deployment.yml  # Nginx deployment on AWS
├── custom_api.js                 # Custom API utilities
└── terraform.json                # Terraform configuration reference
```

## Prerequisites

Before using the examples in this repository, ensure you have the following installed:

### AWS Examples
- AWS CLI (version 2.x or later)
- AWS account with appropriate IAM permissions
- CloudFormation knowledge

### Azure Examples
- Azure CLI or Azure PowerShell
- Azure subscription with active credentials
- Resource Group pre-created in your Azure account

### Terraform Examples
- Terraform (version 1.0 or later)
- Cloud provider CLI (AWS CLI or Azure CLI)
- `.tfvars` file with your configuration variables

### JavaScript Examples
- Node.js (version 14.x or later)
- npm or yarn package manager
- Required: `axios` package (`npm install axios`)

## Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/nolecram/iac_examples.git
   cd iac_examples
   ```

2. **Set up environment variables**:
   ```bash
   cp .env.example .env
   # Edit .env with your credentials
   source .env
   ```

3. **Navigate to your desired example**:
   ```bash
   cd Basic    # For basic examples
   # or
   cd AWS      # For AWS examples
   # or
   cd Examples # For advanced examples
   ```

4. **Deploy infrastructure**:
   - See specific directory README for deployment instructions

## Examples

### AWS Examples

AWS CloudFormation templates for deploying modern infrastructure on AWS.

**Key Example: Nginx Deployment**
- Template: `AWS/aws_nginx_deployment.yml`
- Deploys: VPC, Security Group, EC2 instance with Nginx
- Prerequisites: AWS account and EC2 KeyPair

See `AWS/README.md` for detailed instructions.

### Azure Examples

Azure Resource Manager (ARM) templates and YAML configurations.

**Available Examples**:
- Virtual Machine deployment
- Advanced resource templates

Available in both `Basic/` and `Examples/` directories. See respective README files.

### Terraform Examples

Terraform configurations for infrastructure management.

**Available Examples**:
- Azure resource group and networking
- Infrastructure variables and outputs

Available in both `Basic/` and `Examples/` directories.

## Environment Configuration

Sensitive information is managed through environment variables for security. Create a `.env` file based on `.env.example`:

```bash
# GitHub Enterprise API
export GITHUB_TOKEN="your-github-personal-access-token"

# Microsoft APIs
export ACCESS_TOKEN="your-access-token-for-microsoft-dynamics"

# AWS Credentials (if not using AWS CLI configuration)
export AWS_ACCESS_KEY_ID="your-aws-access-key"
export AWS_SECRET_ACCESS_KEY="your-aws-secret-key"
export AWS_DEFAULT_REGION="us-east-1"

# Azure Credentials
export AZURE_SUBSCRIPTION_ID="your-subscription-id"
export AZURE_RESOURCE_GROUP="your-resource-group"
```

**⚠️ Security Note**: Never commit `.env` files to version control. Use `.env.example` as a template.

## Getting Started

### For AWS Deployments

1. Navigate to the `AWS/` directory
2. Ensure you have an EC2 KeyPair created
3. Review `aws_nginx_deployment.yml` for parameters
4. Deploy using AWS CLI or CloudFormation console

See `AWS/README.md` for complete instructions.

### For Azure Deployments

1. Choose between `Basic/` or `Examples/` directory
2. Review the ARM template or YAML configuration
3. Deploy using Azure CLI:
   ```bash
   az group create --name myResourceGroup --location eastus
   az deployment group create --resource-group myResourceGroup \
     --template-file azuredeploy.json
   ```

### For Terraform Deployments

1. Navigate to the desired directory
2. Initialize Terraform:
   ```bash
   terraform init
   ```
3. Review the plan:
   ```bash
   terraform plan
   ```
4. Apply the configuration:
   ```bash
   terraform apply
   ```

### For JavaScript Examples

1. Install dependencies:
   ```bash
   npm install
   ```
2. Set environment variables
3. Run the script:
   ```bash
   node custom_api.js
   ```

## Contributing

We welcome contributions! Please see `CONTRIBUTING.md` for guidelines on how to:

- Report issues
- Submit pull requests
- Follow coding standards
- Document your changes

## Resources

Useful documentation and links:

- [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)
- [Azure Resource Manager Templates](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/)
- [Terraform Documentation](https://www.terraform.io/docs/)
- [Infrastructure as Code Best Practices](https://en.wikipedia.org/wiki/Infrastructure_as_code)
- [Node.js Documentation](https://nodejs.org/en/docs/)

## Troubleshooting

### AWS Issues

**Problem**: `An error occurred (ValidationError)`
- **Solution**: Verify EC2 KeyPair exists and CloudFormation parameters are correct

**Problem**: Insufficient IAM permissions
- **Solution**: Ensure your AWS user has CloudFormation, EC2, and IAM permissions

### Azure Issues

**Problem**: Authentication fails
- **Solution**: Run `az login` and verify subscription with `az account show`

**Problem**: Resource deployment timeout
- **Solution**: Check resource group limits and quotas in Azure Portal

### Terraform Issues

**Problem**: `Error acquiring the state lock`
- **Solution**: Remove `.terraform.lock.hcl` and reinitialize

**Problem**: Provider authentication failed
- **Solution**: Verify credentials in `.env` file and provider configuration

### API Issues

**Problem**: `401 Unauthorized` on API calls
- **Solution**: Verify tokens in `.env` file are valid and not expired

**Problem**: Rate limiting errors
- **Solution**: Wait before retrying or implement exponential backoff

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

---

**Last Updated**: October 2025  
**Maintainer**: [@nolecram](https://github.com/nolecram)  
**Repository**: [github.com/nolecram/iac_examples](https://github.com/nolecram/iac_examples)
