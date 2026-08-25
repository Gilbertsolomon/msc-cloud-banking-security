# Integrated Evaluation

## Module 09 - Integrated Security Evaluation

## Purpose

This evaluation assesses how the security layers work together across the MSc cloud-banking security prototype. It records only the verified observations from Modules 01-08.

## Evaluation Scope

The evaluation covers network security, IAM, data protection, secure compute, monitoring, threat detection, and incident response. It evaluates the practically validated prototype and distinguishes it from capabilities that were designed or proposed but constrained during implementation.

## Security Layers Under Evaluation

- Network Security
- IAM
- Data Protection
- Secure Compute
- Monitoring
- Threat Detection
- Incident Response

## Integrated Test Methodology

Each scenario was assessed against its expected outcome using existing implementation and validation evidence from Modules 01-08. Results are reported as PASS, PARTIAL, or FAIL only where supported by the supplied observations. No additional AWS resources or tests were created for Module 09.

**PASS** means the supplied observation met the expected outcome.

**PARTIAL** means important functionality was demonstrated, but the complete intended evidence chain or capability was not independently demonstrated.

**FAIL** means the supplied observation did not meet the expected outcome. No scenario was recorded as FAIL.

## Evaluation Scenarios

### EV-01 Network Segmentation and Isolation

**Expected outcome:** Public/private segmentation and associated network controls are implemented and validated.

**Observed outcome:** The MSc-Banking-VPC used the intended public/private network segmentation and associated security controls.

**Status:** PASS

**Evidence source:** Existing network implementation and validation evidence in `cloudformation/02-network-security/` and `cloudformation/03-iam-security/`.

### EV-02 Least-Privilege Access Control

**Expected outcome:** Unauthorised privileged operations are denied and the temporary test identity is removed.

**Observed outcome:** Privileged administrative operations were denied; `msc-monitoring-test` attempted an unauthorised operation and was subsequently deleted using `msc-cloud-admin`.

**Status:** PASS

**Evidence source:** `cloudformation/03-iam-security/` and `cloudformation/06-logging-monitoring/`.

### EV-03 Customer-Data Protection

**Expected outcome:** Simulated banking-data storage uses private-access controls, encryption, and versioning.

**Observed outcome:** The simulated banking-data environment was validated with private-access controls, encryption, versioning, and the Module 04 secure-storage controls.

**Status:** PASS

**Evidence source:** `cloudformation/04-secure-storage/` and its existing validation evidence.

### EV-04 Secure Application Workload

**Expected outcome:** The prototype workload runs inside the intended private AWS security boundary with successful controlled execution.

**Observed outcome:** The prototype banking Lambda workload operated within the intended private AWS security boundary and controlled synthetic execution completed successfully.

**Status:** PASS

**Evidence source:** `cloudformation/05-secure-compute/` and its existing validation evidence.

### EV-05 Security Event Detection and Alerting

**Expected outcome:** An unauthorised activity event is visible through the complete CloudTrail, CloudWatch metric, and alarm evidence chain.

**Observed outcome:** The AccessDenied metric/alarm pipeline detected activity and `MSc-Banking-AccessDenied-Alarm` transitioned to `ALARM`, but the denied action was not located in the required CloudTrail Event History or CloudWatch Logs evidence.

**Status:** PARTIAL

**Evidence source:** `cloudformation/06-logging-monitoring/` and `tests/monitoring/`.

### EV-06 Threat Detection

**Expected outcome:** GuardDuty is activated and sample findings are validated under approved account conditions.

**Observed outcome:** GuardDuty activation and sample-finding validation could not be completed because of the experimental account Free account plan and service-access limitation; no findings were generated.

**Status:** PARTIAL

**Evidence source:** `cloudformation/07-threat-detection/` and `tests/threat-detection/`.

### EV-07 Automated Incident Response

**Expected outcome:** Qualifying synthetic events trigger an automated non-destructive response while low-severity events do not.

**Observed outcome:** The Low-severity event did not produce containment tags; the High-severity event matched EventBridge, invoked Lambda, and applied the `Quarantined-Test` research tag.

**Status:** PASS

**Evidence source:** `cloudformation/08-incident-response/` and `tests/incident-response/`.

## Evidence Collection

Evidence references use existing module and test-documentation paths only. No screenshot numbers, dissertation figure numbers, or new evidence references have been invented.

## Results

| Result | Count |
|---|---:|
| PASS | 5 |
| PARTIAL | 2 |
| FAIL | 0 |

Total evaluation scenarios: 7

Strict success rate: $(5 / 7) \times 100 = 71.4\%$

Only full PASS results are included in the strict success rate. PARTIAL results were deliberately not counted as PASS because their complete intended evidence chains or capabilities were not independently demonstrated.

## Limitations

The evaluation represents a controlled academic research environment using simulated or synthetic banking data, a single AWS account, a single AWS Region for the practical prototype, and limited experimental scale. It did not use a production customer workload, real banking core system, or real malicious cyberattack. GuardDuty validation was constrained by the AWS account/free-plan service-access limitation. Monitoring had an incomplete end-to-end CloudTrail/CloudWatch evidence chain for the controlled denied event. Incident response used synthetic EventBridge events and a non-destructive VPC research tag rather than production network quarantine. Results should not be statistically generalised to production banks.

## Cleanup and Validation Notes

This Module 09 task created no AWS resources and required no additional AWS testing. Existing module cleanup decisions remain applicable.
