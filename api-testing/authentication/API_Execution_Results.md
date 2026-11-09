# EduShop — Epic 1 API Execution Results

**Feature:** Authentication & Account Access  
**Environment:** EduShop Local (`http://localhost:5000`)  
**Source of results:** Tester-reported execution in Postman. Expected outcomes are based on the EduShop API documentation and the recorded test cases. Actual results summarize the tester's confirmations; detailed request/response evidence is not attached.

## Registration — `POST /api/auth/register`

| TC ID | Test Scenario | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| EQ-T14 | Register with valid data | `200 OK`; authentication response with Customer role and tokens | Tester reported successful registration and expected response | PASS |
| API-AUTH-02 | Missing required fields | `400 Bad Request`; validation error | Tester reported expected validation rejection | PASS |
| API-AUTH-03 | Invalid email format | `400 Bad Request`; email validation error | Tester reported expected validation rejection | PASS |
| API-AUTH-04 | Password shorter than 6 characters | `400 Bad Request`; password validation error | Tester reported expected validation rejection | PASS |
| API-AUTH-05 | Passwords do not match | `400 Bad Request`; confirmation validation error | Tester reported expected validation rejection | PASS |
| API-AUTH-06 | Email already registered | `400 Bad Request`; duplicate-email error | Tester reported expected duplicate-email rejection | PASS |
| API-AUTH-07 | Password complexity violations | `400 Bad Request`; password policy error | Tester reported expected password policy rejection | PASS |

## Login — `POST /api/auth/login`

| TC ID | Test Scenario | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| API-AUTH-15 | Valid credentials | `200 OK`; access and refresh tokens, access token valid for 60 minutes | Tester reported successful login and 60-minute access token lifetime | PASS |
| API-AUTH-16 | Missing or malformed fields | `400 Bad Request`; validation response | Tester reported Login validation PASS; individual datasets were not detailed | PASS |
| API-AUTH-17 | Wrong password vs. non-existent email | `401 Unauthorized` for both; identical generic message | Tester reported the same `Wrong Email or Password` message in both cases | PASS |

## Refresh Token — `POST /api/auth/refresh`

| TC ID | Test Scenario | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| API-AUTH-08 | Valid, unused refresh token | `200 OK`; new access + refresh token pair | Tester explicitly confirmed `200` for valid refresh | PASS |
| API-AUTH-09 | Unparseable access token | `401 Unauthorized`; `Invalid access token.` | Tester explicitly confirmed `401` | PASS |
| API-AUTH-10 | Reuse previously used refresh token | `401 Unauthorized`; `Invalid or expired refresh token.` | Tester explicitly confirmed `401` | PASS |
| API-AUTH-11 | Expired refresh token | `401 Unauthorized`; `Invalid or expired refresh token.` | Tester explicitly confirmed `401` | PASS |
| API-AUTH-12 | Revoked refresh token | `401 Unauthorized`; `Invalid or expired refresh token.` | Tester explicitly confirmed `401` | PASS |
| API-AUTH-13 | Refresh token belongs to deleted user | `401 Unauthorized`; `User not found.` | Tester explicitly confirmed `401` | PASS |

## Logout — `POST /api/auth/logout` (verified using `POST /api/auth/refresh`)

| TC ID | Test Scenario | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| API-AUTH-14 | Refresh token cannot be reused after logout | After logout, refresh returns `401 Unauthorized` with `Invalid or expired refresh token.` | Tester logged out, then attempted refresh using the old token; received `401` and `Invalid or expired refresh token.` | PASS |

## Access Control — Admin-only API endpoint

| TC ID | Test Scenario | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| API-AUTH-18 | Customer calls an Admin-only endpoint with a valid Customer token | `403 Forbidden` | Tester reported `403 Forbidden` | PASS |

**Endpoint note:** The exact Admin-only request path used for API-AUTH-18 was not recorded. Add it when available rather than guessing an endpoint.

## Execution Summary

| Metric | Result |
|---|---:|
| Test Cases | 18 |
| Passed | 18 |
| Failed | 0 |
| Pass Rate | 100% (tester-reported) |

**Evidence:** Detailed Postman request/response exports are not attached. This file records reported outcomes and does not claim independent verification. UI-only scenarios and `GET /api/auth/me` are outside this execution summary.
