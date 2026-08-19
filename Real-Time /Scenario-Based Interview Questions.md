# Manual Testing – Real-Time / Scenario-Based Interview Questions

## 1. Requirement-Based Scenarios

### Q1. What would you do if a requirement is unclear?

**Answer:**

I would not start testing based on assumptions. I would first clarify the requirement with the BA, Product Owner, Developer, or relevant stakeholder.

My approach would be:

1. Identify exactly what is unclear.
2. Review related requirements, acceptance criteria, and existing functionality.
3. Ask specific questions rather than general questions.
4. Document the clarification.
5. Update the test scenarios based on the confirmed behavior.
6. Start testing only after the expected behavior is clear.

**Example:**

If the requirement says:

> "The user should be able to cancel an appointment."

I would clarify:

* Can the user cancel after the appointment date has passed?
* Is cancellation allowed within 24 hours?
* Is a cancellation confirmation required?
* Should the appointment status change to `Cancelled`?
* Should the user receive an email or push notification?
* What happens if cancellation fails?

This prevents defects caused by misunderstanding the requirement.

---

### Q2. What would you do if there are no requirements or documentation?

**Answer:**

I would use multiple sources to understand the expected behavior:

* Existing application behavior
* Business/Product Owner
* Developers
* Previous test cases
* API documentation
* Database information
* Production behavior
* Related user stories
* Existing automation tests

I would then document the assumptions and get confirmation from the appropriate stakeholder before finalizing the test scenarios.

---

### Q3. A developer says your defect is not a bug because the requirement is unclear. What would you do?

**Answer:**

I would avoid arguing based on personal opinion.

I would:

1. Review the requirement and acceptance criteria.
2. Demonstrate the actual behavior.
3. Explain the expected behavior and why I believe it differs.
4. Discuss it with the BA/Product Owner if necessary.
5. Get a business decision.
6. Update the requirement or defect accordingly.

**Senior-level approach:**

> "My goal is not to prove that the developer is wrong. My goal is to establish the correct expected behavior."

---

# 2. Functional Testing Scenarios

## Q4. You are asked to test a Login page. What scenarios would you cover?

**Answer:**

I would divide the testing into positive, negative, boundary, security, usability, and compatibility scenarios.

### Positive Scenarios

* Valid username + valid password
* Login with valid credentials
* Remember Me functionality
* Successful logout
* Login after password reset

### Negative Scenarios

* Invalid username
* Invalid password
* Both username and password invalid
* Blank username
* Blank password
* Both fields blank
* Locked account
* Inactive account

### Boundary Scenarios

* Minimum username length
* Maximum username length
* Minimum password length
* Maximum password length
* Special characters
* Spaces
* Very long input

### Security Scenarios

* Password masking
* SQL injection
* XSS input
* Brute-force protection
* Account lockout
* Session timeout
* Secure logout

### Usability

* Error message clarity
* Tab order
* Keyboard navigation
* Password visibility option
* Forgot Password link

### Compatibility

* Chrome
* Edge
* Firefox
* Safari
* Different screen resolutions
* Mobile browsers

---

# 3. Scenario-Based Testing

## Q5. How would you test an ATM?

**Answer:**

I would identify the major business flows first.

### Positive Scenarios

1. Insert valid card.
2. Enter valid PIN.
3. Select withdrawal.
4. Enter valid amount.
5. Verify cash is dispensed.
6. Verify balance is updated.
7. Verify transaction receipt.

### Negative Scenarios

* Invalid card
* Expired card
* Invalid PIN
* Multiple incorrect PIN attempts
* Insufficient balance
* Amount greater than withdrawal limit
* ATM has insufficient cash
* Network failure
* Card retained by ATM

### Boundary Scenarios

* Minimum withdrawal amount
* Maximum withdrawal amount
* Daily withdrawal limit
* Zero amount
* Negative amount
* Amount not supported by available denominations

### Integration Validation

I would also verify:

* Account balance
* Transaction record
* ATM transaction log
* Bank response
* Receipt information

---

## Q6. How would you test an e-commerce checkout flow?

**Answer:**

I would test the complete end-to-end business flow:

```text
Login
  ↓
Search Product
  ↓
Product Details
  ↓
Add to Cart
  ↓
Update Quantity
  ↓
Apply Coupon
  ↓
Checkout
  ↓
Enter Address
  ↓
Select Shipping
  ↓
Select Payment
  ↓
Place Order
  ↓
Payment Confirmation
  ↓
Order Confirmation
```

I would validate:

