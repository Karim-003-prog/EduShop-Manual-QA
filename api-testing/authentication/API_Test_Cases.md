# EduShop — Epic 1: Authentication & Account Access

## API Test Cases

> Scope: API test cases documented from tester notes and prior records. Sample test data are illustrative; do not treat them as proof of execution. Passwords and tokens must not be committed.

## Registration

### EQ-T14 — Verify that the API registers a user with valid data.

**Preconditions:** Open Postman.

**Steps:**
1. Select the POST method and enter the registration endpoint URL.
2. Type the required valid data into the body.
3. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "Test",
    "lastName": "Customer",
    "email": "Test12@gmail.com",
    "password": "Adfm12!",
    "confirmPassword": "Adfm12!"
  }
}
```

**Expected result:** The API should return 200 OK and JSON response containing the access token, refresh token, email, first name, last name, Customer role, and access token expiration time.

### API-AUTH-02 — Verify registration rejects missing required fields.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "",
    "lastName": "Customer",
    "email": "qa.missing@example.com",
    "password": "Adfm12!",
    "confirmPassword": "Adfm12!"
  }
}
```

**Expected result:** 400 Bad Request; validation error for the missing required field.

### API-AUTH-03 — Verify registration rejects an invalid email format.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "Test",
    "lastName": "Customer",
    "email": "invalid-email",
    "password": "Adfm12!",
    "confirmPassword": "Adfm12!"
  }
}
```

**Expected result:** 400 Bad Request; email validation error.

### API-AUTH-04 — Verify registration rejects passwords shorter than 6 characters.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "Test",
    "lastName": "Customer",
    "email": "qa.short@example.com",
    "password": "Aa1!x",
    "confirmPassword": "Aa1!x"
  }
}
```

**Expected result:** 400 Bad Request; password validation error.

### API-AUTH-05 — Verify registration rejects mismatched passwords.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "Test",
    "lastName": "Customer",
    "email": "qa.mismatch@example.com",
    "password": "Adfm12!",
    "confirmPassword": "Different1!"
  }
}
```

**Expected result:** 400 Bad Request; password confirmation validation error.

### API-AUTH-06 — Verify registration rejects an already registered email.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": {
    "firstName": "Test",
    "lastName": "Customer",
    "email": "existing.customer@example.com",
    "password": "Adfm12!",
    "confirmPassword": "Adfm12!"
  }
}
```

**Expected result:** 400 Bad Request; message indicates the email is already registered.

### API-AUTH-07 — Verify registration rejects passwords that violate complexity rules.

**Preconditions:** Postman is open.; EduShop backend is running.

**Steps:**
1. Send POST http://localhost:5000/api/auth/register with the specified test data.
2. Check status code and error response.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/register",
  "body": [
    {
      "password": "abc123!",
      "confirmPassword": "abc123!"
    },
    {
      "password": "ABC123!",
      "confirmPassword": "ABC123!"
    },
    {
      "password": "Abcdef!",
      "confirmPassword": "Abcdef!"
    },
    {
      "password": "Abc1234",
      "confirmPassword": "Abc1234"
    }
  ]
}
```

**Expected result:** 400 Bad Request for each dataset; password policy validation error.

## Login

### API-AUTH-15 — Verify successful login with valid credentials

**Preconditions:** Registered customer; backend running

**Steps:**
1. Send POST /api/auth/login with valid email and password.

**Test data:**

```text
Registered email and correct password
```

**Expected result:** 200 OK; access and refresh tokens returned; access token lifetime is 60 minutes.

### API-AUTH-16 — Verify login validation rejects missing or malformed fields

**Preconditions:** Backend running

**Steps:**
1. Send POST /api/auth/login for each dataset; inspect status and response.

**Test data:**

```text
Invalid email format; missing email; missing password; empty email/password
```

**Expected result:** 400 Bad Request for each input that fails documented validation.

### API-AUTH-17 — Verify wrong password and non-existent email return the same generic message

**Preconditions:** Registered test account; backend running

**Steps:**
1. Attempt login with registered email + wrong password, then non-existent email + password; compare responses.

**Test data:**

```text
Two credential sets
```

**Expected result:** 401 Unauthorized for both; identical generic error message without revealing account existence.

## Refresh Token

### API-AUTH-08 — Verify that a valid refresh token generates a new token pair.

**Preconditions:** Log in and obtain a valid, unused access/refresh token pair.

**Steps:**
1. Send the valid token pair to the refresh endpoint.
2. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: valid or recently expired token; RefreshToken: valid unused token."
}
```

