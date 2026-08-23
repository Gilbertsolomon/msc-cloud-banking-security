# 02 - Network Security

## Purpose

This module extends the network foundation of the cloud-banking prototype by implementing controlled Internet routing, private subnet isolation and security-group boundaries.

## Infrastructure as Code

The resources are provisioned using AWS CloudFormation. The template is available in `network-security.yaml`.

## Security Objectives

- Establish a controlled public entry network.
- Prevent direct Internet routing from the private subnet.
- Separate public and private routing.
- Restrict communication using security groups.
- Maintain reproducibility through AWS CloudFormation.

## Implemented Controls

- Internet Gateway
- Public route table
- Public default route
- Public subnet route-table association
- Private route table
- Private subnet route-table association
- Public web security group
- Private application security group

## Cost Control

No NAT Gateway is deployed in this module.

## Validation

The implementation is validated using:

- AWS route-table associations
- Internet Gateway attachment
- Security-group rules
- The VPC resource map