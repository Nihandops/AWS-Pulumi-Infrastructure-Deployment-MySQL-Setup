# AWS-Pulumi-Infrastructure-Deployment-MySQL-Setup

# AWS Hands-On Exam Solution with Pulumi

This project implements the infrastructure for the AWS Hands-On Exam using Pulumi with Python.

## Prerequisites

1. Install Pulumi: https://www.pulumi.com/docs/get-started/install/
2. Install AWS CLI: https://aws.amazon.com/cli/
3. Configure AWS credentials: `aws configure`
4. Install Python 3.7+

## Setup

1. Clone this repository
2. Create a virtual environment: `python -m venv venv`
3. Activate the virtual environment:
   - On Windows: `venv\Scripts\activate`
   - On Unix/MacOS: `source venv/bin/activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Copy `Pulumi.dev.yaml.example` to `Pulumi.dev.yaml`
6. Configure your settings in `Pulumi.dev.yaml`:
   - Set your SSH public key
   - Set your public IP address

## Deployment

1. Initialize the Pulumi stack: `pulumi stack init dev`
2. Preview the deployment: `pulumi preview`
3. Deploy the infrastructure: `pulumi up`
4. After deployment, note the outputs (bastion public IP, private instance private IP)

## Validation

1. SSH to the bastion host: `ssh -J ops@<bastion-ip> ec2-user@<private-ip>`
2. From the private instance, test internet connectivity: `curl https://aws.amazon.com`
3. Test MySQL connection from bastion: `mysql -h <private-ip> -u appuser -p -e "SELECT 1;"`

## Cleanup

1. Destroy all resources: `pulumi destroy`
2. Remove the stack: `pulumi stack rm dev`