**Expected result:** 200 OK; a new access token and refresh token are returned. The old refresh token becomes unusable.

### API-AUTH-09 — Verify that an invalid access token is rejected.

**Preconditions:** Obtain a valid, unused refresh token. 

**Steps:**
1. Open Postman and select POST http://localhost:5000/api/auth/refresh.
2. Enter the specified tokens in the JSON request body.
3. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: malformed string; RefreshToken: valid unused token."
}
```

**Expected result:** 401 Unauthorized; message: "Invalid access token."

### API-AUTH-10 — Verify that a previously used refresh token is rejected.

**Preconditions:** Successfully refresh a token pair once.

**Steps:**
1. Resend the original access token and the original (already used) refresh token.
2. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: original token; RefreshToken: previously used token."
}
```

**Expected result:** 401 Unauthorized; message: "Invalid or expired refresh token."

### API-AUTH-11 — Verify that an expired refresh token is rejected.

**Preconditions:** Have a refresh token that has passed its 7-day expiry.

**Steps:**
1. Open Postman and select POST http://localhost:5000/api/auth/refresh.
2. Enter the specified tokens in the JSON request body.
3. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: associated parseable token; RefreshToken: expired token."
}
```

**Expected result:** 401 Unauthorized; message: "Invalid or expired refresh token."

### API-AUTH-12 — Verify that a revoked refresh token is rejected.

**Preconditions:** Have a revoked refresh token in a controlled test environment.

**Steps:**
1. Open Postman and select POST http://localhost:5000/api/auth/refresh.
2. Enter the specified tokens in the JSON request body.
3. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: associated parseable token; RefreshToken: revoked token."
}
```

**Expected result:** 401 Unauthorized; message: "Invalid or expired refresh token."

### API-AUTH-13 — Verify that refresh fails when the user no longer exists.

**Preconditions:** Have a valid token pair for a test user whose account has been deleted, with the refresh token record retained.

**Steps:**
1. Open Postman and select POST http://localhost:5000/api/auth/refresh.
2. Enter the specified tokens in the JSON request body.
3. Click Send.

**Test data:**

```text
{
  "url": "http://localhost:5000/api/auth/refresh",
  "method": "POST",
  "body": {
    "accessToken": "<access token per scenario>",
    "refreshToken": "<refresh token per scenario>"
  },
  "scenario": "AccessToken: deleted test user token; RefreshToken: associated unused token."
}
```

**Expected result:** 401 Unauthorized; message: "User not found."

## Logout

### API-AUTH-14 — Verify that logout invalidates the user's refresh token.

**Preconditions:** User is logged in.; A valid refresh token is available.

**Steps:**
1. Save the current access token and refresh token.
2. Send the Logout request.
3. Send POST /api/auth/refresh using the saved tokens.

**Test data:**

```text
Previously issued access token and refresh token.
```

**Expected result:** 401 Unauthorized with message "Invalid or expired refresh token."

## Access Control

### API-AUTH-18 — Verify a Customer token cannot access an Admin-only API

**Preconditions:** Valid Customer token; Admin-only endpoint available

**Steps:**
1. Call an Admin-only endpoint using the Customer Bearer token.

**Test data:**

```text
Customer JWT; admin-only API route
```

**Expected result:** 403 Forbidden.
