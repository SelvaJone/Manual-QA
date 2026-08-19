# Manual QA Interview Questions

## Senior QA / SDET Interview Preparation

This document contains practical **Manual QA interview questions and answers** designed for Senior QA, QA Automation Engineer, SDET, and Test Engineer roles.

---

# 1. Manual Testing Fundamentals

## 1. What is Software Testing?

Software testing is the process of verifying and validating that a software application meets its requirements and behaves as expected.

The main goals are:

* Find defects before production.
* Verify business requirements.
* Validate user expectations.
* Reduce production risk.
* Ensure the application is reliable and usable.

### Example

For an e-commerce application, QA should verify:

* User registration
* Login
* Product search
* Product filtering
* Add to cart
* Checkout
* Payment
* Order confirmation
* Order cancellation
* Refund

---

## 2. What is the difference between Verification and Validation?

### Verification

Verification checks whether we are **building the product correctly**.

Examples:

* Requirement reviews
* Design reviews
* Code reviews
* Test case reviews

### Validation

Validation checks whether we are **building the correct product**.

Examples:

* Functional testing
* Integration testing
* System testing
* User acceptance testing

### Interview Answer

> Verification is primarily about reviewing work products without executing the application, while validation involves executing the software to confirm that it meets business and user requirements.

---

# 3. What is the difference between QA and Testing?

**QA (Quality Assurance)** is a broader process focused on preventing defects and improving the software development process.

**Testing** is one activity within QA focused on identifying defects in the product.

### Example

QA activities:

* Process improvement
* Requirement review
* Test strategy
* Quality standards
* Defect prevention

Testing activities:

* Test execution
* Functional testing
* Regression testing
* Exploratory testing
* Defect reporting

---

# 4. What is SDLC?

SDLC stands for **Software Development Life Cycle**.

Typical phases include:

1. Requirement gathering
2. Requirement analysis
3. Design
4. Development
5. Testing
6. Deployment
7. Maintenance

QA should ideally become involved during the **requirement phase**, not only after development is complete.

---

# 5. What is STLC?

STLC stands for **Software Testing Life Cycle**.

Typical phases are:

1. Requirement analysis
2. Test planning
3. Test case development
4. Test environment setup
5. Test execution
6. Defect reporting and tracking
7. Test closure

---

# 6. What is a Test Scenario?

A test scenario is a high-level condition or functionality that needs to be tested.

### Example

For a login page:

* Verify login with valid credentials.
* Verify login with invalid credentials.
* Verify login with blank username.
* Verify login with blank password.
* Verify password masking.
* Verify Forgot Password functionality.
* Verify account lockout.

---

# 7. What is a Test Case?

A test case contains detailed steps, test data, expected results, and other information required to verify a specific behavior.

### Example

**Test Case:** Verify successful login.

**Precondition:**

User has a valid registered account.

**Steps:**

1. Open the application.
2. Enter a valid username.
3. Enter a valid password.
4. Click Login.

**Expected Result:**

User should successfully log in and be redirected to the home page.

---

# 8. What is the difference between Test Scenario and Test Case?

| Test Scenario            | Test Case             |
| ------------------------ | --------------------- |
| High-level               | Detailed              |
| Describes what to test   | Describes how to test |
| Usually fewer scenarios  | Multiple test cases   |
| Useful for test coverage | Used for execution    |

### Example

**Scenario:**

> Verify login functionality.

**Test Cases:**

* Valid username + valid password
* Invalid username + valid password
* Valid username + invalid password
* Invalid username + invalid password
* Blank username
* Blank password
* Both fields blank
* Locked account

---

# 9. What is Functional Testing?

Functional testing verifies whether the application behaves according to functional requirements.

Examples:

* Login
* Registration
* Search
* Payment
* File upload
* Appointment booking
* Notifications

---

# 10. What is Non-Functional Testing?

Non-functional testing evaluates characteristics other than specific business functionality.

Examples:

* Performance
* Security
* Usability
* Accessibility
* Compatibility
* Reliability
* Scalability

---

# 11. What is Smoke Testing?

Smoke testing is a quick verification of critical functionality to determine whether a build is stable enough for detailed testing.

### Example

For a banking application:

* Application launches.
* Login works.
* Account information loads.
* Money transfer page opens.
* Logout works.

If critical functionality fails, the build may be rejected.

---

# 12. What is Sanity Testing?

Sanity testing is focused testing performed after a change or bug fix to verify that the specific functionality works and related areas have not been obviously broken.

