# Secure Compute Tests

## CP-01 CloudFormation Deployment

**Objective:** Verify that the secure compute CloudFormation stack deploys successfully.

**Expected result:** Stack `msc-secure-compute` reaches `CREATE_COMPLETE`.

**Observed result:** Stack `msc-secure-compute` reached `CREATE_COMPLETE`.

**Status:** PASS

## CP-02 Private VPC Placement

**Objective:** Verify that the Lambda workload is deployed within the intended banking VPC.

**Expected result:** The function is associated with `MSc-Banking-VPC`.

**Observed result:** The VPC result was `MSc-Banking-VPC`.

**Status:** PASS

## CP-03 Private Subnet Placement

**Objective:** Verify that the Lambda workload is placed in the intended private subnet.

**Expected result:** The function is associated with `MSc-Private-Subnet`.

**Observed result:** The subnet result was `MSc-Private-Subnet`.

**Status:** PASS

## CP-04 Security Group Boundary

**Objective:** Verify that the Lambda workload uses the intended private application security group.

**Expected result:** The function is associated with `MSc-Private-App-SG`.

**Observed result:** The security group result was `MSc-Private-App-SG`.

**Status:** PASS

## CP-05 Execution Role Assignment

**Objective:** Verify that an IAM execution role is assigned to the Lambda function.

**Expected result:** An IAM execution role is assigned.

**Observed result:** IAM execution role assigned: `YES`.

**Status:** PASS

## CP-06 Synthetic Workload Invocation

**Objective:** Verify that the synthetic request executes successfully.

**Expected result:** Synthetic request execution succeeds.

**Observed result:** Synthetic request execution: `SUCCEEDED`.

**Status:** PASS

## CP-07 Successful Response

**Objective:** Verify that the Lambda function returns the expected successful response status.

**Expected result:** Lambda response status code is `200`.

**Observed result:** Lambda response status code was `200`.

**Status:** PASS

## CP-08 CloudWatch Log Generation

**Objective:** Verify that Lambda execution generates a CloudWatch log event.

**Expected result:** A CloudWatch log event is generated.

**Observed result:** CloudWatch log event generated: `YES`.

**Status:** PASS
