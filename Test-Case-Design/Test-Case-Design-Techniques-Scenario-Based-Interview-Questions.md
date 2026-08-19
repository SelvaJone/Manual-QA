# Test Case Design Techniques – Real-Time / Scenario-Based Interview Questions

## Overview

Test Case Design is one of the most important skills expected from a QA Engineer. Interviewers often focus less on definitions and more on how you identify scenarios, choose test data, prioritize coverage, and handle edge cases.

This document contains real-time and scenario-based interview questions suitable for Manual QA, Senior QA, QA Automation Engineer, and SDET interviews.

---

# 1. What is Test Case Design?

Test Case Design is the process of identifying test scenarios, conditions, inputs, expected results, and validations required to verify that an application behaves as expected.

A good test case should be:

* Clear
* Specific
* Repeatable
* Traceable
* Maintainable
* Independent where possible
* Focused on one behavior
* Easy for another tester to execute

---

# 2. What are the major Test Case Design Techniques?

Common techniques include:

1. Equivalence Partitioning
2. Boundary Value Analysis
3. Decision Table Testing
4. State Transition Testing
5. Use Case Testing
6. Error Guessing
7. Pairwise Testing
8. Cause-Effect Graphing
9. Exploratory Testing
10. Risk-Based Testing

---

# 3. What is Equivalence Partitioning?

Equivalence Partitioning divides input data into groups where the system is expected to behave similarly.

Instead of testing every possible input, we select representative values from each partition.

### Example

Suppose an application accepts age from 18 to 60.

Partitions:

* Less than 18 → Invalid
* 18–60 → Valid
* Greater than 60 → Invalid

Example test values:

```text
17 → Invalid
25 → Valid
61 → Invalid
```

---

# 4. Real-Time Scenario: How would you test an age field accepting 18–60?

I would use equivalence partitioning and boundary value analysis.

### Test Data

```text
17 → Invalid
18 → Valid
19 → Valid
30 → Valid
59 → Valid
60 → Valid
61 → Invalid
```

I would also check:

* Blank value
* Null value
* Decimal value
* Negative value
* Alphabetic characters
* Special characters
* Very large number
* Spaces
* Leading zeros

---

# 5. What is Boundary Value Analysis?

Boundary Value Analysis focuses on values at the edges of an accepted range.

For a range of 18–60, important values are:

```text
17
18
19
59
60
61
```

The reason is that defects frequently occur around boundaries.

---

# 6. What is the difference between Equivalence Partitioning and Boundary Value Analysis?

| Technique                | Purpose                            |
| ------------------------ | ---------------------------------- |
| Equivalence Partitioning | Divides inputs into logical groups |
| Boundary Value Analysis  | Tests values around boundaries     |

Example:

For an age field accepting 18–60:

### Equivalence Partitioning

```text
<18
18–60
>60
```

### Boundary Value Analysis

```text
17
18
19
59
60
61
```

In real projects, I normally combine both techniques.

---

# 7. Scenario: Test a username field accepting 5–15 characters.

### Equivalence Partitions

```text
Less than 5 → Invalid
5–15 → Valid
Greater than 15 → Invalid
```

### Boundary Tests

```text
4 characters → Invalid
5 characters → Valid
6 characters → Valid
14 characters → Valid
15 characters → Valid
16 characters → Invalid
```

Additional tests:

```text
Empty
Spaces
Special characters
Unicode characters
Numbers
Alphanumeric
Leading spaces
Trailing spaces
Duplicate username
SQL injection strings
Very long input
```

---

# 8. Scenario: How would you test a password field?

I would first identify the password rules.

For example:

```text
Minimum 8 characters
At least one uppercase
At least one lowercase
At least one number
At least one special character
```

Then I would create positive, negative, boundary, and security-oriented scenarios.

### Examples

```text
Password123! → Valid
Pass123! → Invalid if minimum is 9
password123! → Invalid if uppercase required
PASSWORD123! → Invalid if lowercase required
Password! → Invalid if number required
Password123 → Invalid if special character required
```

I would also test:

* Copy/paste behavior
* Show/hide password
* Spaces
* Leading/trailing spaces
* Maximum length
* Browser autofill
* Password masking
* Error messages
* Account lockout behavior

