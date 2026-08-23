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

## Validation Results

The deployed network security controls were validated against three key configuration requirements:

1. **Public Subnet Routing:** The public subnet is associated with an explicit default route (`0.0.0.0/0`) through the attached Internet Gateway, enabling controlled Internet connectivity for public-facing resources.

2. **Private Subnet Isolation:** The private subnet has no direct route to the Internet Gateway, ensuring that resources deployed within the private network layer are not directly exposed to the public Internet.

3. **Private Application Access Control:** The private application security group permits application traffic on TCP port `8080` only from the approved public web security group, preventing direct public access to the private application layer.

Detailed validation procedures, observed results, and supporting evidence for these security controls are maintained under `tests/network/`.