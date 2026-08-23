# Multi-Layer Defence Architecture for Cloud-Based Banking

## Project Overview

This repository contains the technical implementation supporting an MSc Cloud and Network Security dissertation investigating a multi-layer defence architecture for mitigating customer data breaches in cloud-based banking systems.

The prototype is implemented in Amazon Web Services (AWS), with AWS CloudFormation used as Infrastructure as Code (IaC) to support reproducibility and configuration consistency.

## Security Architecture

The proposed architecture integrates six security layers:

1. Identity and Access Management
2. Data Protection
3. Network Security
4. Continuous Monitoring and Detection
5. Incident Response
6. Governance, Risk and Compliance

## Repository Structure

- `cloudformation/` - AWS infrastructure templates
- `architecture/` - architecture diagrams
- `tests/` - controlled security testing artefacts
- `evidence/` - sanitised implementation evidence
- `docs/` - supporting technical documentation

## Security Notice

No real banking customer information, AWS credentials, passwords, access keys, MFA secrets or production data are stored in this repository. All experimental data used within the prototype is synthetic.