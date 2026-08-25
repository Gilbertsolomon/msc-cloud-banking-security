# Proposed-to-Implemented Architecture Mapping

## Purpose

This document traces the proposed security objectives to the controls implemented and experimentally evaluated in Modules 01-09.

## Proposed Architecture

The proposed architecture comprises preventive network, IAM, storage, and compute controls; detective monitoring and GuardDuty capabilities; and automated incident response.

## Implemented Architecture

The practically validated prototype implemented network segmentation, IAM least privilege, protected S3 storage, private Lambda execution, CloudTrail/CloudWatch monitoring, and synthetic EventBridge/Lambda response. GuardDuty remained proposed and was not practically validated.

## Security-Control Mapping

| Security objective/threat | Security requirement | AWS implementation | Control classification | Module | Evaluation scenario | Validation result |
|---|---|---|---|---|---|---|
| Network intrusion/lateral movement | Separate public and private trust boundaries | VPC, public/private subnets, route tables, Internet Gateway, security groups | Preventive | 01-02 | EV-01 | PASS |
| Credential/privilege misuse | Restrict administrative actions to least privilege | IAM restricted identity and least-privilege policy | Preventive | 03 | EV-02 | PASS |
| Data exposure | Protect stored simulated banking data | S3 encryption, Block Public Access, ownership enforcement, versioning, TLS-only policy | Preventive | 04 | EV-03 | PASS |
| Workload exposure | Execute application workload inside a controlled boundary | Lambda in the private security boundary with IAM execution role | Preventive | 05 | EV-04 | PASS |
| Undetected unauthorised activity | Record and alert on AccessDenied activity | CloudTrail, S3 audit archive, CloudWatch Logs, metric filter, alarm | Detective | 06 | EV-05 | PARTIAL |
| Threat identification | Provide higher-level managed threat findings | Proposed GuardDuty component; practical activation constrained | Detective | 07 | EV-06 | PARTIAL |
| Delayed/manual response | Respond selectively to qualifying security events | EventBridge high-severity rule and Lambda research-tag response | Responsive/Corrective | 08 | EV-07 | PASS |

## Proposed Components Not Fully Implemented

GuardDuty was proposed as the managed threat-detection component but was not practically activated or validated because the experimental AWS account presented free-plan/service-access limitations and did not clearly confirm free-trial eligibility. No sample findings were generated. Monitoring also retained a PARTIAL result because the complete denied-event CloudTrail/CloudWatch evidence chain was not independently demonstrated.

## Implementation Constraints

The prototype used a controlled academic environment, synthetic or simulated banking data, one AWS account and Region, limited scale, no production customer workload, no real banking core system, and no real malicious activity. Incident response used synthetic EventBridge events and a non-destructive research tag rather than production network quarantine. These constraints prevent claims of universal prevention, production readiness, or statistical generalisability.

## Evidence References

Evidence references use existing repository paths only:

- EV-01: `cloudformation/02-network-security/` and `cloudformation/03-iam-security/`
- EV-02: `cloudformation/03-iam-security/` and `cloudformation/06-logging-monitoring/`
- EV-03: `cloudformation/04-secure-storage/`
- EV-04: `cloudformation/05-secure-compute/`
- EV-05: `cloudformation/06-logging-monitoring/` and `tests/monitoring/`
- EV-06: `cloudformation/07-threat-detection/` and `tests/threat-detection/`
- EV-07: `cloudformation/08-incident-response/` and `tests/incident-response/`

## Final Mapping Summary

The mapping preserves the Module 09 outcome of 5 PASS, 2 PARTIAL, and 0 FAIL. It distinguishes the proposed architecture from the implemented and experimentally validated prototype, and identifies currently retained or lifecycle-limited resources without inferring unverified AWS states.
