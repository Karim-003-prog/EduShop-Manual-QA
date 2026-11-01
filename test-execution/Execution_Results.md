# EduShop — Registration Test Execution Summary

**Feature / Epic:** Authentication & Account Access ([EQ-1](https://abdalkarimsamer.atlassian.net/browse/EQ-1))  
**User Story:** Register a new account ([EQ-10](https://abdalkarimsamer.atlassian.net/browse/EQ-10))  
**Test source:** Zephyr export `atm-exporter.xlsx`, 10 test cases (`EQ-T1`–`EQ-T10`)  
**Results source:** Tester-reported execution results in QA-Track conversation; **not synchronized to Zephyr**.

## Execution Overview

| Metric | Count |
|---|---:|
| Test cases in export | 10 |
| Reported passed | 9 |
| Reported failed | 1 |
| Reported blocked / not executed | 0 |
| Jira defects reported | 1 |

## Reported Results

| Zephyr ID | Test case | Reported outcome | Defect |
|---|---|---|---|
| EQ-T1 | All registration fields are mandatory | Passed | — |
| EQ-T2 | Accepts valid email formats | Passed | — |
| EQ-T3 | Rejects emails with missing components | Passed | — |
| EQ-T4 | Rejects email without a TLD | **Failed** | [EQ-42](https://abdalkarimsamer.atlassian.net/browse/EQ-42) |
| EQ-T5 | Accepts a password meeting all requirements | Passed | — |
| EQ-T6 | Rejects passwords shorter than 6 characters | Passed | — |
| EQ-T7 | Rejects passwords without uppercase letters | Passed | — |
| EQ-T8 | Rejects passwords without lowercase letters | Passed | — |
| EQ-T9 | Rejects passwords without digits | Passed | — |
| EQ-T10 | Rejects passwords without special characters | Passed | — |

## Defect / Requirement Note

- **[EQ-42](https://abdalkarimsamer.atlassian.net/browse/EQ-42):** Registration accepts an email address without a top-level domain (TLD).
- **Jira test data:** `Test1@gmail`.
- **Tester observation:** The registration flow accepted the email without a dot-separated TLD.
- **Requirement caveat:** EQ-10 AC-02 requires a "valid email format" but does not explicitly define a dot-separated TLD. Defect classification should be confirmed against the product's intended validation policy.
- **Jira documentation gap at time of review:** EQ-42 description still contains an `Actual Result` placeholder and has no attachment.

## Reconciliation Before Publishing a Final Execution Baseline

1. Record the actual execution statuses in Zephyr (the export supplied here currently marks all 10 cases `Draft`, which is a test-case lifecycle status, not evidence of execution).
2. Re-export after Zephyr updates, and preserve the updated BVA data: `Abc12!` (6 characters), `Abc12!!` (7 characters).
3. Complete the `Actual Result` and evidence on EQ-42; confirm whether a dot-separated TLD is a defined requirement.
4. Attach the original Test Plan once retrieved; it is intentionally not reconstructed or invented in this execution summary.

**Provenance:** Test case names/IDs from the supplied Zephyr export; outcomes from the tester's statement in the conversation. No browser or API runs were performed by the author of this report.
