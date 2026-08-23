# IAM Security Tests

## IAM-01 Restricted Policy Assignment

**Objective:** Verify that the restricted auditor identity was created and assigned the intended policy.

**Expected result:** The `msc-banking-auditor` identity exists and has `MSc-Banking-Auditor-Policy` attached, with no `AdministratorAccess` attached.

**Observed result:** `msc-banking-auditor` was created and `MSc-Banking-Auditor-Policy` was attached. The `AdministratorAccess` result was not provided.

**Status:** FAIL

## IAM-02 Authorised DescribeVpcs Action

**Objective:** Verify that the restricted policy permits read-only VPC inspection.

**Expected result:** Policy simulation for `ec2:DescribeVpcs` returns `ALLOWED`.

**Observed result:** Policy simulation for `ec2:DescribeVpcs` returned `ALLOWED`.

**Status:** PASS

## IAM-03 Denied DeleteVpc Action

**Objective:** Verify that the restricted policy denies destructive VPC deletion.

**Expected result:** Policy simulation for `ec2:DeleteVpc` returns `DENIED`.

**Observed result:** Policy simulation for `ec2:DeleteVpc` returned `DENIED`.

**Status:** PASS
