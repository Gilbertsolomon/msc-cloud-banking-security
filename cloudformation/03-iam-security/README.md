# 03 - IAM Security

## Purpose

This module implements and validates least-privilege IAM controls for the MSc cloud-banking security project.

## Least-Privilege Design

The temporary `msc-banking-auditor` identity receives only the managed policy `MSc-Banking-Auditor-Policy`. The policy permits read-only inspection of selected Amazon EC2 networking and AWS CloudFormation resources; it does not grant administrative actions.

## Resources Implemented

- IAM managed policy: `MSc-Banking-Auditor-Policy`
- Temporary IAM user: `msc-banking-auditor`

No access keys or console credentials were created for the temporary auditor.

## Validation Methodology

Validation used IAM policy simulation for the authorised `ec2:DescribeVpcs` action and the unauthorised `ec2:DeleteVpc` action. The identity and policy attachment were also inspected directly. The privileged `msc-cloud-admin` identity had MFA enabled and validated earlier.

## Verified Results

- Restricted IAM identity created: `msc-banking-auditor`
- Attached policy: `MSc-Banking-Auditor-Policy`
- AdministratorAccess attached to restricted auditor: not provided
- Policy simulation `ec2:DescribeVpcs`: `ALLOWED`
- Policy simulation `ec2:DeleteVpc`: `DENIED`
- CloudFormation stack `msc-iam-security` status: not provided

## Cleanup Decision

The temporary auditor stack will be deleted after evidence collection.
