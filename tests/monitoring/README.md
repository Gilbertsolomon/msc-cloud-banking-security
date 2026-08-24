# Logging and Monitoring Tests

## MON-01 CloudFormation Deployment

**Objective:** Verify that the logging and monitoring CloudFormation stack deploys successfully.

**Expected result:** Stack `msc-logging-monitoring` reaches `CREATE_COMPLETE`.

**Observed result:** Stack `msc-logging-monitoring` reached `CREATE_COMPLETE`.

**Status:** PASS

## MON-02 CloudTrail Auditing

**Objective:** Verify that CloudTrail is actively recording audit activity.

**Expected result:** CloudTrail logging is `LOGGING`.

**Observed result:** CloudTrail logging was `LOGGING`.

**Status:** PASS

## MON-03 Log Integrity Validation

**Objective:** Verify that CloudTrail log-file validation is confirmed.

**Expected result:** CloudTrail log-file validation is independently verified as enabled.

**Observed result:** CloudTrail log-file validation was `NOT INDEPENDENTLY VERIFIED`.

**Status:** FAIL

## MON-04 CloudWatch Log Delivery

**Objective:** Verify that CloudTrail delivers logs to CloudWatch Logs.

**Expected result:** CloudWatch log delivery is confirmed.

**Observed result:** CloudWatch log delivery: `YES`.

**Status:** PASS

## MON-05 Controlled Authorisation Failure

**Objective:** Verify that a controlled unauthorised management action is generated and denied.

**Expected result:** A controlled denied action is generated, the request is not authorised, and the target user is not created.

**Observed result:** `msc-monitoring-test` attempted `iam:CreateUser` for `msc-should-fail`; AWS returned Access Denied / not authorised, and the target IAM user was not created.

**Status:** PASS

## MON-06 CloudTrail Event Detection

**Objective:** Verify that the denied action is visible in CloudTrail Event History.

**Expected result:** The denied action is visible in CloudTrail Event History.

**Observed result:** Denied action visible in CloudTrail Event History: `NO`.

**Status:** FAIL

## MON-07 Centralised CloudWatch Logging

**Objective:** Verify that the denied action is visible in the CloudWatch Logs group.

**Expected result:** The denied action is visible in the CloudWatch Logs group.

**Observed result:** Denied action visible in the CloudWatch Logs group: `NO`.

**Status:** FAIL

## MON-08 Security Metric Generation

**Objective:** Verify that an AccessDenied metric is generated for the controlled failure.

**Expected result:** The AccessDenied metric is generated.

**Observed result:** AccessDenied metric generated: `YES`.

**Status:** PASS

## MON-09 Alarm Detection

**Objective:** Verify that the AccessDenied alarm detects the security metric.

**Expected result:** The AccessDenied alarm reaches the expected alarm state.

**Observed result:** AccessDenied alarm final test state: `ALARM`.

**Status:** PASS

## MON-10 Temporary Identity Cleanup

**Objective:** Verify that the temporary monitoring test identity is removed after validation.

**Expected result:** `msc-monitoring-test` is deleted.

**Observed result:** Temporary identity `msc-monitoring-test` deleted: `YES`.

**Status:** PASS