---

# 9. What is Decision Table Testing?

Decision Table Testing is useful when application behavior depends on multiple conditions.

### Example

Suppose a customer gets a discount when:

```text
Customer is a member
AND
Order amount >= $100
```

Decision table:

| Member | Amount >= $100 | Discount |
| ------ | -------------- | -------- |
| Yes    | Yes            | Yes      |
| Yes    | No             | No       |
| No     | Yes            | No       |
| No     | No             | No       |

This gives systematic coverage of combinations.

---

# 10. Real-Time Scenario: How would you test an insurance premium calculation?

Suppose premium depends on:

* Age
* Driving history
* Vehicle type
* Location

I would create a decision table containing combinations of these conditions.

I would verify:

* Normal combinations
* High-risk combinations
* Low-risk combinations
* Boundary values
* Missing data
* Invalid combinations
* Changes to one condition while keeping others constant

I would also validate the calculated premium against the expected business rules.

---

# 11. What is State Transition Testing?

State Transition Testing verifies how an application behaves when moving from one state to another.

### Example: User Account

```text
Active
   ↓
Failed Login
   ↓
Failed Login
   ↓
Locked
```

If the system locks an account after 3 failed attempts:

```text
Attempt 1 → Active
Attempt 2 → Active
Attempt 3 → Locked
Attempt 4 → Locked
```

Important scenarios:

* Correct login after failed attempts
* Failed login count reset
* Lockout duration
* Unlock mechanism
* Password reset
* Admin unlock
* Login after account unlock

---

# 12. Scenario: How would you test an ATM?

I would identify different states and transitions.

### States

```text
Card Inserted
PIN Entry
Authenticated
Transaction Selection
Transaction Processing
Transaction Completed
Card Ejected
```

### Scenarios

* Valid card + valid PIN
* Valid card + invalid PIN
* Three incorrect PIN attempts
* Insufficient balance
* Invalid withdrawal amount
* Amount above daily limit
* ATM has insufficient cash
* Cancel transaction
* Card retained
* Network failure
* Power failure
* Timeout
* Cash dispensed but transaction fails
* Transaction debited but cash not dispensed

---

# 13. What is Use Case Testing?

Use Case Testing validates the application from the user's business-flow perspective.

### Example: Online Shopping

```text
Login
↓
Search Product
↓
Select Product
↓
Add to Cart
↓
Checkout
↓
Enter Address
↓
Select Payment
↓
Place Order
↓
Order Confirmation
```

Test both:

### Main Flow

Successful purchase.

### Alternate Flows

* Product unavailable
* Invalid address
* Payment declined
* Coupon invalid
* Session timeout
* Cart item removed
* Network interruption

---

# 14. Scenario: How would you test an e-commerce checkout?

I would divide testing into:

### Functional

* Add product
* Update quantity
* Remove product
* Apply coupon
* Select address
* Select shipping method
* Select payment method
* Place order

### Negative

* Invalid coupon
* Expired card
* Insufficient funds
* Missing address
* Out-of-stock product
* Invalid postal code

### Boundary

* Quantity = 0
* Quantity = 1
* Maximum quantity
* Maximum order amount

### Integration

* Payment gateway
* Inventory service
* Tax service
* Shipping service
* Order service

### Recovery

* Payment succeeds but order creation fails
* Order created but confirmation notification fails
* Network disconnect during payment

---

# 15. What is Error Guessing?

Error Guessing uses tester experience and knowledge of common failure patterns to identify likely defects.

Examples:

For a login page, I would try:

```text
Blank username
Blank password
Both blank
Very long username
Very long password
Special characters
Spaces
Invalid credentials
Expired password
Locked account
Multiple rapid login attempts
```

This technique is especially useful when combined with formal test design techniques.

---

# 16. What is Pairwise Testing?

Pairwise Testing reduces the number of combinations while ensuring that every pair of parameter values is tested.

### Example

Suppose an application supports:

```text
Browser:
Chrome
Firefox
Edge

OS:
Windows
macOS
Linux

Language:
English
French
Spanish
```

Testing every combination requires:

```text
3 × 3 × 3 = 27 combinations
```

