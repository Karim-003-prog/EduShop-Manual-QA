# EQ-42 — Registration accepts an email without a top-level domain

**Jira:** https://abdalkarimsamer.atlassian.net/browse/EQ-42  
**Epic:** EQ-1 — Authentication & Account Access  
**Story:** EQ-10 — Register a new account / AC-02  
**Related Test:** EQ-T4  
**Jira priority:** Medium  
**Jira status at review:** To Do

## Test data
`Test1@gmail`

## Steps to reproduce
1. Open registration.
2. Enter an email without a dot-separated TLD.
3. Complete other fields with valid data.
4. Attempt to register.

## Expected result (assumed policy)
The system rejects email addresses without a dot-separated TLD and prevents submission.

## Actual result (tester-reported)
Registration accepts the email address without the dot-separated TLD.

## Requirement ambiguity
AC-02 says the email must have a valid format, but does not explicitly specify a dot-separated TLD requirement. Confirm this consumer-email validation policy with the Product Owner/BA.

## Evidence gaps
The original Jira description has an unfilled Actual Result placeholder, and no screenshot/network response is attached. Add exact observed UI response, build/browser, and evidence before formal triage.