### Example

A developer fixes the payment calculation.

QA might test:

* Correct payment amount.
* Discount calculation.
* Tax calculation.
* Order total.
* Payment confirmation.

---

# 13. Smoke Testing vs Sanity Testing

| Smoke                            | Sanity                        |
| -------------------------------- | ----------------------------- |
| Broad and shallow                | Narrow and deep               |
| Checks build stability           | Checks specific changes       |
| Usually performed on a new build | Usually after fixes/changes   |
| Covers critical functionality    | Covers affected functionality |

---

# 14. What is Regression Testing?

Regression testing verifies that existing functionality continues to work after code changes.

### Example

A developer changes the checkout module.

Regression testing may include:

* Product search
* Cart
* Pricing
* Discounts
* Checkout
* Payment
* Order confirmation
* Order history

The goal is to ensure the change did not break existing functionality.

---

# 15. Retesting vs Regression Testing

### Retesting

Retesting verifies that a previously failed test now passes after a defect has been fixed.

### Regression

Regression verifies that the fix did not introduce problems elsewhere.

### Example

Bug:

> User cannot complete payment using Visa.

After the fix:

**Retesting:**

Verify Visa payment works.

**Regression:**

Verify:

* Mastercard
* Amex
* PayPal
* Cart
* Order confirmation
* Refund

---

# 16. What is Exploratory Testing?

Exploratory testing is an approach where test design, execution, and learning happen simultaneously.

Instead of following only predefined test cases, QA explores the application based on risk, experience, and observations.

### Example

While testing a search field, you might try:

* Empty search
* Special characters
* Very long text
* Numbers
* Unicode characters
* SQL-like input
* Copy/paste
* Rapid repeated searches
* Browser refresh
* Network interruption

---

# 17. What is Ad Hoc Testing?

Ad hoc testing is informal testing without detailed predefined test cases.

The tester uses experience and intuition to identify potential defects.

### Difference

Exploratory testing is generally more structured and has a testing objective.

Ad hoc testing is more informal and spontaneous.

---

# 18. What is End-to-End Testing?

End-to-end testing validates a complete business workflow across multiple systems or components.

### Example: E-commerce

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
Payment
  ↓
Order Creation
  ↓
Email Notification
  ↓
Order History
```

The goal is to validate the complete customer journey.

---

# 19. What is Integration Testing?

Integration testing verifies communication between multiple components or services.

### Example

An application may communicate with:

```text
Mobile App
    ↓
API
    ↓
Customer Service
    ↓
Database
    ↓
Notification Service
```

QA verifies that the systems exchange data correctly.

---

# 20. What is System Testing?

System testing validates the complete integrated application against its requirements.

It generally occurs after integration testing and before acceptance testing.

---

# 21. What is UAT?

UAT stands for **User Acceptance Testing**.

Business users or customer representatives validate whether the application meets business needs.

### Example

A business stakeholder validates:

> Can a customer successfully schedule a service appointment?

If the workflow satisfies the business requirement, the feature can move toward production.

---

# 22. What is a Defect?

A defect is a difference between the expected behavior and actual behavior of the application.

### Example

Requirement:

> Password must contain at least 8 characters.

Actual behavior:

> Application accepts a 4-character password.

This is a defect.

---

# 23. What is a Defect Life Cycle?

A typical defect lifecycle is:

```text
New
 ↓
Assigned
 ↓
Open
 ↓
In Progress
 ↓
Fixed
 ↓
Ready for QA
 ↓
Retest
 ↓
Verified
 ↓