Pairwise testing can significantly reduce the number of combinations while still covering interactions between pairs of parameters.

---

# 17. Scenario: How do you test a system supporting many browsers, OS versions, and devices?

I would not blindly test every possible combination.

I would:

1. Identify supported combinations.
2. Review production usage.
3. Identify high-risk combinations.
4. Use pairwise testing.
5. Prioritize customer-critical platforms.
6. Execute smoke testing across the matrix.
7. Perform detailed regression on high-risk combinations.

Example:

```text
Chrome + Windows
Chrome + macOS
Firefox + Windows
Firefox + macOS
Edge + Windows
Safari + macOS
```

Then expand coverage based on risk and production usage.

---

# 18. How do you identify test scenarios from a requirement?

I normally follow this approach:

```text
Requirement
    ↓
Business Rules
    ↓
Positive Scenarios
    ↓
Negative Scenarios
    ↓
Boundary Conditions
    ↓
Validation Rules
    ↓
Integration Scenarios
    ↓
Error Handling
    ↓
Security Considerations
    ↓
Usability / Accessibility
    ↓
Test Data
```

---

# 19. Scenario: Requirement says "User can transfer money."

How would you derive test cases?

I would ask questions such as:

* From which account?
* To which account?
* Minimum transfer amount?
* Maximum transfer amount?
* Daily transfer limit?
* Supported currencies?
* Same-bank transfer?
* External-bank transfer?
* Scheduled transfer?
* Authentication required?
* OTP required?
* What happens when balance is insufficient?
* What happens if the receiving account is invalid?
* What happens if the network fails?
* Is the transaction reversible?

Then I would design positive, negative, boundary, security, integration, and recovery scenarios.

---

# 20. What is Risk-Based Test Case Design?

Risk-Based Testing prioritizes testing based on:

```text
Business Impact × Probability of Failure
```

High-risk areas receive more testing attention.

### Example

For a banking application:

| Feature         | Risk      |
| --------------- | --------- |
| Money Transfer  | Very High |
| Login           | High      |
| Balance Display | High      |
| Profile Photo   | Low       |
| Theme Selection | Very Low  |

I would prioritize money transfer and authentication before low-impact UI features.

---

# 21. Scenario: You have only two hours for regression. What will you test?

I would not attempt complete regression.

I would perform risk-based testing.

### Priority

```text
1. Application launch
2. Login
3. Critical business flow
4. Payment / transaction
5. Core APIs
6. Database-related functionality
7. Major integrations
8. Recently changed functionality
9. Previously defect-prone areas
10. Basic UI validation
```

I would communicate the reduced scope and associated risk to stakeholders.

---

# 22. How do you decide whether a test case is good?

A good test case should:

* Have a clear objective
* Contain clear preconditions
* Have well-defined test data
* Have precise steps
* Have expected results
* Be traceable to requirements
* Be reproducible
* Avoid unnecessary dependencies
* Validate one logical behavior

---

# 23. Scenario: Developer says your test case is invalid. What do you do?

I would not immediately argue.

I would:

1. Review the requirement.
2. Review acceptance criteria.
3. Understand the developer's interpretation.
4. Check business rules.
5. Reproduce the behavior.
6. Discuss with BA/Product Owner if ambiguity exists.
7. Update the test case if the requirement changed.
8. Document the final decision.

The goal is to establish the expected behavior rather than prove that one person is right.

---

# 24. Scenario: Requirement is incomplete. Should QA start testing?

I would start preparing test scenarios, but I would not make assumptions silently.

I would identify:

* Missing business rules
* Missing validation rules
* Missing error behavior
* Missing boundary conditions
* Missing integration expectations

Then I would raise questions with the BA/Product Owner.

This prevents defects caused by misunderstanding requirements.

---

# 25. Scenario: Login button accepts unlimited attempts. How would you test it?

I would investigate the security requirement first.

Possible scenarios:

```text
1 failed attempt
2 failed attempts
3 failed attempts
Maximum allowed attempts
Attempt after account lock
Correct password after failed attempts
Password reset after lock
Login from another device
Login after lock duration
Concurrent login attempts
```

I would also verify:

