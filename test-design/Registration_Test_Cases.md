# Registration Test Cases

> Source: Zephyr export, 10 cases EQ-T1 through EQ-T10. All were Draft in the export. Outcomes are tester-reported, not verified Zephyr runs.

## EQ-T1: Verify that all registration fields are mandatory.

**Preconditions:** The user is on the registration page.

**Steps:**

- Keep all fields blank
- Click the submit button

**Test Data:**

 N\A

**Expected Result:**

Registration blocks submission of the form if any fields are empty and 
displays a validation error message.

**Tester-reported Result:** Passed

## EQ-T2: Verify that the email is in a valid email format

**Preconditions:** The user is on the registration page.

**Steps:**

Click on the email field
Type a valid email address

**Test Data:**

Email: Test1@gmail.com
Email: test1@gmail.com
Email: TEST1@GMAIL.com

**Expected Result:**

The system accepts the valid email address without displaying any email 
validation errors

**Tester-reported Result:** Passed

## EQ-T3: Verify registration rejects emails with missing components

**Preconditions:** The user is on the registration page

**Steps:**

Click on the email field
Type these test data

**Test Data:**

Email: usertest.com
Email: @test.com
Email: usertest@.com

**Expected Result:**

The system should reject the emails with missing components.

**Tester-reported Result:** Passed

## EQ-T4: Verify that the registration rejects an email with a missing TLD

**Preconditions:** The user is on the registration page

**Steps:**

Click on the email field.
Type the email with a missing TLD.

**Test Data:**

Email: Test1@gmail

**Expected Result:**

The system must prevent submission and show an appropriate validation error 
message.

**Tester-reported Result:** Failed — [EQ-42](https://abdalkarimsamer.atlassian.net/browse/EQ-42)

## EQ-T5: Verify that registration accepts a password meeting all requirements

**Preconditions:** The user is on the registration page

**Steps:**

Click on the password field 
Enter a valid password

**Test Data:**

Abc12! (6 characters)
Abc12!! (7 characters) — corrected after the export

**Expected Result:**

The system should accept a valid password without displaying an error 
message.

**Tester-reported Result:** Passed

## EQ-T6: Verify that registration rejects passwords shorter than 6 characters.

**Preconditions:**     * The registration page is accessible.
    * The email address is not already registered.

**Steps:**

    * Navigate to the Registration page.
    * Fill in all required fields with valid data.
    * Enter Aa1@x in the Password field.
    * Enter the same password in the Confirm Password field.
    * Click the Register button.

**Test Data:**

    * Email: test01@example.com
    * Password: Aa1@x (5 characters)
    * Confirm Password: Aa1@x
    * Other required fields: Valid data

**Expected Result:**

The system should reject passwords shorter than 6 characters

**Tester-reported Result:** Passed

## EQ-T7: Verify that registration rejects passwords without an uppercase letter.

**Preconditions:**     * Registration page is accessible.
    * The email address is not already registered.

**Steps:**

    * Navigate to the Registration page.
    * Fill in all required fields with valid data.
    * Enter abc1@x in the Password field.
    * Enter the same password in the Confirm Password field.
    * Click the Register button.

**Test Data:**

    * Email: test02@example.com
    * Password: abc1@x
    * Confirm Password: abc1@x
    * Other required fields: Valid data

**Expected Result:**

The system should reject a password without an uppercase letter

**Tester-reported Result:** Passed

## EQ-T8: Verify that registration rejects passwords without a lowercase letter.

**Preconditions:**     * Registration page is accessible.
    * The email address is not already registered.

**Steps:**

    * Navigate to the Registration page.
    * Fill in all required fields with valid data.
    * Enter ABC1@X in the Password field.
    * Enter the same password in the Confirm Password field.
    * Click the Register button.

**Test Data:**

    * Email: test03@example.com
    * Password: ABC1@X
    * Confirm Password: ABC1@X
    * Other required fields: Valid data

**Expected Result:**

The system should reject the password without a lowercase letter

**Tester-reported Result:** Passed

## EQ-T9: Verify that registration rejects passwords without a digit

**Preconditions:**     * Registration page is accessible.
    * The email address is not already registered.

**Steps:**

   1. Navigate to the Registration page.
   2. Fill in all required fields with valid data.
   3. Enter Abcd@x in the Password field.
   4. Enter the same password in the Confirm Password field.
   5. Click the Register button.

**Test Data:**

    * Email: test04@example.com
    * Password: Abcd@x
    * Confirm Password: Abcd@x
    * Other required fields: Valid data

**Expected Result:**

The system should reject a password that is missing a digit.

**Tester-reported Result:** Passed

## EQ-T10: Verify that registration rejects passwords without a special character.

**Preconditions:**     * Registration page is accessible.
    * The email address is not already registered.

**Steps:**

    * Navigate to the Registration page.
    * Fill in all required fields with valid data.
    * Enter Abc123 in the Password field.
    * Enter the same password in the Confirm Password field.
    * Click the Register button.

**Test Data:**

    * Email: test05@example.com
    * Password: Abc123
    * Confirm Password: Abc123
    * Other required fields: Valid data

**Expected Result:**

The system should reject a password without a special character.

**Tester-reported Result:** Passed