* Product price
* Quantity
* Taxes
* Discounts
* Shipping charges
* Total amount
* Inventory
* Address validation
* Payment success
* Payment failure
* Duplicate payment prevention
* Order creation
* Confirmation email
* Order history

I would also test refreshing the page, browser back button, session expiration, network failure, and duplicate clicks on **Place Order**.

---

# 4. Smoke Testing

## Q7. A new build is deployed. What would you test first?

**Answer:**

I would perform smoke testing before starting detailed functional or regression testing.

I would verify the critical application paths such as:

* Application launches
* Login works
* Main navigation works
* Core business functionality works
* Database connectivity works
* APIs required by the application are responding
* Critical pages load
* No major application crash occurs

If smoke testing fails, I would stop detailed testing and report the build as unstable.

---

## Q8. What is the difference between smoke and sanity testing?

**Answer:**

### Smoke Testing

Smoke testing verifies whether the **overall build is stable enough for detailed testing**.

Example:

```text
Application launches
Login works
Main pages load
Critical workflow works
```

### Sanity Testing

Sanity testing verifies whether a **specific change or bug fix is working correctly** without performing complete regression testing.

Example:

A developer fixes the appointment cancellation feature.

I would test:

```text
Create Appointment
       ↓
Cancel Appointment
       ↓
Verify Status = Cancelled
```

Then I may test a few related areas to make sure the fix did not obviously break surrounding functionality.

---

# 5. Regression and Retesting

## Q9. What is the difference between retesting and regression testing?

**Answer:**

### Retesting

Retesting verifies that a **specific defect has been fixed**.

Example:

```text
Bug:
User cannot cancel appointment.

Developer fixes it.

Retesting:
Try cancelling the appointment again.
```

### Regression Testing

Regression testing verifies that **existing functionality has not been impacted by the change**.

Example:

After fixing appointment cancellation, I would also verify:

* Create appointment
* Modify appointment
* View appointment
* Reschedule appointment
* Appointment history
* Notifications

---

## Q10. You have 500 regression test cases but only 4 hours. What would you do?

**Answer:**

I would not randomly select tests.

I would prioritize based on risk.

### Priority 1 – Critical Business Flows

* Login
* Core transaction
* Payment
* Order creation
* Appointment creation
* Data updates

### Priority 2 – Recently Changed Areas

Tests directly related to the code changes.

### Priority 3 – High-Risk Integrations

* APIs
* Database
* External services
* Payment systems
* Authentication

### Priority 4 – Lower-Risk Features

Less frequently used functionality.

I would communicate the reduced coverage and associated risk to the QA Lead/Product Owner.

**Senior-level answer:**

> "When time is limited, I use risk-based testing rather than pretending that complete regression coverage is possible."

---

# 6. Production Defect Scenarios

## Q11. A critical defect is discovered in production. What would you do?

**Answer:**

My first priority would be to understand the impact and help the team contain the issue.

I would:

1. Reproduce the issue if possible.
2. Determine affected users/features.
3. Collect logs, screenshots, timestamps, request/response information, and relevant data.
4. Determine severity and business impact.
5. Immediately notify the appropriate stakeholders.
6. Help identify a workaround if available.
7. Support developers with investigation.
8. Validate the fix in the appropriate environment.
9. Perform focused regression testing.
10. Verify the production fix.
11. Participate in root-cause analysis.

I would avoid assigning blame and focus on restoring functionality quickly.

---

## Q12. A defect cannot be reproduced in QA but is occurring in production. What would you do?

**Answer:**

I would compare the environments systematically.

I would check:

* Application version
* Configuration
* Database data
* User permissions
* Environment variables
* Feature flags
* API responses
* Browser/device
* Network conditions
* Region
* Language
* User account
* Production logs
* Timestamp
* Request/response payload

I would use production logs and monitoring tools to identify what happened instead of simply closing the defect as "not reproducible."

---

# 7. Severity vs Priority Scenarios

## Q13. Give an example of High Severity but Low Priority.

**Answer:**

Suppose an application crashes when the user accesses a rarely used administrative report.

The crash is technically severe because the application fails.

However, if:

* Only internal administrators use the feature
* The feature is rarely used
* There is a workaround
* No customer impact exists

the business priority may be lower.

---

## Q14. Give an example of Low Severity but High Priority.

**Answer:**

Suppose the company logo is incorrect on the homepage immediately before a major public launch.

Technically, it may be low severity because the application still functions.

But business priority could be high because:

* The homepage is highly visible.
* It impacts company branding.
* Customers will see it immediately.
* Marketing may depend on it.

