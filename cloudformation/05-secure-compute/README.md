# 05 - Secure Compute

## Purpose

This module deploys a secure serverless compute workload for the MSc cloud-banking security project.

## Serverless Compute Design

The workload uses AWS Lambda to process a synthetic banking request without managing servers. Lambda is appropriate for this prototype because it provides an event-driven execution model, integrates with CloudWatch logging, and supports controlled VPC placement.

The function is attached to the existing private subnet and private application security group. Its execution role provides the permissions required for Lambda execution and VPC networking through the AWS-managed execution policies assigned by the template.

## Data Handling

Only synthetic data was used. No real customer or financial data was used.

## Validation Results

- CloudFormation stack `msc-secure-compute`: `CREATE_COMPLETE`
- Lambda function: `MSc-Banking-Prototype-Function`
- VPC: `MSc-Banking-VPC`
- Subnet: `MSc-Private-Subnet`
- Security group: `MSc-Private-App-SG`
- IAM execution role assigned: `YES`
- Synthetic request execution: `SUCCEEDED`
- Lambda response status code: `200`
- CloudWatch log event generated: `YES`

## Cost-Conscious Design

The module uses serverless Lambda execution with a small memory allocation and short timeout for the synthetic validation workload. It avoids provisioning dedicated compute instances for the prototype.

## Cleanup

After evidence collection, the `msc-secure-compute` CloudFormation stack and its temporary validation resources will be deleted according to the project cleanup procedure.