Closed
```

Possible alternate states include:

* Reopened
* Rejected
* Duplicate
* Deferred
* Cannot Reproduce
* Won't Fix

The exact workflow depends on the organization's process.

---

# 24. Severity vs Priority

### Severity

Severity represents the **technical/business impact** of the defect.

### Priority

Priority represents **how urgently the defect should be fixed**.

### Example 1

Application crashes when users click Login.

* Severity: Critical
* Priority: High

### Example 2

Company logo has a spelling mistake on the homepage.

* Severity: Low
* Priority: High

The defect may have low technical impact but high business visibility.

---

# 25. What is a Blocker Defect?

A blocker defect prevents QA or users from continuing testing or using a critical functionality.

### Example

The application cannot launch.

Or:

> Authentication service is completely unavailable, preventing all authenticated testing.

---

# 26. What information should a good Jira defect contain?

A good defect should include:

* Summary
* Environment
* Application version/build
* Preconditions
* Steps to reproduce
* Expected result
* Actual result
* Severity
* Priority
* Screenshots
* Video if useful
* Logs
* API request/response if applicable
* Device/browser information
* Test data
* Reproducibility

### Senior-Level Answer

> I try to make the defect independently reproducible so that the developer does not need additional clarification from QA.

---

# 27. What would you do if a developer says, "It works on my machine"?

I would avoid making the discussion personal.

I would provide objective evidence:

1. Environment details
2. Application version
3. Test data
4. Exact reproduction steps
5. Screenshots/video
6. Logs
7. API responses if relevant
8. Database evidence if applicable

Then I would work with the developer to determine whether the issue is:

* Environment-specific
* Data-specific
* Configuration-specific
* Browser/device-specific
* Actual application defect

---

# 28. What would you do if you cannot reproduce a defect?

I would:

1. Verify the original steps.
2. Check the environment.
3. Check test data.
4. Check application version.
5. Review logs.
6. Try different browsers/devices.
7. Check network/API behavior.
8. Ask the reporter for additional evidence.
9. Attempt to reproduce with the same data and conditions.

I would not immediately close the defect as invalid.

---

# 29. What is Boundary Value Analysis?

Boundary Value Analysis focuses on values at the boundaries of an input range.

### Example

Requirement:

> Age must be between 18 and 60.

Test:

```text
17
18
19
59
60
61
```

The boundary values are especially important because defects frequently occur around limits.

---

# 30. What is Equivalence Partitioning?

Equivalence partitioning divides input data into groups where values are expected to behave similarly.

### Example

Age:

```text
Invalid: < 18
Valid:   18–60
Invalid: > 60
```

Instead of testing every possible age, representative values can be selected.

For example:

```text
17 → Invalid partition
30 → Valid partition
61 → Invalid partition
```

---

# 31. How do you decide what to test when you have limited time?

I use a **risk-based testing approach**.

I prioritize:

1. Critical business functionality
2. Customer-facing functionality
3. Recently changed functionality
4. High-risk integrations
5. Areas with previous defects
6. Production-impacting workflows
7. Security-sensitive functionality
8. High-usage features

### Senior-Level Answer

> When time is limited, I don't simply execute fewer test cases randomly. I prioritize testing based on business impact, technical risk, change scope, defect history, and customer usage.

---

# 32. What would you test on a Login page?

I would consider:

### Positive Scenarios

* Valid username + valid password
* Valid credentials
* Remember Me
* Successful logout

### Negative Scenarios

* Invalid username
* Invalid password
* Both invalid
* Blank username
* Blank password
* Both blank

### Boundary Scenarios

* Minimum username length
* Maximum username length
* Minimum password length
* Maximum password length

### Security

* Password masking
* Account lockout
* Brute-force protection
* Session timeout
* Secure transmission
* Error-message behavior

### Usability

* Tab navigation
* Keyboard interaction
* Error messages
* Forgot Password
* Browser compatibility

---

# 33. Scenario: Login works, but users are randomly logged out. How would you investigate?

I would investigate systematically.

### Step 1: Reproduce

Determine:

* How frequently it occurs
* Which users are affected
* Which browsers/devices
* Whether it happens after inactivity
* Whether it happens during navigation

### Step 2: Check Session Behavior

Investigate:

* Session timeout
* Cookie expiration
* Token expiration
* Refresh token behavior
* Multiple login behavior

### Step 3: Check Network

Look for:

* 401 responses
* 403 responses
* Failed token refresh
* API failures

### Step 4: Check Server Logs

Look for:

* Authentication failures
* Session invalidation
* Token errors
* Backend exceptions

### Step 5: Compare Environments

Determine whether the issue occurs in:

* QA
* Stage
* Production

### Senior-Level Answer

> I would not assume the UI is responsible. I would trace the complete authentication flow from UI to network calls to token/session management and backend logs.

---

# 34. Scenario: A requirement is unclear. What would you do?

I would not immediately start writing test cases based on assumptions.

I would:

1. Identify the ambiguity.
2. Review related requirements.
3. Discuss it with the Product Owner/BA.
4. Document the clarification.
5. Update acceptance criteria if needed.
6. Design test scenarios based on the confirmed behavior.

### Example

Requirement:

> "User should receive a notification."

Questions:

* Which notification?
* Email, SMS, or push?
* When should it be sent?
* What happens if delivery fails?
* Is there a retry?
* What message should be displayed?

---

# 35. Scenario: Developer says the defect is not important. What do you do?

I would explain the impact using objective information.

For example:

> "The issue affects users in the checkout workflow and prevents approximately 30% of our supported payment methods from working."

Then I would discuss:

* Customer impact
* Business impact
* Frequency
* Scope
* Workaround
* Release impact

If disagreement remains, I would involve the appropriate Product Owner/QA Lead rather than turning it into a personal argument.

---

# 36. Scenario: You have 500 test cases but only 2 hours. What would you do?

I would perform risk-based prioritization.

### Priority 1

Critical business workflows:

* Login
* Core transaction
* Payment
* Data creation
* Data retrieval

### Priority 2

Recently modified functionality.

### Priority 3

High-risk integrations.

### Priority 4

Historically unstable functionality.

### Priority 5

Lower-risk UI and cosmetic areas.

I would communicate the reduced coverage and residual risk to the team.

---

# 37. Scenario: Production defect is reported. What do you do first?

I would first understand the impact and determine whether it is actively affecting customers.

Then:

1. Reproduce if possible.
2. Gather production evidence.
3. Identify affected users/workflows.
4. Determine severity.
5. Notify appropriate stakeholders.
6. Investigate logs/API/database behavior.
7. Support root-cause analysis.
8. Validate the fix.
9. Perform targeted regression.
10. Document the incident and prevention actions.

---

# 38. Scenario: A test passes in QA but fails in Production. What could be the reason?

Possible causes include:

* Environment configuration differences
* Different database data
* Feature flags
* API versions
* External service differences
* Authentication differences
* Infrastructure differences
* Browser/device differences
* Missing production configuration
* Race conditions
* Production-only data
* Scale/performance issues
* Caching
* Permissions

I would compare QA and production systematically rather than assuming the test was incorrect.

---

# 39. Scenario: You find a critical defect one hour before production release. What do you do?

I would immediately communicate the issue with:

* Clear defect description
* Business impact
* Reproduction steps
* Evidence
* Severity
* Affected functionality
* Potential workaround
* Release risk

Then I would work with Product, Development, and Release stakeholders to determine whether to:

* Fix before release
* Delay release
* Disable the affected feature
* Release with an accepted risk

As QA, my responsibility is to provide **accurate risk information**, not unilaterally make the business decision.

---

# 40. Scenario: How do you know when testing is complete?

Testing is not simply complete because all test cases passed.

I consider:

* Planned test coverage
* Critical scenarios executed
* Regression completed
* Known defects reviewed
* Critical/high defects resolved or accepted
* Requirements validated
* Risk assessed
* Production readiness reviewed
* Test environment stability
* Business acceptance

### Senior-Level Answer

> Testing is complete when the agreed exit criteria are satisfied and the remaining product risk is understood and accepted by the appropriate stakeholders.

---

# 41. Scenario: You discover many defects during regression. What would you investigate?

I would look for patterns.

Possible causes:

* Recent code changes
* Poor regression coverage
* Shared component changes
* Integration failures
* Environment problems
* Test data issues
* Inadequate unit/integration testing
* Configuration changes

I would also determine whether the defects are related to a common root cause.

---

# 42. Scenario: A feature works manually but automation fails. What do you check?

I would determine whether the problem is:

* Automation synchronization
* Locator issue
* Test data
* Environment
* Authentication/session
* API dependency
* Timing
* Browser/device difference
* Actual application defect

I would reproduce the same workflow manually and compare the automation's actions and network behavior.

---

# 43. Scenario: Automation passes locally but fails in CI. What would you investigate?

I would compare:

* Browser version
* Operating system
* Environment variables
* Secrets
* Test data
* Network access
* Time zone
* Parallel execution
* Resource availability
* Authentication state
* Headless vs headed behavior
* Dependency versions

I would also examine CI logs, screenshots, videos, and traces where available.

---

# 44. Scenario: How would you test a file upload feature?

I would test:

### Positive

* Valid file
* Supported file type
* Maximum allowed size
* Minimum valid file

### Negative

* Unsupported file type
* File larger than limit
* Empty file
* Corrupted file
* Duplicate file

### Security

* Malicious file
* Executable file
* Invalid extension
* Filename injection scenarios

### Usability

* Drag and drop
* Cancel upload
* Progress indicator
* Retry
* Multiple files
* Error messages

### Additional

* Network interruption
* Slow upload
* Refresh during upload
* Browser compatibility

---

# 45. Scenario: How would you test a search box?

I would test:

### Functional

* Exact match
* Partial match
* Case sensitivity
* Multiple words
* No results

### Boundary

* Empty input
* One character
* Maximum length
* Very long input

### Special Input

* Numbers
* Special characters
* Unicode
* Spaces
* Leading/trailing spaces

### Behavior

* Auto-suggest
* Search history
* Sorting
* Filtering
* Pagination

### Resilience

* Slow network
* API failure
* Timeout
* Repeated searches

---

# 46. Scenario: How would you test an appointment booking system?

I would think through the complete business workflow.

```text
Select Vehicle
     ↓
