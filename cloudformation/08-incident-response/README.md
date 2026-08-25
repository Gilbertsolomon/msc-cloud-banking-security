# 08 - Incident Response

## Purpose

This module documents a controlled, automated incident-response workflow for the MSc cloud-banking security project.

## Event-Driven Architecture

Amazon EventBridge receives security events and matches high-severity events. The enabled rule invokes an AWS Lambda response function. Lambda uses a least-privilege incident-response role to apply controlled research tags to the existing banking VPC.

The role permits only the required tag operations on the supplied VPC resource and includes the standard Lambda logging policy. The response is deliberately non-destructive: it applies `IncidentStatus` and `IncidentSource` tags rather than modifying, deleting, or isolating production resources.

## Validation Methodology

Validation used synthetic EventBridge `PutEvents` submissions. A low-severity event acted as a negative control and did not trigger containment. A high-severity event acted as the positive-response test and triggered the Lambda tagging response. No real cyberattack was performed, and no destructive containment operation was performed.

## Verified Results

- CloudFormation status: `CREATE_COMPLETE`
- EventBridge rule enabled: `YES`
- Low-severity `PutEvents` result: `SUCCESS`
- Low-severity containment tag result: `NO`
- High-severity `PutEvents` result: `SUCCESS`
- `IncidentStatus` after the high-severity event: `Quarantined-Test`
- `IncidentSource` after the high-severity event: `MSc-Synthetic-Security-Event`
- Lambda response log generated: `YES`
- Lambda invocation successful: `YES`
- Test containment tags removed after validation: `NOT YET VERIFIED`

The verified Lambda response was:

```text
response: containment-tag-applied
event_id: IR-TEST-HIGH-001
severity: High
```

The Lambda execution also produced `START`, `END`, and `REPORT` records in the `/aws/lambda/MSc-Banking-Incident-Response` CloudWatch log group.

## Research Data and Scope

The security event was synthetic. The quarantine mechanism was a controlled research tagging operation rather than a production containment procedure. No real customer data or production banking system was used.

## Cost-Conscious Design

The workflow uses serverless EventBridge and Lambda resources with short execution settings and no dedicated compute infrastructure. The containment test uses reversible tags rather than destructive actions.

## Rollback and Cleanup

The temporary `IncidentStatus` and `IncidentSource` tags are intended to be removed after validation. Their removal was not yet verified. Future deployments can be rolled back by deleting the CloudFormation stack after evidence collection.

## Limitations

This validation used synthetic events and a reversible research tag, so it does not demonstrate response to a real cyberattack or production incident. The low-severity event did not produce containment tags, and removal of the high-severity test tags remains not yet verified.
