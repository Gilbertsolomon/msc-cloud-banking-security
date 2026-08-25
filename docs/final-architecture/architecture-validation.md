# Final Architecture Validation

## Validation Objective

To consolidate the existing Module 01-09 implementation and validation evidence into a bounded final architecture record without repeating AWS experiments or inventing missing observations.

## Validation Scope

The scope includes network security, IAM, data protection, secure compute, monitoring, threat detection, incident response, and the Module 09 integrated evaluation. The final network block supplied for this review contained bracketed values rather than actual observations; those values are therefore recorded as not supplied.

## Network Validation

Existing evidence documents the following network controls:

- Amazon VPC with public and private subnets.
- Public subnet association with an explicit Internet Gateway default route.
- No direct Internet Gateway route for the private subnet.
- Private application access restricted to the approved public web security group on TCP port 8080.

The following final-state values were not supplied and are not inferred: `msc-banking-network` status, `msc-network-security` status, VPC/subnet presence values, exact public-tier security-rule result, and exact private application security-group source-restriction result.

## IAM Validation

Least-privilege behaviour was experimentally demonstrated: unauthorised privileged administrative activity was denied, and the temporary monitoring identity was deleted. The existing IAM module records earlier MFA enablement and validation for `msc-cloud-admin`; no additional MFA claim is made here.

## Data-Protection Validation

Module 04 validated S3 SSE-S3 AES-256 encryption, Block Public Access, `BucketOwnerEnforced` ownership, versioning, and the `DenyInsecureTransport` policy using synthetic or simulated banking data. This is not a claim about testing real customer data.

## Secure-Compute Validation

Module 05 validated a controlled Lambda workload operating within the intended private AWS security boundary with successful synthetic execution and CloudWatch evidence. No production banking workload or embedded customer credentials were used.

## Monitoring Validation

Module 06 demonstrated CloudTrail logging, CloudWatch log delivery, AccessDenied metric generation, and alarm transition to `ALARM`. The specific denied administrative action was not successfully located in the required CloudTrail Event History or associated CloudWatch Logs evidence, so the integrated monitoring result remains PARTIAL.

## Threat-Detection Validation

GuardDuty was proposed but was not practically activated or validated. The experimental AWS account presented free-plan and service-access limitations, and the cost-safety procedure stopped activation when free-trial eligibility was not clearly confirmed. No GuardDuty sample findings were generated.

## Incident-Response Validation

Synthetic EventBridge testing demonstrated selective, non-destructive response. A low-severity event did not trigger containment; a high-severity event invoked Lambda and applied `IncidentStatus = Quarantined-Test` plus the configured synthetic incident-source tag. The operation was a controlled research tagging action, not production containment or a real cyberattack.

## Integrated Evaluation Reference

Module 09 recorded the following final integrated results:

| Scenario | Result |
|---|---|
| EV-01 Network Security | PASS |
| EV-02 IAM | PASS |
| EV-03 Data Protection | PASS |
| EV-04 Secure Compute | PASS |
| EV-05 Monitoring | PARTIAL |
| EV-06 Threat Detection | PARTIAL |
| EV-07 Incident Response | PASS |

Totals: 5 PASS, 2 PARTIAL, 0 FAIL. Strict success rate: 71.4%. This is a descriptive proportion of fully passing evaluation scenarios, not a probability of preventing attacks or banking breaches.

## Known Limitations

- Controlled academic research environment.
- Simulated or synthetic banking data.
- Single AWS account and single AWS Region.
- Limited experimental scale.
- No production customer workload or real banking core system.
- No real malicious cyberattack.
- GuardDuty practical validation constrained by account/free-plan service access.
- Incomplete end-to-end CloudTrail/CloudWatch evidence chain for the denied event.
- Synthetic EventBridge incident-response events.
- Non-destructive VPC research tagging rather than production network quarantine.
- Results should not be statistically generalised to production banks.

## Final Validation Status

The implemented prototype is documented and experimentally evaluated within the stated limits. Deleted resources remain part of the experimentally validated prototype but are not currently live; the temporary monitoring identity is confirmed deleted. The current live/deleted state of other temporary stacks is not inferred where the existing evidence does not confirm it. GuardDuty remains proposed and constrained rather than practically validated.

## Resource Lifecycle

| Resource or layer | Lifecycle state supported by existing evidence |
|---|---|
| Network foundation | Retained temporarily for final architecture validation. |
| IAM temporary test identity | Deleted after validation. |
| Secure-storage resources | Use the lifecycle state documented in Module 04; no additional deletion is inferred here. |
| Secure-compute resources | Use the lifecycle state documented in Module 05; no additional deletion is inferred here. |
| Logging/monitoring resources | Use the lifecycle state documented in Module 06; no additional deletion is inferred here. |
| GuardDuty | Not enabled; no detector or findings are claimed. |
| Incident-response resources | Use the lifecycle state documented in Module 08; temporary tag removal was not verified. |