Select Service
     ↓
Select Dealer
     ↓
Select Date
     ↓
Select Time
     ↓
Select Transportation
     ↓
Review Appointment
     ↓
Confirm
     ↓
Appointment Created
```

I would test:

* Valid booking
* Invalid inputs
* No dealer available
* No appointment slots
* Slot becomes unavailable
* Double booking
* Time-zone differences
* Cancel appointment
* Reschedule
* Confirmation notification
* Duplicate submission
* Network failure
* Session expiration

---

# 47. Scenario: Two users try to book the same appointment slot simultaneously. What should you test?

This is a concurrency scenario.

I would verify:

1. Both users see the available slot.
2. Both attempt to book it.
3. Only one booking succeeds.
4. The other receives an appropriate message.
5. Database state remains consistent.
6. No duplicate appointment is created.
7. Notifications reflect the correct booking.
8. UI reflects the updated availability.

This scenario may require coordination with API, database, and performance testing.

---

# 48. Scenario: The application becomes very slow. How would you investigate?

I would first determine:

* Which page is slow?
* Which API is slow?
* Is the issue consistent?
* Which environment?
* Which users?
* Which devices?
* What changed recently?

Then investigate:

```text
UI
 ↓
Browser Network
 ↓
API
 ↓
Backend Service
 ↓
