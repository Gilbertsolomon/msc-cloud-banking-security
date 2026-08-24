# 06 - Logging and Monitoring

## Purpose

This module provides security auditing, centralised log delivery, metric generation, and alerting for the MSc cloud-banking security project.

## CloudTrail Audit Architecture

AWS CloudTrail records management activity and delivers audit logs to a dedicated S3 archive. The archive uses SSE-S3 encryption, Block Public Access, `BucketOwnerEnforced` object ownership, and a `DenyInsecureTransport` policy. CloudTrail log-file validation is enabled in the template.

## CloudWatch Monitoring

CloudTrail also delivers events to a dedicated CloudWatch Logs group through an IAM delivery role. An `AccessDenied` metric filter detects authorisation failures, and the AccessDenied alarm evaluates that metric for alerting.

## Controlled Validation Methodology

Validation used a controlled denied management action from the temporary identity `msc-monitoring-test`. The identity attempted `iam:CreateUser` for `msc-should-fail`; AWS returned Access Denied / not authorised, and the target IAM user was not created. The resulting audit and monitoring observations were recorded without assuming event correlation where it was not observed.

## Verified Results

- CloudFormation status for `msc-logging-monitoring`: `CREATE_COMPLETE`
- CloudTrail logging: `LOGGING`
- CloudTrail log-file validation: `NOT INDEPENDENTLY VERIFIED`
- CloudWatch log delivery: `YES`
- Controlled denied management action generated: `YES`
- Denied action visible in CloudTrail Event History: `NO`
- Denied action visible in the CloudWatch Logs group: `NO`
- AccessDenied metric generated: `YES`
- AccessDenied alarm final test state: `ALARM`
- Temporary identity `msc-monitoring-test` deleted: `YES`

### Controlled Action

- Test identity: `msc-monitoring-test`
- Attempted action: `iam:CreateUser`
- Target user: `msc-should-fail`
- AWS result: Access Denied / not authorised
- Target IAM user created: `NO`

## Limitations

CloudTrail log-file validation was not independently verified. The denied action was not visible in CloudTrail Event History or the CloudWatch Logs group during validation, although the AccessDenied metric was generated and the alarm reached `ALARM`.

## Cost-Conscious Design

The module uses short CloudWatch Logs retention and native CloudTrail, S3, CloudWatch Logs, metric-filter, and alarm capabilities for focused security monitoring.

## Cleanup

The temporary identity `msc-monitoring-test` was deleted after validation. Temporary monitoring resources will be removed according to the project cleanup procedure after evidence collection.