* Error messages
* Account lock state
* Audit logs
* Notification
* Rate limiting
* CAPTCHA if applicable

---

# 26. Scenario: Search box accepts a maximum of 50 characters.

Test cases:

```text
0 characters
1 character
49 characters
50 characters
51 characters
Very large input
Spaces only
Leading spaces
Trailing spaces
Special characters
Unicode
Numbers
Alphanumeric
SQL injection strings
HTML/script input
```

This combines boundary, equivalence, error guessing, and security-oriented testing.

---

# 27. Scenario: Dropdown contains 1000 values. How would you test it?

I would not manually validate every value unless required.

I would verify:

* Dropdown opens
* Search/filter works
* First value
* Last value
* Random representative values
* Duplicate values
* Sorting
* Keyboard navigation
* Scroll behavior
* Selection
* Clear/reset
* Invalid search
* Case sensitivity
* Performance
* Accessibility

For business-critical values, I would validate all required entries against the source data.

---

# 28. Scenario: Date field accepts dates from today to one year from today.

I would test:

```text
Yesterday → Invalid
Today → Valid
Tomorrow → Valid
One year minus one day → Valid
Exactly one year → Valid
One year plus one day → Invalid
```

Also:

```text
Leap year dates
Invalid dates
Different date formats
Manual entry
Calendar selection
Timezone differences
Past dates
Blank date
Copy/paste
```

---

# 29. Scenario: How would you test a file upload field?

I would test:

### Positive

* Valid file
* Supported extension
* Minimum valid size
* Maximum valid size

### Negative

* Unsupported extension
* Empty file
* Oversized file
* Corrupted file
* Duplicate file
* Malicious file name
* Special characters in filename

### Additional

* Multiple files
* Cancel upload
* Upload progress
* Network interruption
* Retry
* Remove uploaded file
* Drag and drop
* Browser compatibility

---

# 30. Scenario: How would you test a REST API without UI?

I would validate:

### Request

* HTTP method
* URL
* Headers
* Authentication
* Query parameters
* Path parameters
* Request body

### Response

* Status code
* Response body
* Schema
* Headers
* Response time
* Error messages

### Negative

* Missing mandatory field
* Invalid data type
* Invalid authentication
* Invalid token
* Invalid endpoint
* Unsupported method
* Boundary values

### Integration

* Database updates
* Downstream API calls
* Event/message generation

---

# 31. How do you design tests when requirements are not available?

I would use:

* Existing application behavior
* Business workflows
* User stories
* UI behavior
* API contracts
* Database rules
* Production defects
* Previous test cases
* Domain knowledge
* Exploratory testing

I would clearly document assumptions rather than treating assumptions as confirmed requirements.

---

# 32. What is the difference between a Test Scenario and a Test Case?

### Test Scenario

High-level condition to test.

Example:

```text
Verify user login functionality.
```

### Test Case

Detailed validation.

```text
Enter valid username.
Enter valid password.
Click Login.
Verify user is redirected to Dashboard.
```

---

# 33. Scenario: How many test cases are enough?

There is no fixed number.

Test coverage depends on:

* Risk
* Requirements
* Business criticality
* Complexity
* Input combinations
* User base
* Defect history
* Regulatory requirements
* Time available

The objective is sufficient risk-based coverage rather than maximizing the number of test cases.

---

# 34. How do you avoid duplicate test cases?

I review:

* Existing test cases
* Requirement coverage
* Scenario descriptions
* Preconditions
* Test data
* Expected results

I also group tests by functionality and use unique scenario IDs.

If two tests validate the same behavior with the same purpose, I consolidate them unless the difference is important for coverage.

---

# 35. Scenario: A requirement changes after test cases are written. What do you do?

I would:

```text
Requirement Changed
       ↓
Impact Analysis
       ↓
Identify Affected Tests
       ↓
Update Existing Tests
       ↓
Add New Scenarios
       ↓
Remove Obsolete Tests
       ↓
Review Traceability
       ↓
Execute Regression
```

I would also check whether existing defects or automation scripts are affected.

---

# 36. Senior-Level Interview Scenario

### Interviewer:

"You have a registration form with 20 fields. You have only one hour. How will you design your tests?"

### Strong Answer:

"I would first identify the critical business rules and mandatory fields. Then I would prioritize the registration flow using risk-based testing.

I would cover the happy path first, followed by mandatory-field validation, boundary values, invalid formats, duplicate registration, authentication-related behavior, and integration with downstream services.

For fields with ranges, I would use boundary value analysis. For fields with different categories of valid and invalid values, I would use equivalence partitioning. For combinations of conditions, I would use decision tables.

I would also review recent changes and historical defect-prone areas.

Because I only have one hour, I would focus on high-risk scenarios first and clearly communicate what was covered and what remains untested."

---

# 37. Senior-Level Scenario

### Interviewer:

"How would you test a banking application transfer feature?"

### Strong Answer:

"I would start with the business rules and identify the transaction lifecycle.

I would test valid transfers, insufficient balance, transfer limits, invalid beneficiary accounts, duplicate transfers, authentication and OTP, transaction status, failure handling, timeout scenarios, and network interruptions.

I would apply boundary value analysis to transfer limits and equivalence partitioning to transaction amounts.

I would also validate backend behavior, including account balance updates, transaction records, audit logs, notifications, and downstream integrations.

Because this is a high-risk financial feature, I would prioritize transaction integrity, security, data consistency, and recovery scenarios."

---

# 38. Senior-Level Scenario

### Interviewer:

"How do you know whether your test coverage is sufficient?"

### Strong Answer:

"I look at coverage from multiple perspectives rather than simply counting test cases.

I verify requirement coverage, business-flow coverage, positive and negative scenarios, boundary conditions, integration points, risk areas, historical defects, and platform coverage.

I also review code or API coverage when that information is available.

For critical functionality, I make sure the major failure and recovery scenarios are covered.

Ultimately, sufficient coverage means that the remaining risk is understood and acceptable to the business."

---

# 39. Common Mistakes in Test Case Design

Avoid:

* Testing only the happy path
* Ignoring boundary values
* Ignoring negative scenarios
* Creating duplicate test cases
* Writing overly long test cases
* Using unclear expected results
* Not validating error messages
* Ignoring integrations
* Ignoring historical defects
* Testing without understanding requirements
* Creating tests without traceability
* Focusing only on UI
* Ignoring data integrity
* Ignoring security considerations

---

# 40. Quick Interview Cheat Sheet

## Equivalence Partitioning

Divide inputs into logical groups.

```text
Valid
Invalid
```

## Boundary Value Analysis

Test values around boundaries.

```text
Min-1
Min
Min+1

Max-1
Max
Max+1
```

## Decision Table

Use when multiple conditions determine behavior.

```text
Condition A
Condition B
Condition C
        ↓
Expected Result
```

## State Transition

Use when behavior depends on current state.

```text
State A → Event → State B
```

## Use Case Testing

Validate complete business workflows.

```text
User Action → System Response → Next Action
```

## Error Guessing

Use experience to identify likely failures.

## Pairwise Testing

Reduce large combinations while covering important parameter interactions.

## Risk-Based Testing

Prioritize testing based on business impact and probability of failure.

---

# 41. Final Interview Strategy

When an interviewer gives you a scenario, don't immediately start listing random test cases.

Use this structure:

```text
1. Clarify the requirement
2. Identify business rules
3. Identify positive scenarios
4. Identify negative scenarios
5. Identify boundary values
6. Identify data variations
7. Identify integrations
8. Identify error handling
9. Identify security concerns
10. Identify recovery scenarios
11. Prioritize based on risk
12. Explain what you would test first
```

A senior QA engineer should demonstrate **structured thinking**, not simply produce a large number of test cases.

---

# Key Takeaway

The strongest Test Case Design interview answers demonstrate that you know **when and why to use a particular technique**.

Remember:

```text
Requirement
    ↓
Business Rules
    ↓
Equivalence Partitioning
    ↓
Boundary Value Analysis
    ↓
Decision Tables
    ↓
State Transitions
    ↓
Use Cases
    ↓
Negative / Error Guessing
    ↓
Integration
    ↓
Security
    ↓
Risk-Based Prioritization
```

This approach helps demonstrate senior-level QA thinking during real-time scenario-based interviews.