---

# 8. Database Validation Scenarios

## Q15. The UI shows that a customer was successfully created. How would you validate it?

**Answer:**

I would verify the complete data flow:

```text
UI
 ↓
API
 ↓
Service
 ↓
Database
```

I would validate:

* Customer ID
* Name
* Email
* Account status
* Created timestamp
* Region
* Required fields
* Default values
* Relationships with other tables

I would also ensure that sensitive information is stored correctly and that no duplicate record was created.

---

## Q16. UI shows one value but the database contains another. What would you do?

**Answer:**

I would determine where the mismatch occurs.

I would compare:

```text
UI value
   ↓
API response
   ↓
Service/business logic
   ↓
Database value
```

For example:

```text
Database = "ACTIVE"
API = "ACTIVE"
UI = "INACTIVE"
```

This indicates that the issue is likely between the API response and UI rendering.

If:

```text
Database = "ACTIVE"
API = "INACTIVE"
```

I would investigate the service/API/business logic.

---

# 9. API + UI Integration Scenarios

## Q17. UI displays "Order Created Successfully," but the order is not in the database. Is this a defect?

**Answer:**

Yes, it is potentially a serious defect.

I would verify:

1. UI response.
2. API response/status code.
3. Request payload.
4. Backend logs.
5. Database transaction.
6. Asynchronous processing.
7. Message queue/event processing if applicable.
8. Whether the database query is checking the correct environment.

If the application reports success but the business transaction is not persisted, that can result in data loss or inconsistent system state.

---

## Q18. API returns HTTP 200 but the UI displays an error. What would you investigate?

**Answer:**

I would not assume that HTTP 200 means the business operation succeeded.

I would inspect:

* Response body
* Business status
* Error codes
* Response schema
* UI parsing logic
* Required fields
* Null values
* Mapping logic
* Browser console
* Network logs

For example:

```json
{
  "status": "FAILED",
  "message": "Unable to process request"
}
```

The HTTP status is 200, but the business operation failed.

---

# 10. End-to-End Business Scenarios

## Q19. How would you test a vehicle appointment booking system?

**Answer:**

I would test the complete business journey.

```text
Login
 ↓
Select Vehicle
 ↓
Enter/Verify VIN
 ↓
Select Service
 ↓
Search Dealer
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
Confirm Appointment
 ↓
Verify Appointment Created
```

I would validate:

* VIN validity
* Vehicle ownership
* Region
* Dealer availability
* Service availability
* Appointment slots
* Time zone
* Transportation options
* Confirmation
* Database record
* API response
* Notification
* Appointment history

I would also test negative cases such as unavailable dealers, expired slots, invalid VINs, network failures, and duplicate booking attempts.

---

# 11. Scenario: Application Is Slow

## Q20. Users report that every page takes more than 30 seconds to load. What would you do?

**Answer:**

I would first determine whether the issue is UI, API, database, network, or environment related.

I would measure:

```text
Browser
   ↓
API Response Time
   ↓
Backend Processing
   ↓
Database Query
   ↓
External Services
```

I would inspect:

* Browser network tab
* API response time
* Server logs
* Database query performance
* External API latency
* CPU/memory usage
* Network latency
* Monitoring dashboards

If the API itself takes 28 seconds, the UI is probably not the primary problem.

---

# 12. Scenario: Intermittent Failure

## Q21. A test passes 9 times and fails once. How would you investigate?

**Answer:**

I would treat it as an intermittent/flaky issue rather than immediately assuming the test is defective.

I would collect:

* Exact timestamp
* Test data
* Environment
* Browser/device
* Logs
* API request/response
* Screenshots/video
* Network conditions
* Database state

Then I would try to determine whether the problem is caused by:

* Race condition
* Timing issue
* Asynchronous processing
* Test data collision
* Environment instability
* Network failure
* Backend instability
* Actual application defect

I would reproduce it repeatedly and identify the pattern.

---

# 13. Scenario: Requirements Change Mid-Sprint

## Q22. The requirement changes after you have already completed testing. What would you do?

**Answer:**

I would perform an impact analysis.

I would identify:

* Existing test cases affected
* New test scenarios
* Regression areas
* Automation impact
* Test data impact
* API/database impact
* Schedule impact

Then I would communicate the additional testing effort and risks.

I would not simply modify one test case and assume everything is covered.

---

# 14. Scenario: Developer Fixes One Defect

## Q23. A developer says, "I only changed one line of code, so regression testing isn't necessary." How would you respond?

**Answer:**

