# Control Traceability

## Security Control Traceability

## Purpose

This matrix traces security requirements through implemented controls and the integrated evaluation scenarios using existing module evidence only.

## Preventive Controls

- Network Security restricts communication paths and supports segmentation and isolation.
- IAM restricts who can perform actions through least-privilege permissions.
- Data Protection protects stored information through private-access controls, encryption, and versioning.
- Secure Compute provides controlled workload execution within a private security boundary.

## Detective Controls

- Monitoring provides visibility into unauthorised activity through CloudTrail, CloudWatch Logs, metric filters, and alarms.
- Threat Detection represents the proposed higher-level finding capability through GuardDuty; practical validation was constrained by account and service-access limitations.

## Responsive Controls

- Incident Response automatically responds to qualifying synthetic events through EventBridge and Lambda using a controlled research tag.

## Control-to-Test Mapping

| Threat/security requirement | Security layer | Implemented AWS control | Evaluation scenario | Observed result | Status |
|---|---|---|---|---|---|
| Network intrusion/lateral movement | Network Security | Public/private subnet segmentation and associated route/security controls | EV-01 | MSc-Banking-VPC used the intended public/private segmentation and associated controls | PASS |
| Credential/privilege misuse | IAM | Least-privilege IAM policy and restricted test identity | EV-02 | Privileged administrative operations were denied; the temporary test identity was subsequently deleted | PASS |
| Data exposure | Data Protection | Private S3 access controls, encryption, and versioning | EV-03 | Simulated banking-data storage protections were validated | PASS |
| Workload exposure | Secure Compute | Private Lambda workload placement and controlled execution | EV-04 | Synthetic Lambda execution completed successfully within the intended private boundary | PASS |
| Undetected unauthorised activity | Monitoring | CloudTrail, CloudWatch Logs, AccessDenied metric filter, and alarm | EV-05 | Metric/alarm detection succeeded, but the complete CloudTrail/CloudWatch evidence chain was not demonstrated | PARTIAL |
| Threat identification | Threat Detection | Proposed GuardDuty finding capability | EV-06 | GuardDuty activation and sample-finding validation were constrained by account/free-plan service access; no findings were generated | PARTIAL |
| Delayed/manual response | Incident Response | EventBridge high-severity rule and Lambda research-tag response | EV-07 | Low severity did not trigger containment; high severity invoked Lambda and applied the Quarantined-Test tag | PASS |

## Evidence Mapping

Evidence is mapped to existing repository paths without invented screenshot or figure numbers:

- EV-01: `cloudformation/02-network-security/` and `cloudformation/03-iam-security/`
- EV-02: `cloudformation/03-iam-security/` and `cloudformation/06-logging-monitoring/`
- EV-03: `cloudformation/04-secure-storage/`
- EV-04: `cloudformation/05-secure-compute/`
- EV-05: `cloudformation/06-logging-monitoring/` and `tests/monitoring/`
- EV-06: `cloudformation/07-threat-detection/` and `tests/threat-detection/`
- EV-07: `cloudformation/08-incident-response/` and `tests/incident-response/`

## Traceability Limitations

Traceability is limited to the existing experimental evidence and documentation. The prototype uses synthetic or simulated data, a single AWS account and Region, limited scale, no production banking system, and no real malicious activity. GuardDuty was not practically validated because account/free-plan service access was constrained. Monitoring did not independently demonstrate the complete CloudTrail/CloudWatch evidence chain for the denied event. Incident response was validated with synthetic events and a non-destructive research tag rather than production network quarantine.