Database
 ↓
External Services
```

I would use available logs, monitoring, browser network tools, API tools, and database queries to isolate the bottleneck.

---

# 49. Scenario: An API returns HTTP 200 but the UI displays an error. How would you investigate?

I would inspect:

1. API response body.
2. Response schema.
3. Required fields.
4. Business status inside the response.
5. UI parsing logic.
6. Console errors.
7. Network payload.
8. Backend logs.

HTTP 200 only means the HTTP request was successfully processed at the protocol level. It does not necessarily mean the business operation succeeded.

---

# 50. What makes someone a strong Senior QA engineer?

A strong Senior QA engineer does more than execute test cases.

They:

* Understand requirements deeply.
* Think about risk.
* Design effective test scenarios.
* Identify gaps early.
* Investigate failures systematically.
* Communicate clearly.
* Understand APIs and databases.
* Collaborate effectively with developers.
* Understand automation.
* Analyze production issues.
* Think from the customer's perspective.
* Make testing decisions based on evidence.
* Communicate release risk clearly.

### Strong Interview Answer

> "As a Senior QA engineer, I see my role as more than finding bugs. I try to identify risks early, understand the complete business workflow, challenge unclear requirements, investigate failures across UI/API/database layers, and provide the team with enough information to make informed release decisions."

---

# Interview Preparation Strategy

For scenario-based interviews, avoid giving only textbook definitions.

Use this structure:

```text
1. Understand the problem
2. Clarify requirements
3. Identify risks
4. Define test scenarios
5. Execute/prioritize tests
6. Investigate failures
7. Collect evidence
8. Communicate impact
9. Validate fixes
10. Perform regression
11. Assess release risk
```

## Senior QA Mindset

When answering scenario questions, demonstrate:

**Requirement Understanding → Risk Analysis → Test Design → Execution → Investigation → Communication → Validation**

This is much stronger than simply saying:

> "I will execute the test cases and report the bugs."

---

# Next Topics

The next documents in this Manual QA interview series can cover:

1. `Manual-QA-Scenario-Based-Questions.md`
2. `Manual-QA-Test-Case-Scenarios.md`
3. `Manual-QA-Bug-Scenarios.md`
4. `Manual-QA-Agile-Scenarios.md`
5. `Manual-QA-Production-Scenarios.md`
6. `Manual-QA-API-Scenarios.md`
7. `Manual-QA-Database-Scenarios.md`
8. `Manual-QA-Mobile-Testing-Scenarios.md`
9. `Manual-QA-Senior-QA-Leadership-Scenarios.md`
10. `Manual-QA-Mock-Interview.md`
