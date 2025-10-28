# Advanced Examples

Complex, production-ready Infrastructure as Code examples demonstrating advanced patterns and best practices.

## Overview

This directory contains advanced examples suitable for experienced practitioners and those building production infrastructure.

## Contents

- **api_call.js**: GitHub Enterprise API integration example
- **azure_vm.yml**: Advanced Azure Virtual Machine deployment template
- **azuredeploy.json**: Production-grade ARM template with advanced features
- **main.tf**: Advanced Terraform configuration with modules and state management

## Examples

### GitHub Enterprise API Integration

Learn how to interact with GitHub Enterprise APIs for:
- Fetching user statistics
- Retrieving license information
- Analyzing active committers
- Custom reporting and auditing

**Usage**:
```bash
# Install dependencies
npm install axios

# Set GitHub token
export GITHUB_TOKEN="your_github_token"

# Run the script
node api_call.js
```

### Advanced Azure VM Deployment

Provisions a production-ready virtual machine with:
- Advanced networking configuration
- Security group rules
- Monitoring and diagnostics
- Custom extensions

### Production ARM Template

Full-featured ARM template including:
- Multiple resource types
- Cross-resource dependencies
- Parameter validation
- Output configuration

### Advanced Terraform Configuration

Demonstrates:
- Module composition
- Remote state management
- Variable validation
- Data source usage
- Complex resource dependencies

## Deployment Instructions

### Azure YAML Template

```bash
az deployment group create \
  --resource-group myResourceGroup \
  --template-file azure_vm.yml \
  --parameters \
    vmName=prodVM \
    location=eastus \
    vmSize=Standard_D2s_v3
```

### ARM Template

```bash
az deployment group create \
  --resource-group myResourceGroup \
  --template-file azuredeploy.json \
  --parameters azuredeploy.parameters.json
```

### Terraform

```bash
# Initialize with remote backend
terraform init -backend-config="key=prod/terraform.tfstate"

# Plan with variables
terraform plan -var="environment=production"

# Apply with auto-approval (use with caution)
terraform apply -auto-approve
```

## Best Practices Demonstrated

- **Security**: Secrets management, least-privilege access
- **Scalability**: Modular design, reusable components
- **Maintainability**: Clear variable naming, documentation
- **Reliability**: Error handling, validation
- **Auditability**: Logging, state tracking

## Performance Considerations

- Resource creation order optimization
- Parallel deployment where possible
- State file management for large deployments
- Network performance tuning

## Cost Optimization

- Resource right-sizing
- Auto-shutdown configurations
- Reserved instances consideration
- Storage optimization

## Troubleshooting

### Common Issues

**API Rate Limiting**:
- Implement exponential backoff
- Use pagination for large datasets
- Consider caching

**Deployment Timeouts**:
- Increase timeout thresholds
- Check resource quotas
- Review dependency chains

**State Management Issues**:
- Backup state files regularly
- Use state locking for team deployments
- Monitor for state drift

## Support

For advanced questions and issues:
1. Review official provider documentation
2. Check GitHub issues in relevant repositories
3. Consult with infrastructure architects
4. See CONTRIBUTING.md for reporting