The size of the code change does not necessarily determine the testing impact.

I would ask:

* What functionality does the code affect?
* Which components consume it?
* Are there shared services?
* Are there downstream integrations?
* Is the code used by multiple features?

A one-line change in a shared utility could impact many features.

I would perform risk-based regression around the affected functionality.

---

# 15. Scenario: Missing Test Data

## Q24. You cannot test a critical scenario because required test data is unavailable. What would you do?

**Answer:**

I would first determine whether I can safely create or generate the required data.

Possible options:

* Create test data through UI
* Use API
* Use approved database scripts
* Request data from the appropriate team
* Use existing test accounts
* Mock/stub external dependencies where appropriate

I would document the blocker and its impact instead of silently skipping the test.

---

# 16. Scenario: User Reports a Defect

## Q25. A customer reports that a feature is not working. What information would you collect?

**Answer:**

I would collect:

* User/account information
* Application version
* Environment
* Browser/device
* Operating system
* Region
* Language
* Steps performed
* Expected result
* Actual result
* Date/time
* Screenshots/video
* Error message
* Network/API information
* Relevant logs
* Test data

Then I would attempt reproduction and determine the scope and severity.

---

# 17. Scenario: Feature Works in One Region

## Q26. A feature works in the US but fails in Mexico. How would you investigate?

**Answer:**

I would compare regional configuration and data.

I would check:

* Region configuration
* API endpoints
* Dealer/service data
* Localization
* Currency
* Language
* Time zone
* Feature flags
* Database records
* Backend rules
* External integrations

For example, a dealer search failure in one region may be caused by missing regional database data rather than a UI defect.

---

# 18. Scenario: Language/Localization

## Q27. The application is configured for Spanish, but some screens still display English. What would you test?

**Answer:**

I would check:

* Translation files
* Missing translation keys
* Language configuration
* API-provided text
* Cached translations
* Browser/device language
* Region settings
* Dynamic messages
* Error messages
* Buttons and labels
* Notifications

I would also test switching:

```text
English → Spanish
Spanish → English
```

and verify that the complete application consistently reflects the selected language.

---

# 19. Scenario: Duplicate Submission

## Q28. A user clicks "Submit" twice quickly. Two records are created. Is this a defect?

**Answer:**

Usually, yes, if the business requirement expects only one transaction.

I would investigate:

* UI button disabling
* API idempotency
* Backend duplicate validation
* Database constraints
* Network retry behavior
* Request IDs/correlation IDs

The strongest solution may need to exist at the backend rather than relying only on disabling the UI button.

---

# 20. Scenario: Data Is Deleted

## Q29. A user deletes a record. What would you validate?

**Answer:**

I would validate:

### UI

* Confirmation dialog
* Correct record selected
* Success message
* Record removed from UI

### API

* Correct endpoint
* Correct ID
* Correct response
* Appropriate status code

### Database

* Record deleted or marked inactive
* Related records handled correctly
* Audit information maintained

### Business Rules

* Unauthorized users cannot delete
* Required records cannot be deleted
* Dependent records are handled correctly

---

# 21. Scenario: Browser Back Button

## Q30. How would you test browser Back/Forward navigation?

**Answer:**

I would test:

* Login → Dashboard → Back
* Form → Back without saving
* Checkout → Back
* Payment → Back
* Logout → Back
* Session expiration → Back
* Multiple-page workflows

I would especially verify that sensitive or completed transactions cannot be accidentally resubmitted by using browser navigation.

---

# 22. Scenario: Session Timeout

## Q31. How would you test session timeout?

**Answer:**

I would:

1. Login.
2. Remain inactive until timeout.
3. Attempt to access a protected page.
4. Verify the user is redirected appropriately.
5. Verify sensitive data is not accessible.
6. Attempt browser Back navigation.
7. Verify API calls require valid authentication.
8. Login again and verify normal operation.

---

# 23. Scenario: Defect Appears After Deployment

## Q32. Everything passed QA, but production has a defect. Does that mean QA failed?

**Answer:**

Not necessarily.

Production defects can happen because of:

* Environment differences
* Production-only data
* Configuration differences
* Uncovered scenarios
* Third-party integrations
* Scale/load differences
* Feature flags
* Deployment issues
* Infrastructure differences

However, I would still perform root-cause analysis to determine:

> "Why was this scenario not detected before production?"

The goal is to improve the testing process rather than simply assign blame.

---

# 24. Senior QA Decision-Making

## Q33. How do you decide what to test first?

**Answer:**

I use a combination of:

