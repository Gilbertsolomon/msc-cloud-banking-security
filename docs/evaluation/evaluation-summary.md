# Evaluation Summary

## Integrated Security Evaluation Summary

## Evaluation Objective

The objective was to evaluate the integrated defence-in-depth architecture using only the verified experimental observations and existing evidence from Modules 01-08.

## Architecture Under Evaluation

The designed/proposed architecture contains seven connected security layers: IAM, Network Security, Data Protection, Secure Compute, Monitoring, Threat Detection, and Incident Response. The practically validated prototype demonstrates the implemented controls in the available research environment; GuardDuty remains a proposed component whose practical validation was constrained by the AWS account and service-access limitation.

## Evaluation Method

Seven integrated scenarios were compared with their expected outcomes. A PASS records a fully met expected outcome. A PARTIAL records meaningful demonstrated functionality with an incomplete evidence chain or constrained capability. A FAIL would record an unmet expected outcome; none was recorded. No additional AWS resources or tests were created for this evaluation.

## Summary of Results

| Result | Count |
|---|---:|
| PASS | 5 |
| PARTIAL | 2 |
| FAIL | 0 |

The strict success rate is $(5 / 7) \times 100 = 71.4\%$. This is a proportion of evaluation scenarios receiving full PASS status, not a probability of preventing cyberattacks or banking breaches.

## Cross-Layer Security Observations

Defence in depth was represented by the following relationships:

- **IAM** restricts who can perform actions.
- **Network security** restricts communication paths.
- **Data protection** protects stored information.
- **Secure compute** provides controlled workload execution.
- **Monitoring** provides visibility into unauthorised activity.
- **Threat detection** represents the proposed higher-level finding capability, although practical GuardDuty validation was constrained.
- **Incident response** automatically responds to qualifying synthetic events.

Together, the layers address prevention, visibility, and response at different control points. IAM and network controls constrain activity, storage controls protect information at rest, and the compute boundary limits workload exposure. Monitoring detects selected unauthorised activity, while incident response demonstrates an automated reaction to a qualifying synthetic event.

The strongest experimentally demonstrated controls were network segmentation, least-privilege access behaviour, secure storage protections, secure private workload execution, and the EventBridge/Lambda response workflow.

## Limitations

The prototype was conducted in a controlled academic research environment using simulated or synthetic banking data, a single AWS account, a single AWS Region, and limited experimental scale. It included no production customer workload, real banking core system, or real malicious cyberattack. Results should not be statistically generalised to production banks or interpreted as universal security effectiveness.

Monitoring was PARTIAL because AccessDenied metric and alarm generation worked, but the specific denied administrative action was not successfully located in the required CloudTrail Event History or associated CloudWatch Logs evidence. GuardDuty was PARTIAL because practical activation and sample-finding validation were unavailable under the experimental account Free account plan and service-access limitation. This is an implementation and evaluation constraint, not evidence that GuardDuty itself failed.

## Overall Evaluation

The integrated evaluation recorded 5 PASS, 2 PARTIAL, and 0 FAIL results. The prototype therefore demonstrated several complementary controls and an automated synthetic incident-response path, while retaining the two limitations rather than overstating the evidence.

The proposed architecture is broader than the practically validated implementation. GuardDuty was included in the proposed threat-detection design but was not enabled and generated no sample findings in this account. The practically implemented detective capability was the existing CloudTrail and CloudWatch monitoring layer, with incomplete end-to-end event evidence for the controlled denied action.

Incident-response validation used synthetic EventBridge events. The high-severity event applied `IncidentStatus = Quarantined-Test` and the configured synthetic incident-source tag; this was a non-destructive research tagging operation, not production network isolation or a real cyberattack.

PARTIAL results were deliberately retained as PARTIAL for academic integrity. Counting them as PASS would obscure the missing evidence and misrepresent the boundary between demonstrated functionality and independently verified end-to-end behaviour. The 71.4% strict success rate must therefore be read as a descriptive evaluation result, not as a probability of preventing cyberattacks or banking breaches.
