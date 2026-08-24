# Threat Detection Tests

## TD-01 GuardDuty Activation

**Objective:** Determine whether GuardDuty can be enabled under the project cost-safety procedure.

**Expected result:** GuardDuty is enabled only after the required cost and free-trial conditions are confirmed.

**Observed result:** GuardDuty enabled: `NO`.

**Status:** NOT EXECUTED / STOPPED BY COST-SAFETY CONTROL

## TD-02 Free-Trial Confirmation

**Objective:** Confirm that the account is eligible for the required 30-day GuardDuty free trial.

**Expected result:** Free-trial eligibility is clearly confirmed before activation.

**Observed result:** GuardDuty 30-day free trial confirmed: `NO`; account/free-plan limitations were displayed.

**Status:** NOT VERIFIED

## TD-03 Sample Finding Generation

**Objective:** Generate an AWS-provided GuardDuty sample finding without performing malicious activity.

**Expected result:** A sample finding is generated.

**Observed result:** Sample findings generated: `NO` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-04 Finding Visibility

**Objective:** Verify that a generated sample finding is visible in GuardDuty.

**Expected result:** A generated sample finding is visible.

**Observed result:** Sample findings visible: `NO` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-05 Finding-Type Identification

**Objective:** Identify the type of a GuardDuty sample finding.

**Expected result:** The selected finding type is identified.

**Observed result:** Selected finding type: `NOT TESTED` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-06 Severity Identification

**Objective:** Identify the severity of a GuardDuty sample finding.

**Expected result:** The selected finding severity is identified.

**Observed result:** Selected finding severity: `NOT TESTED` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-07 Resource Context

**Objective:** Verify that the affected resource category is visible in a GuardDuty finding.

**Expected result:** The affected resource category is visible.

**Observed result:** Affected resource category visible: `NO` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-08 Sample Metadata Validation

**Objective:** Confirm the metadata associated with a GuardDuty sample finding.

**Expected result:** Sample metadata is confirmed.

**Observed result:** Sample metadata confirmed: `NO` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## TD-09 Finding Investigation/Filtering

**Objective:** Investigate and filter GuardDuty findings.

**Expected result:** Finding filtering and investigation are completed.

**Observed result:** Finding filtering/investigation completed: `NO` because GuardDuty was not enabled.

**Status:** NOT APPLICABLE / NOT EXECUTED

## Experiment Safety

No real malicious activity was performed, no real compromise occurred, and no production banking resources or genuine customer data were used.
