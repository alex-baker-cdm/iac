# AWS Examples

Amazon Web Services (AWS) Infrastructure as Code examples using CloudFormation.

## Overview

This directory contains AWS CloudFormation templates for deploying and managing infrastructure on Amazon Web Services.

## Contents

- **aws_nginx_deployment.yml**: CloudFormation template for deploying Nginx on EC2

## AWS Nginx Deployment Example

### Description

This CloudFormation template automates the deployment of a production-ready Nginx web server on AWS, including:

- **VPC (Virtual Private Cloud)**: Custom VPC with configurable CIDR blocks
- **Public Subnet**: For internet-facing resources
- **Internet Gateway**: For external connectivity
- **Route Table**: Network routing configuration
- **Security Group**: Firewall rules for HTTP (80), HTTPS (443), and SSH (22)
- **EC2 Instance**: t2.micro instance with Nginx pre-installed
- **IAM Role**: Service-specific permissions and access control

### Prerequisites

1. **AWS Account**: Active AWS account with billing enabled
2. **EC2 KeyPair**: Pre-created EC2 KeyPair for SSH access
   ```bash
   # Create a new KeyPair (if needed)
   aws ec2 create-key-pair --key-name my-key-pair --query 'KeyMaterial' --output text > my-key-pair.pem
   chmod 400 my-key-pair.pem
   ```
3. **AWS CLI**: Version 2.x or later installed and configured
4. **IAM Permissions**: User must have CloudFormation, EC2, and IAM permissions

## Deployment Instructions

### Option 1: Using AWS CLI

```bash
# 1. Set variables
export STACK_NAME="nginx-deployment"
export KEY_PAIR="my-key-pair"
export REGION="us-east-1"

# 2. Validate template
aws cloudformation validate-template \
  --template-body file://aws_nginx_deployment.yml \
  --region $REGION

# 3. Create the stack
aws cloudformation create-stack \
  --stack-name $STACK_NAME \
  --template-body file://aws_nginx_deployment.yml \
  --parameters ParameterKey=KeyName,ParameterValue=$KEY_PAIR \
  --capabilities CAPABILITY_NAMED_IAM \
  --region $REGION

# 4. Monitor stack creation
aws cloudformation describe-stacks \
  --stack-name $STACK_NAME \
  --query 'Stacks[0].StackStatus' \
  --region $REGION

# 5. Wait for completion
aws cloudformation wait stack-create-complete \
  --stack-name $STACK_NAME \
  --region $REGION
```

### Option 2: Using AWS CloudFormation Console

1. Open AWS CloudFormation Console
2. Click "Create stack" → "With new resources (standard)"
3. Upload template file: `aws_nginx_deployment.yml`
4. Enter stack name: e.g., `nginx-deployment`
5. Specify EC2 KeyPair
6. Review and create
7. Wait for stack status: `CREATE_COMPLETE`

## Post-Deployment

1. **Get Instance IP**:
   ```bash
   aws ec2 describe-instances \
     --filters "Name=tag:Name,Values=nginx-instance" \
     --query 'Reservations[0].Instances[0].PublicIpAddress' \
     --output text
   ```

2. **SSH into Instance**:
   ```bash
   ssh -i my-key-pair.pem ec2-user@<PUBLIC_IP>
   ```

3. **Verify Nginx**:
   ```bash
   curl http://<PUBLIC_IP>
   ```

## Security Best Practices

1. **SSH Access**: Restrict SSH (port 22) to known IP addresses
2. **HTTPS**: Configure SSL/TLS certificates
3. **IAM Roles**: Use minimal required permissions
4. **Security Groups**: Further restrict traffic as needed
5. **VPC Flow Logs**: Enable for traffic monitoring

## Cleanup

```bash
# Delete the CloudFormation stack
aws cloudformation delete-stack \
  --stack-name nginx-deployment \
  --region us-east-1

# Wait for deletion
aws cloudformation wait stack-delete-complete \
  --stack-name nginx-deployment \
  --region us-east-1
```

## Resources

- [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)
- [AWS EC2 Best Practices](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-best-practices.html)
- [Nginx Documentation](https://nginx.org/en/docs/)

## Support

For issues or questions:
1. Review AWS documentation
2. Check AWS Support Center
3. See parent README.md for general guidance
4. Report issues via CONTRIBUTING.md
