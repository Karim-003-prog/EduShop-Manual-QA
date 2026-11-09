# EduShop — Epic 1 API Execution Results

Results are **tester-reported**. A PASS on an endpoint does not automatically confirm each individual negative scenario.

| ID | Feature | Test Case | Status |
|---|---|---|---|
| EQ-T14 | Registration | Verify that the API registers a user with valid data. | PASS |
| API-AUTH-02 | Registration | Verify registration rejects missing required fields. | PASS |
| API-AUTH-03 | Registration | Verify registration rejects an invalid email format. | PASS |
| API-AUTH-04 | Registration | Verify registration rejects passwords shorter than 6 characters. | PASS |
| API-AUTH-05 | Registration | Verify registration rejects mismatched passwords. | PASS |
| API-AUTH-06 | Registration | Verify registration rejects an already registered email. | PASS |
| API-AUTH-07 | Registration | Verify registration rejects passwords that violate complexity rules. | PASS |
| API-AUTH-08 | Refresh Token | Verify that a valid refresh token generates a new token pair. | NOT CONFIRMED |
| API-AUTH-09 | Refresh Token | Verify that an invalid access token is rejected. | NOT CONFIRMED |
| API-AUTH-10 | Refresh Token | Verify that a previously used refresh token is rejected. | NOT CONFIRMED |
| API-AUTH-11 | Refresh Token | Verify that an expired refresh token is rejected. | NOT CONFIRMED |
| API-AUTH-12 | Refresh Token | Verify that a revoked refresh token is rejected. | NOT CONFIRMED |
| API-AUTH-13 | Refresh Token | Verify that refresh fails when the user no longer exists. | NOT CONFIRMED |
| API-AUTH-14 | Logout | Verify that logout invalidates the user's refresh token. | PASS |
| API-AUTH-15 | Login | Verify successful login with valid credentials | PASS |
| API-AUTH-16 | Login | Verify login validation rejects missing or malformed fields | PASS (endpoint-level report) |
| API-AUTH-17 | Login | Verify wrong password and non-existent email return the same generic message | PASS |
| API-AUTH-18 | Access Control | Verify a Customer token cannot access an Admin-only API | PASS |

## Actual results / evidence notes

**EQ-T14** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-02** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-03** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-04** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-05** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-06** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-07** — Passed (reported by tester; detailed response evidence not provided).

**API-AUTH-08** — Not separately documented.

**API-AUTH-09** — Not separately documented.

**API-AUTH-10** — Not separately documented.

**API-AUTH-11** — Not separately documented.

**API-AUTH-12** — Not separately documented.

**API-AUTH-13** — Not separately documented.

**API-AUTH-14** — After logout, the refresh request returned 401 Unauthorized with message "Invalid or expired refresh token."

**API-AUTH-15** — Tester reported successful login and 60-minute token lifetime.

**API-AUTH-16** — Tester reported Login API PASS; individual datasets not confirmed.

**API-AUTH-17** — Tester reported both returned "Wrong Email or Password".

**API-AUTH-18** — Tester reported 403 Forbidden.

## Coverage limitations

- Refresh Token endpoint was reported PASS overall, but individual negative-case outcomes were not separately confirmed.
- Logout refresh-token revocation and Customer-to-Admin 403 checks were explicitly reported PASS.
- UI redirect checks, /me endpoint checks, and other Epic 1 acceptance criteria are not claimed as API-executed here.
- No request/response screenshots or Postman run exports are attached.