* Business criticality
* Risk
* Recent code changes
* Customer impact
* Frequency of use
* Integration complexity
* Defect history
* Regulatory/security impact

For example:

```text
Payment
   ↓
Authentication
   ↓
Core business transaction
   ↓
Major integrations
   ↓
Frequently used features
   ↓
Low-risk features
```

---

# 25. Scenario: No Time for Full Testing

## Q34. Product management asks you to sign off even though only 60% of testing is complete. What would you do?

**Answer:**

I would not simply say "yes" or "no."

I would communicate the risk clearly:

* What has been tested
* What has not been tested
* Known defects
* Business-critical areas covered
* Remaining high-risk scenarios
* Production impact
* Recommended mitigation

Then I would let the appropriate business stakeholder make the release decision based on documented risk.

**Strong interview statement:**

> "QA provides visibility into product quality and risk; the final business release decision should be made with awareness of that risk."

---

# 26. Scenario: Test Case Passes but Feature Is Wrong

## Q35. Your test case passes, but you believe the functionality is incorrect. What would you do?

**Answer:**

I would not mark the product as acceptable simply because the test case passed.

I would:

1. Review the requirement.
2. Validate the business intent.
3. Discuss it with the Product Owner/BA.
4. Create a defect if the behavior violates the expected business behavior.
5. Update the test case if the requirement or expected behavior has changed.

A test case is only as good as the requirement behind it.

---

# 27. Scenario: Critical Test Fails at the End of Release

## Q36. One critical test fails one hour before production deployment. What would you do?

**Answer:**

I would immediately determine:

* Is it reproducible?
* What functionality is affected?
* How many users are impacted?
* Is there a workaround?
* Is it a blocker?
* Is the failure caused by the environment?
* Is the failure related to the release?

I would communicate the risk immediately.

I would not hide the failure simply because the release deadline is approaching.

---

# 28. Scenario: Defect Priority Disagreement

## Q37. You mark a defect as High Priority, but the Product Owner says it is Low Priority. What would you do?

**Answer:**

I would explain the impact objectively using:

* Customer impact
* Business impact
* Frequency
* Revenue impact
* Workaround
* Release impact
* Regulatory/security impact

If the Product Owner still considers it low priority, I would document the decision and continue testing based on the agreed priority.

---

# 29. Scenario: Test Environment Is Unstable

## Q38. The QA environment keeps going down. How would you handle it?

**Answer:**

I would separate environment problems from application defects.

I would:

1. Record downtime.
2. Identify patterns.
3. Report environment issues.
4. Coordinate with DevOps/infrastructure.
5. Use logs to identify failures.
6. Continue testing unaffected areas where possible.
7. Track blocked test cases.
8. Communicate the impact on schedule and coverage.

I would not mark blocked tests as "Passed."

---

# 30. Final Senior-Level Scenario

## Q39. What makes you a strong QA engineer when requirements, time, and resources are limited?

**Answer:**

I focus on **risk, business impact, and communication**.

My approach is:

```text
Understand Requirement
        ↓
Identify Business-Critical Flows
        ↓
Analyze Risk
        ↓
Prioritize Testing
        ↓
Execute Positive + Negative + Boundary Scenarios
        ↓
Validate UI + API + Database
        ↓
Investigate Defects
        ↓
Perform Risk-Based Regression
        ↓
Communicate Coverage + Risks
        ↓
Provide Release Recommendation
```

A senior QA engineer should not only execute test cases.

They should be able to answer:

* What can fail?
* Who will be impacted?
* How likely is it?
* How severe is it?
* What should we test first?
* What evidence do we have?
* What risk remains?
* Is the product ready for release?

---

# Quick Interview Framework

When the interviewer gives you **any scenario**, use this structure:

```text
1. Understand the requirement
2. Identify positive scenarios
3. Identify negative scenarios
4. Identify boundary conditions
5. Identify business-critical scenarios
6. Check integrations
7. Validate API/database if applicable
8. Consider security
9. Consider compatibility
10. Consider error handling
11. Consider production impact
12. Prioritize based on risk
13. Communicate findings
14. Perform regression after fixes
```

## Golden Senior QA Answer

When you don't immediately know the answer, don't guess.

Say:

> "I would first understand the business requirement and expected behavior. Then I would analyze the risk, identify positive, negative, boundary, and integration scenarios, prioritize the critical flows, execute the tests, investigate failures using logs/API/database information where applicable, and communicate the remaining risk to the stakeholders."

This framework can be adapted to **almost any manual QA scenario-based interview question**.
