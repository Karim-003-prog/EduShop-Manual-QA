# EduShop — Manual QA Test Plan (Reconstructed Working Draft)

> **Important:** This is a reconstructed working draft based on the available EduShop backlog, Jira EQ-10 and Zephyr export. The original Test Plan discussed earlier was not available. This is **not** a recovered or formally approved plan.

## Objective
Validate EduShop registration against acceptance criteria, find defects, record evidence, and maintain traceability of requirements, test cases and bugs.

## Current test scope
**Epic:** [EQ-1 — Authentication & Account Access](https://abdalkarimsamer.atlassian.net/browse/EQ-1).  
**User Story:** [EQ-10 — Register a new account](https://abdalkarimsamer.atlassian.net/browse/EQ-10), AC-01–AC-07.  
The current Zephyr export has 10 cases related to AC-01–AC-03; AC-04–AC-07 require additional test design. Other EduShop modules and automated/performance testing are outside this iteration's recorded execution scope.

## Test basis and tools
EduShop Test Backlog; Jira User Story and ACs; Zephyr cases; local application (frontend localhost:4200, backend localhost:5000); browser DevTools; Jira for defects, Zephyr for test design/execution and GitHub for portfolio reporting. API/database checks are not claimed as executed in this iteration.

## Test approach
Manual functional UI testing with positive and negative scenarios, equivalence partitioning, BVA (password 5, 6, 7 characters), one-condition-at-a-time decision-table checks for password complexity, and risk-based exploratory checks. Use expected results grounded in requirements; clarify ambiguous TLD policy.

## Entry criteria
Local build accessible; required test data ready; ACs understood; test cases available; browser environment operational.

## Exit / reporting criteria
Run planned tests, record actual and expected outcomes and evidence, log defects, communicate unresolved ambiguities, retest fixes and conduct relevant regression. No release sign-off or complete story coverage is implied by the current results.

## Risks
1. Ambiguous email-domain policy for a dot-separated TLD — clarify with Product Owner/BA; see [EQ-42](https://abdalkarimsamer.atlassian.net/browse/EQ-42).
2. Incomplete test design for AC-04 to AC-07 — add dedicated cases.
3. Zephyr export lists all cases as Draft, while tester reported outcomes separately — enter official Test Cycle evidence.
4. Older Zephyr export has wrong BVA test data — update Zephyr to `Abc12!` (6) and `Abc12!!` (7).

## Current iteration deliverables
Test cases (CSV and Markdown), registration AC traceability, tester-reported execution summary and defect documentation. Capture environment/version and screenshots in a subsequent execution cycle.
