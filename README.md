# EduShop-Manual-QA

Manual QA portfolio covering UI testing for the EduShop e-commerce application, with planned API and database work.

## Registration work products

- **Epic:** [EQ-1 — Authentication & Account Access](https://abdalkarimsamer.atlassian.net/browse/EQ-1)
- **User Story:** [EQ-10 — Register a new account](https://abdalkarimsamer.atlassian.net/browse/EQ-10)
- **Reported execution:** 10 Test Cases; 9 Passed, 1 Failed (EQ-T4). **Results are tester-reported**; the Zephyr export still lists Draft.
- **Jira defect:** [EQ-42 — Registration accepts email without a dot-separated TLD](https://abdalkarimsamer.atlassian.net/browse/EQ-42)

| Work product | Document |
|---|---|
| Test Plan (reconstructed draft; original not available) | [Test Plan](test-planning/Test_Plan.md) |
| Test Cases | [Markdown](test-design/Registration_Test_Cases.md), [CSV](test-design/Registration_Test_Cases.csv) |
| AC coverage | [Traceability](traceability/Registration_AC_Coverage.md) |
| Execution | [Results](test-execution/Execution_Results.md) |
| Defect | [EQ-42](defect-reports/EQ-42_Registration_Email_TLD.md) |

**Limitations:** Current 10-case export covers parts of AC-01–AC-03 only; AC-04–AC-07 need further test design. EQ-T5 BVA was corrected after export to `Abc12!` (6 chars) / `Abc12!!` (7 chars). AC-02 does not explicitly mandate a dot-separated TLD; clarify before confirming a requirements defect.
