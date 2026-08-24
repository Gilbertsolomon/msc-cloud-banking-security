# Secure Storage Tests

## ST-01 Public Access Protection

**Objective:** Verify that S3 public access is blocked.

**Expected result:** S3 Block Public Access is `ON`.

**Observed result:** S3 Block Public Access was `ON`.

**Status:** PASS

## ST-02 Encryption at Rest

**Objective:** Verify that default bucket encryption protects stored objects.

**Expected result:** Default bucket encryption is `SSE-S3 AES-256`.

**Observed result:** Default bucket encryption was `SSE-S3 AES-256`.

**Status:** PASS

## ST-03 Versioning

**Objective:** Verify that bucket versioning is enabled.

**Expected result:** Bucket versioning is `ENABLED`.

**Observed result:** Bucket versioning was `ENABLED`.

**Status:** PASS

## ST-04 Object Ownership

**Objective:** Verify that object ownership prevents ACL-based ownership ambiguity.

**Expected result:** Object Ownership is `BUCKET OWNER ENFORCED`.

**Observed result:** Object Ownership was `BUCKET OWNER ENFORCED`.

**Status:** PASS

## ST-05 Secure Transport Policy

**Objective:** Verify that insecure transport is denied by the bucket policy.

**Expected result:** The `DenyInsecureTransport` bucket policy is present.

**Observed result:** The `DenyInsecureTransport` bucket policy was `PRESENT`.

**Status:** PASS

## ST-06 Stored Object Encryption

**Objective:** Verify that the synthetic validation object is encrypted when stored.

**Expected result:** `MSc Cloud Banking Security Prototype.txt` uses `SSE-S3` encryption.

**Observed result:** `MSc Cloud Banking Security Prototype.txt` used `SSE-S3` encryption.

**Status:** PASS

## ST-07 Version Preservation

**Objective:** Verify that multiple versions of the synthetic validation object are preserved.

**Expected result:** Multiple versions of `MSc Cloud Banking Security Prototype.txt` are created.

**Observed result:** Multiple versions were created: `YES`.

**Status:** PASS
