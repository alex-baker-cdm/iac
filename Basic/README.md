# Basic Examples

Simple, introductory Infrastructure as Code examples for AWS, Azure, and Terraform.

## Overview

This directory contains foundational examples suitable for beginners and those learning Infrastructure as Code concepts.

## Contents

- **azure_vm.yml**: Basic Azure Virtual Machine deployment in YAML
- **azuredeploy.json**: ARM template for Azure resource deployment
- **main.tf**: Terraform configuration for basic infrastructure setup
- **server.js**: Node.js server automation script

## Quick Start

### Azure VM Deployment (YAML)

```bash
# Install Azure CLI (if not already installed)
curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Authenticate with Azure
az login

# Deploy the VM
az deployment group create \
  --resource-group myResourceGroup \
  --template-file azure_vm.yml \
  --parameters location=eastus vmName=basicVM
```

### Azure ARM Template

```bash
# Deploy using Azure CLI
az deployment group create \
  --resource-group myResourceGroup \
  --template-file azuredeploy.json

# Or using PowerShell
New-AzResourceGroupDeployment \
  -ResourceGroupName myResourceGroup \
  -TemplateFile azuredeploy.json
```

### Terraform

```bash
# Initialize Terraform
terraform init

# Review the plan
terraform plan

# Apply the configuration
terraform apply

# View outputs
terraform output
```

### Node.js Server Automation

```bash
# Install dependencies
npm install

# Run the server script
node server.js
```

## Prerequisites

- **Azure Examples**: Azure CLI or PowerShell, Active Azure subscription
- **Terraform**: Terraform installed, Cloud provider credentials configured
- **Node.js**: Node.js 22+ (LTS), npm installed

## Key Concepts

These examples demonstrate:

- Resource group creation and management
- Virtual machine provisioning
- Network configuration basics
- Variable usage and parameterization
- Infrastructure provisioning automation

## Next Steps

- Review the `Examples/` directory for more advanced patterns
- Check AWS examples for CloudFormation deployments
- Explore custom scripts and API integrations

## Support

For issues or questions:
1. Check parent README.md
2. Review official documentation links
3. See CONTRIBUTING.md for reporting issues
