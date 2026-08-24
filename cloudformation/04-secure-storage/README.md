# 04 - Secure Storage

## Purpose

This module provides a secure, cost-conscious Amazon S3 storage layer for simulated banking data.

## Security Architecture

The storage design combines explicit SSE-S3 encryption, S3 Block Public Access, `BucketOwnerEnforced` object ownership, versioning, and TLS-only access enforced by the `DenyInsecureTransport` bucket policy.

## Controls Implemented

- Default server-side encryption using SSE-S3 with AES-256
- S3 Block Public Access enabled
- Bucket ownership enforced with `BucketOwnerEnforced`
- Bucket versioning enabled
- Insecure transport denied through the `DenyInsecureTransport` bucket policy

Only synthetic data is used. No real customer, financial, or personally identifiable information is stored in this module.

## Validation Results

- CloudFormation stack `msc-secure-storage`: `CREATE_COMPLETE`
- S3 Block Public Access: `ON`
- Default bucket encryption: `SSE-S3 AES-256`
- Bucket versioning: `ENABLED`
- Object Ownership: `BUCKET OWNER ENFORCED`
- `DenyInsecureTransport` bucket policy: `PRESENT`
- Synthetic test-object encryption for `MSc Cloud Banking Security Prototype.txt`: `SSE-S3`
- Multiple versions of `MSc Cloud Banking Security Prototype.txt` created: `YES`

## Cost-Conscious Design

The module uses an S3 bucket with native security controls and does not introduce additional paid storage-security services. Validation uses a synthetic test object and avoids real banking data.

## Cleanup

After evidence collection, the temporary validation resources and test object versions will be removed according to the project cleanup procedure.
