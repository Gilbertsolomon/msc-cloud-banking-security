# 07 - Threat Detection

## Purpose

This module documents the controlled evaluation of Amazon GuardDuty as a detective control for the MSc cloud-banking security project.

## GuardDuty Rationale

Amazon GuardDuty was considered as a managed threat-detection service that could identify suspicious activity and provide findings without requiring real malicious activity. GuardDuty is a detective control: it observes activity and reports potential threats rather than preventing the activity itself.

The intended validation method was to use AWS-generated sample findings, not to perform an actual attack or malicious activity.

## Cost-Safety Decision

The AWS console did not clearly confirm eligibility for the required 30-day GuardDuty free trial and instead displayed account/free-plan limitations. The project procedure required activation to stop when free-trial eligibility could not be clearly confirmed. GuardDuty activation was therefore intentionally stopped as a cost-control and risk-management decision.

This is an implementation constraint, not a confirmed technical failure of the GuardDuty service.

## Verified Results

- GuardDuty enabled: `NO`
- GuardDuty 30-day free trial confirmed: `NO`
- Sample findings generated: `NO`
- Sample findings visible: `NO`
- Selected finding type: `NOT TESTED`
- Selected finding severity: `NOT TESTED`
- Affected resource category visible: `NO`
- Sample metadata confirmed: `NO`
- Finding filtering/investigation completed: `NO`
- No real malicious activity was performed.
- No production banking resources or genuine customer data were used.

GuardDuty sample findings were not generated. No actual attack activity was performed and no real compromise occurred. No customer, financial, or personally identifiable information was used.

## Validated Detective-Control Implementation

The existing CloudTrail and CloudWatch monitoring layer remains the validated detective-control implementation for this project. It provides audit logging, centralised log delivery, AccessDenied metric generation, and alerting without requiring GuardDuty activation.

## Limitations

GuardDuty activation was not executed because free-trial eligibility was not clearly confirmed. Consequently, sample finding generation, finding visibility, finding type, severity, metadata, and filtering/investigation were not tested. The affected resource category and sample metadata were not confirmed.

## Future Work

Validate GuardDuty in an account where cost approval and free-trial eligibility are explicitly confirmed, using AWS-generated sample findings only.

## Cleanup and Resource Decision

No GuardDuty detector or sample findings were created during this controlled experiment. No GuardDuty cleanup was required. Any future validation resources should be removed after evidence collection according to the project cleanup procedure.
