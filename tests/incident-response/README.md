# Incident Response Tests

## IR-01 CloudFormation Deployment

**Objective:** Verify that the incident-response CloudFormation stack deploys successfully.

**Expected result:** Stack `msc-incident-response` reaches `CREATE_COMPLETE`.

**Observed result:** Stack status was `CREATE_COMPLETE`.

**Status:** PASS

## IR-02 EventBridge Rule Activation

**Objective:** Verify that the security EventBridge rule is enabled.

**Expected result:** The EventBridge security rule is enabled.

**Observed result:** EventBridge rule enabled: `YES`.

**Status:** PASS

## IR-03 Low-Severity Event Submission

**Objective:** Verify that the low-severity negative-control event can be submitted.

**Expected result:** The low-severity `PutEvents` request succeeds.

**Observed result:** Low-severity `PutEvents` result: `SUCCESS`.

**Status:** PASS

## IR-04 Low-Severity Non-Match Validation

**Objective:** Verify that a low-severity event does not trigger containment.

**Expected result:** No containment tag is applied by the high-severity EventBridge rule.

**Observed result:** Low-severity containment tag result: `NO`; `IncidentStatus` was not present in the MSc-Banking-VPC Tags view.

**Status:** PASS

## IR-05 High-Severity Event Submission

**Objective:** Verify that the high-severity positive-response event can be submitted.

**Expected result:** The high-severity `PutEvents` request succeeds.

**Observed result:** High-severity `PutEvents` result: `SUCCESS`.

**Status:** PASS

## IR-06 Automated Containment Tag

**Objective:** Verify that a matching high-severity event causes the Lambda response to apply the controlled containment tag.

**Expected result:** `IncidentStatus` is set to `Quarantined-Test`.

**Observed result:** `IncidentStatus` after the high-severity event: `Quarantined-Test`.

**Status:** PASS

## IR-07 Incident Source Tag

**Objective:** Verify that the response records the source of the synthetic security event.

**Expected result:** `IncidentSource` is set to `MSc-Synthetic-Security-Event`.

**Observed result:** `IncidentSource` after the high-severity event: `MSc-Synthetic-Security-Event`.

**Status:** PASS

## IR-08 CloudWatch Response Logging

**Objective:** Verify that the Lambda response produces a CloudWatch log event.

**Expected result:** A Lambda response log is generated.

**Observed result:** Lambda response log generated: `YES`. The verified response was `containment-tag-applied`, with event ID `IR-TEST-HIGH-001` and severity `High`; `START`, `END`, and `REPORT` records were also generated.

**Status:** PASS

## IR-09 Lambda Response Invocation

**Objective:** Verify that the high-severity event invokes the response Lambda successfully.

**Expected result:** Lambda invocation for the high-severity event succeeds.

**Observed result:** Lambda invocation successful: `YES`.

**Status:** PASS

## IR-10 Rollback of Test Containment State

**Objective:** Verify that temporary containment tags are removed after validation.

**Expected result:** Test containment tags are removed.

**Observed result:** Test containment tags removed after validation: `NOT YET VERIFIED`.

**Status:** NOT VERIFIED

## Safety Scope

The event was synthetic. No real cyberattack or destructive containment operation was performed, and no real customer data or production banking system was used. The containment mechanism was a controlled research tagging operation.
