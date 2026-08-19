# Test Levels and Test Types – Scenario-Based Interview Questions

## 1. What are the different levels of software testing?

The major levels of software testing are:

1. **Unit Testing**
2. **Integration Testing**
3. **System Testing**
4. **Acceptance Testing**

### Interview Answer

> Unit testing validates individual components, integration testing validates interactions between components, system testing validates the complete application, and acceptance testing validates whether the system meets business and user requirements.

### Real-Time Scenario

Suppose an automotive application has:

* Mobile App
* Vehicle API
* Dealer Service API
* Database
* Notification service

I would typically validate:

* Individual methods/components → Unit Testing
* Mobile App ↔ API → Integration Testing
* Complete appointment booking flow → System Testing
* Business acceptance of the appointment feature → UAT

---

# 2. What is Unit Testing?

Unit testing validates the smallest testable unit of application code independently.

Examples:

* Method
* Function
* Class
* Component

Unit testing is usually performed by developers using frameworks such as JUnit, TestNG, NUnit, or similar tools.

### Scenario

A method calculates the total service cost:

```text
Service Cost = Labor + Parts + Tax
```

I would test:

* Valid values
* Zero values
* Negative values
* Boundary values
* Null values
* Decimal values

### Interview Answer

> Unit testing verifies individual pieces of code in isolation before they are integrated with other components.

---

# 3. What is Integration Testing?

Integration testing verifies communication and interaction between two or more components.

### Example

```text
Mobile App
    ↓
API
    ↓
Database
```

I would validate:

* Request is correctly generated
* API receives the request
* API processes the request
* Database is updated
* Correct response is returned
* Error handling works correctly

### Scenario

A user adds a vehicle to the application.

The flow is:

```text
App → Vehicle API → Vehicle Database → API Response → App
```

If the vehicle is saved in the database but the app does not display it, this could indicate an integration issue.

---

# 4. What is System Testing?

System testing validates the complete integrated application against functional and business requirements.

### Scenario

For a service appointment application:

```text
Login
  ↓
Select Vehicle
  ↓
Select Dealer
  ↓
Select Service
  ↓
Select Date
  ↓
Select Time
  ↓
Confirm Appointment
  ↓
Receive Confirmation
```

The entire workflow would be validated as a system-level test.

### Interview Answer

> System testing validates the complete integrated system from an end-user perspective against the specified requirements.

---

# 5. What is Acceptance Testing?

Acceptance testing determines whether the application is acceptable for business or customer use.

Common examples:

* UAT
* Business Acceptance Testing
* Operational Acceptance Testing
* Contract Acceptance Testing

### Scenario

A business team wants to verify that customers can successfully schedule a vehicle service appointment.

QA may execute functional testing first, and business users may perform UAT to confirm the workflow satisfies their business expectations.

---

# 6. What is UAT?

UAT stands for **User Acceptance Testing**.

It is performed to determine whether the system satisfies business requirements and is ready for business use.

### Scenario

The business requirement says:

> Customers must be able to schedule a service appointment with an available dealer.

During UAT, business users may validate:

* Dealer selection
* Service selection
* Available appointment slots
* Confirmation
* Cancellation
* Business rules

### Interview Answer

> UAT focuses on validating whether the product meets business needs and is acceptable to end users or business stakeholders.

---

# 7. What is Smoke Testing?

Smoke testing is a high-level validation performed to determine whether the build is stable enough for detailed testing.

### Typical Smoke Checks

* Application launches
* Login works
* Main navigation works
* Critical APIs respond
* Major functionality is accessible
* No blocking issue exists

### Scenario

A new mobile application build is provided to QA.

Before starting 500 regression test cases, I would verify:

```text
App Launch
Login
Vehicle Selection
Dealer Search
Appointment Creation
Logout
```

If login itself is broken, I would reject the build instead of spending hours executing detailed test cases.

---

# 8. What is Sanity Testing?

Sanity testing is focused testing performed after receiving a build containing specific changes or fixes.

### Scenario

Developer fixes:

> Dealer search does not return results for Hawaii dealers.

I would perform focused testing around:

* Hawaii dealer search
* Valid dealer
* Invalid dealer
* Partial dealer name
* Address search
* Nearby dealer search

I would also perform limited regression around related functionality.

### Smoke vs Sanity

| Smoke Testing                   | Sanity Testing                 |
| ------------------------------- | ------------------------------ |
| Broad and shallow               | Narrow and deep                |
| Build acceptance                | Change/fix validation          |
| Usually before detailed testing | Usually after specific changes |
| Covers critical functionality   | Covers affected functionality  |

---

# 9. What is Regression Testing?

Regression testing verifies that existing functionality has not been negatively affected by new changes.

### Scenario

A developer changes the appointment booking module.

I would test:

```text
Appointment Creation
Appointment Modification
Appointment Cancellation
Dealer Search
Service Selection
Vehicle Selection
Notifications
```

The objective is to identify unintended side effects.

### Interview Answer

> Regression testing ensures that recent code changes have not broken previously working functionality.

---

# 10. What is Retesting?

Retesting verifies that a previously failed defect has been fixed.

### Scenario

Defect:

> User cannot create an appointment when selecting a specific dealer.

Developer fixes the issue.

I execute the exact failed scenario again.

If it passes, the defect can be considered fixed.

### Retesting vs Regression

**Retesting:**

```text
Verify the specific defect fix
```

**Regression:**

```text
Verify surrounding and existing functionality
```

---

# 11. What is End-to-End Testing?

End-to-End testing validates a complete business workflow across all required systems.

### Scenario

Customer appointment workflow:

```text
Login
 ↓
Vehicle
 ↓
Dealer
 ↓
Service
 ↓
Appointment Slot
 ↓
Booking API
 ↓
Database
 ↓
Notification
 ↓
Confirmation
```

I would verify the entire journey rather than testing individual components separately.

---

# 12. What is Functional Testing?

Functional testing verifies that the application behaves according to functional requirements.

### Examples

For login:

* Valid username/password
* Invalid username
* Invalid password
* Empty username
* Empty password
* Locked account
* Password expiration

### Interview Answer

> Functional testing validates what the system does based on business and functional requirements.

---

# 13. What is Non-Functional Testing?

Non-functional testing validates characteristics such as:

* Performance
* Security
* Usability
* Reliability
* Compatibility
* Scalability
* Accessibility

### Scenario

A search feature works correctly functionally, but takes 30 seconds to return results.

Functionally it may pass.

From a performance perspective, it may fail.

---

# 14. What is Compatibility Testing?

Compatibility testing verifies whether the application works correctly across different environments.

Examples:

* Browsers
* Operating systems
* Mobile devices
* Screen resolutions
* Network conditions
* Database versions
* API versions

### Scenario

An application works correctly on:

```text
Chrome + Windows
```

but fails on:

```text
Safari + iPhone
```

This could be a compatibility issue.

---

# 15. What is Cross-Browser Testing?

Cross-browser testing verifies application behavior across different browsers.

Typical browsers:

* Chrome
* Edge
* Firefox
* Safari

### Scenario

A button works in Chrome but does not respond in Safari.

I would:

1. Reproduce the issue
2. Verify browser version
3. Check console errors
4. Compare behavior across browsers
5. Capture evidence
6. Report the defect with environment details

---

# 16. What is Cross-Platform Testing?

Cross-platform testing verifies application behavior across different operating systems or platforms.

### Example

```text
Windows
macOS
iOS
Android
```

### Scenario

A mobile application works correctly on Android but crashes on iOS when opening the appointment page.

I would isolate whether the problem is:

* OS-specific
* Device-specific
* Application-version-specific
* Network-specific
* Backend-related

---

# 17. What is Installation Testing?

Installation testing verifies whether the software can be installed correctly.

Validate:

* Fresh installation
* Upgrade
* Reinstallation
* Uninstallation
* Installation failure
* Insufficient storage
* Permissions
* Interrupted installation

### Scenario

A new mobile app version is released.

I would verify:

```text
Old Version → New Version
```

and:

```text
Fresh Install → Login → Core Functionality
```

---

# 18. What is Upgrade Testing?

Upgrade testing verifies that an existing installation can successfully move to a newer version without losing required functionality or data.

### Scenario

A user has version 3.4 installed and upgrades to version 3.5.

I would verify:

* App launches
* Existing login/session behavior
* Existing vehicles remain available
* Preferences remain intact
* Existing appointments remain accessible
* New functionality works
* No data corruption occurs

---

# 19. What is Usability Testing?

Usability testing evaluates how easily users can understand and use the application.

### Scenario

A user wants to schedule a service appointment.

If the user cannot understand which button starts the booking process, the application may have a usability problem even if the functionality technically works.

I would evaluate:

* Navigation
* Labels
* Button placement
* Error messages
* Readability
* User flow
* Consistency

---

# 20. What is Accessibility Testing?

Accessibility testing verifies that users with disabilities can use the application.

Examples:

* Screen reader support
* Keyboard navigation
* Color contrast
* Focus indicators
* Alternative text
* Accessible labels
* Text scaling

### Scenario

A button is visible but has no accessible label.

A screen-reader user may not understand what the button does.

That should be reported as an accessibility issue.

---

# 21. What is Performance Testing?

Performance testing evaluates application behavior under expected and abnormal workloads.

Types include:

* Load Testing
* Stress Testing
* Spike Testing
* Endurance Testing
* Volume Testing
* Scalability Testing

### Scenario

An API normally handles 100 requests per second.

During a major release, traffic increases to 1,000 requests per second.

I would validate:

* Response time
* Throughput
* Error rate
* CPU
* Memory
* Database performance
* System stability

---

# 22. What is Load Testing?

Load testing verifies system behavior under expected workload.

### Scenario

The requirement says:

> The application must support 10,000 concurrent users.

I would test the application with an expected workload and monitor:

* Response time
* Throughput
* Error percentage
* Resource utilization

---

# 23. What is Stress Testing?

Stress testing pushes the system beyond normal capacity to identify its breaking point.

### Scenario

If an application is expected to support 10,000 users, I may gradually increase the load:

```text
10,000
15,000
20,000
25,000
```

The objective is to determine:

* When performance degrades
* When errors begin
* How the system behaves under extreme load
* Whether recovery occurs after load decreases

---

# 24. What is Spike Testing?

Spike testing evaluates system behavior when load suddenly increases or decreases.

### Scenario

A notification causes a large number of users to open the application simultaneously.

Traffic suddenly increases from:

```text
1,000 → 20,000 users
```

I would verify whether the application remains stable.

---

# 25. What is Endurance Testing?

Endurance testing verifies system stability over an extended period.

### Scenario

The system normally operates continuously for several days.

I would run sustained load and monitor:

* Memory leaks
* CPU utilization
* Response time degradation
* Database connections
* Application stability

---

# 26. What is Recovery Testing?

Recovery testing validates whether the system can recover from failures.

### Scenario

During appointment booking, the backend becomes temporarily unavailable.

I would verify:

* Appropriate error message
* No duplicate appointment
* User can retry
* Transaction state remains consistent
* System recovers when backend becomes available

---

# 27. What is Security Testing?

Security testing validates whether the application protects data and functionality from unauthorized access.

Examples:

* Authentication
* Authorization
* Session management
* Input validation
* Data protection
* Access control

### Scenario

A user should only see their own vehicle information.

If User A can access User B's vehicle details by changing an ID in the request, this is a serious security defect.

---

# 28. What is Positive Testing?

Positive testing validates expected valid inputs and workflows.

### Example

For an age field:

```text
25
```

is valid input.

The application should accept it.

---

# 29. What is Negative Testing?

Negative testing validates how the application handles invalid or unexpected inputs.

### Example

For an age field:

```text
ABC
-10
999
Special characters
Blank
```

I would verify that the application rejects invalid input appropriately.

---

# 30. What is Boundary Value Testing?

Boundary Value Analysis focuses on values at the edges of valid ranges.

### Example

If the valid age range is:

```text
18–65
```

I would test:

```text
17
18
19
64
65
66
```

---

# 31. What is Equivalence Partitioning?

Equivalence Partitioning divides input data into groups expected to behave similarly.

### Example

If age must be between 18 and 65:

```text
Invalid: <18
Valid: 18–65
Invalid: >65
```

Instead of testing every possible value, I select representative values from each partition.

---

# 32. What is Exploratory Testing?

Exploratory testing involves simultaneous learning, test design, and execution.

### Scenario

A new feature is delivered with limited documentation.

Instead of waiting for complete test cases, I would:

1. Understand the feature
2. Identify risks
3. Explore important workflows
4. Try unexpected combinations
5. Record observations
6. Create defects
7. Document important scenarios

---

# 33. What is Ad Hoc Testing?

Ad hoc testing is informal testing without predefined detailed test cases.

### Scenario

After completing planned testing, I randomly explore:

* Buttons
* Navigation
* Unexpected inputs
* Back button
* Refresh
* Multiple tabs
* Session expiration

It can help identify defects that structured test cases may miss.

---

# 34. What is Alpha Testing?

Alpha testing is typically performed before the product is released to external users.

It is generally performed in a controlled environment by internal teams or selected users.

---

# 35. What is Beta Testing?

Beta testing involves releasing software to a limited group of external users before wider production release.

### Scenario

A company releases an application to 1,000 selected customers.

Their real-world feedback helps identify issues before general availability.

---

# 36. What is Recovery Testing vs Failover Testing?

### Recovery Testing

Focuses on whether the system can recover after failure.

### Failover Testing

Focuses on whether the system can switch to a backup system when the primary system fails.

### Scenario

Primary API server becomes unavailable.

If traffic automatically moves to a secondary server, that is failover.

If the system later restores normal operation after the primary server becomes healthy, that relates to recovery.

---

# 37. What is Regression Testing vs End-to-End Testing?

They are not the same.

### Regression Testing

Focus:

> Did the recent change break existing functionality?

### End-to-End Testing

Focus:

> Does the complete business workflow work across the entire system?

An E2E test can be part of a regression suite.

---

# 38. What is Smoke Testing vs Regression Testing?

### Smoke

```text
Is this build testable?
```

### Regression

```text
Did the recent changes break existing functionality?
```

### Scenario

A new build arrives.

First:

```text
Smoke Testing
```

If it passes:

```text
Functional Testing
Regression Testing
```

If smoke fails:

```text
Reject / Return Build
```

---

# 39. What is Sanity Testing vs Retesting?

### Retesting

Validates the exact defect fix.

### Sanity

Validates the fix/change and closely related functionality.

### Example

Bug:

> Dealer search fails for a specific region.

Retesting verifies the original failed scenario.

Sanity testing may additionally validate:

* Different dealers
* Different search criteria
* Different regions
* Related dealer selection functionality

---

# 40. A Developer Says "The Defect Is Fixed." What Will You Do?

I would not immediately close the defect.

I would:

1. Understand the defect
2. Review the developer's fix information
3. Deploy/obtain the correct build
4. Reproduce the original issue
5. Execute the failed scenario
6. Verify expected behavior
7. Perform relevant regression
8. Check related functionality
9. Update the defect

If everything passes, I would close the defect.

---

# 41. A New Build Has 500 Test Cases. How Will You Start?

I would prioritize testing.

### Step 1 – Smoke

Validate critical application functionality.

### Step 2 – Critical Business Flows

Execute high-priority workflows.

### Step 3 – Changed Areas

Test recently modified functionality.

### Step 4 – Regression

Run broader regression.

### Step 5 – Lower Priority

Execute remaining scenarios based on time and risk.

### Interview Answer

> I would use risk-based prioritization instead of executing all test cases randomly.

---

# 42. Production Has a Critical Defect. Which Testing Level Would You Perform?

It depends on the defect.

I would first reproduce the production issue in an appropriate lower environment if possible.

Then:

1. Perform focused validation
2. Verify the fix
3. Perform regression around the affected area
4. Execute critical smoke testing
5. Validate the production deployment

---

# 43. A Feature Works in QA but Fails in Production. What Would You Check?

I would compare:

* Application version
* Configuration
* Environment variables
* Database data
* API endpoints
* Feature flags
* Authentication
* Permissions
* Network
* External integrations
* Third-party services
* Deployment differences

I would also review application logs and monitoring data.

### Interview Answer

> I would avoid assuming the code is the only cause. I would compare the complete QA and production environments and use logs and monitoring to identify the difference.

---

# 44. A Developer Changes One Line of Code. Do You Need Regression Testing?

Yes, but the regression scope should be risk-based.

I would determine:

* What component changed?
* What functionality depends on it?
* What APIs are affected?
* What business flows use it?
* What integrations are impacted?

A one-line change in a shared authentication component could require significant regression.

A localized UI text change may require much less.

---

# 45. How Do You Decide the Scope of Regression Testing?

I consider:

* Code changes
* Business impact
* Risk
* Dependencies
* Historical defects
* Integration points
* Critical workflows
* Frequently used functionality
* Production impact

### Example

If payment processing changes, I would prioritize:

```text
Payment
Order Creation
Order Confirmation
Refund
Transaction History
Notifications
```

---

# 46. What Would You Do If There Is Not Enough Time for Full Regression?

I would use risk-based testing.

### Priority 1

Critical business flows.

### Priority 2

Changed functionality.

### Priority 3

High-risk integrations.

### Priority 4

Frequently used functionality.

### Priority 5

Lower-risk areas.

I would communicate the remaining test scope and associated risks to stakeholders.

---

# 47. How Would You Test a Login Feature?

I would cover multiple test categories.

### Functional

* Valid credentials
* Invalid username
* Invalid password
* Empty fields
* Locked account
* Password expiration

### Security

* Session management
* Authorization
* Brute-force protection
* Sensitive data exposure

### Usability

* Error messages
* Password visibility
* Keyboard navigation

### Compatibility

* Browsers
* Devices
* Operating systems

### Performance

* Login response time
* Concurrent logins

---

# 48. How Would You Test an Appointment Booking Feature?

I would test the complete workflow:

```text
Login
 ↓
Select Vehicle
 ↓
Select Dealer
 ↓
Select Service
 ↓
Select Date
 ↓
Select Time
 ↓
Confirm
 ↓
Receive Confirmation
```

I would also test:

* Invalid data
* No available slots
* Dealer unavailable
* Network interruption
* Session expiration
* Duplicate booking
* Cancellation
* Modification
* Notifications
* Different regions
* Different languages
* Different devices

---

# 49. How Would You Test a Mobile Application Across Regions?

I would create a region-based test matrix.

Example:

| Region | Language        | Platform    |
| ------ | --------------- | ----------- |
| US     | English         | Android/iOS |
| CA     | English/French  | Android/iOS |
| PR     | English/Spanish | Android/iOS |
| HI     | English         | Android/iOS |
| MX     | English/Spanish | Android/iOS |

I would validate region-specific:

* Business rules
* Content
* Dealers
* Languages
* APIs
* Currency
* Date formats
* Availability
* Legal/privacy content

---

# 50. A Test Case Passes, but the Business User Says the Feature Is Wrong. What Do You Do?

I would not simply argue that the test case passed.

I would:

1. Understand the business expectation
2. Review the requirement
3. Compare requirement vs implementation
4. Check whether the test case is outdated
5. Discuss with BA/product owner
6. Determine the expected behavior
7. Update the test case if necessary
8. Raise a defect if the implementation violates the requirement

### Senior-Level Answer

> A passing test case does not automatically mean the product is correct. The test case itself must be aligned with the current business requirement.

---

# 51. How Do You Explain Test Levels in an Interview?

A concise answer:

> I look at testing levels from component to business acceptance. Unit testing validates individual components, integration testing validates communication between components, system testing validates the complete application, and acceptance testing validates whether the product meets business expectations.

---

# 52. How Do You Explain Test Types in an Interview?

A concise answer:

> Test types describe what characteristic or behavior we are validating. Functional testing verifies business functionality, while non-functional testing covers areas such as performance, usability, security, compatibility, reliability, and accessibility. I select the appropriate test types based on requirements, risk, architecture, and business impact.

---

# 53. Senior QA Scenario: Requirements Are Incomplete. What Testing Will You Perform?

I would not wait indefinitely for perfect requirements.

I would:

1. Identify what is known
2. Review available documentation
3. Discuss gaps with BA/product owner
4. Identify assumptions
5. Perform exploratory testing
6. Identify risks
7. Create questions
8. Validate expected behavior
9. Document assumptions
10. Update test cases as requirements become clearer

---

# 54. Senior QA Scenario: A Critical API Is Down During Testing

I would first determine whether the API is intentionally unavailable or actually failing.

I would check:

* API health
* Status code
* Logs
* Network
* Authentication
* Environment
* Dependencies
* Recent deployments

If it is an environment issue, I would report it and continue with independent testing where possible.

I would avoid marking dependent test cases as application defects without evidence.

---

# 55. Senior QA Scenario: The Application Works Functionally but Is Extremely Slow

I would separate functional correctness from performance behavior.

I would collect:

* Response time
* API response time
* Page loading time
* Database response time
* CPU
* Memory
* Network latency

I would then identify where the delay occurs and raise a performance defect with measurable evidence.

---

# 56. Senior QA Scenario: A Defect Is Fixed but Another Feature Breaks

This is a classic regression issue.

I would:

1. Retest the original defect
2. Confirm the new failure
3. Identify the dependency
4. Determine whether the fix caused the regression
5. Document evidence
6. Link related defects if appropriate
7. Discuss the impact with the developer
8. Execute targeted regression after the next fix

---

# 57. Senior QA Scenario: Production Release Is Tonight and Testing Is Incomplete

I would immediately communicate:

* Completed testing
* Remaining testing
* Known defects
* Severity
* Business impact
* Risk
* Unvalidated areas
* Recommended release decision

I would prioritize:

```text
Critical business workflows
+
Changed functionality
+
High-risk integrations
+
Known defect fixes
```

I would never simply say "testing is incomplete" without explaining the associated risk.

---

# 58. Senior QA Scenario: How Do You Decide Which Test Types to Execute?

I consider:

```text
Requirements
+
Risk
+
Architecture
+
Business Criticality
+
Application Type
+
Recent Changes
+
Production History
```

For example:

### Banking Application

High priority:

* Security
* Functional
* Integration
* Performance
* Data integrity

### Mobile Application

High priority:

* Functional
* Compatibility
* Usability
* Network
* Installation/upgrade
* Performance

---

# 59. Real-Time Scenario: Smoke Test Fails After Deployment

Suppose login fails immediately after deployment.

I would:

1. Stop detailed testing
2. Capture evidence
3. Confirm whether the failure is reproducible
4. Check environment/configuration
5. Notify the development/DevOps team
6. Log a defect or deployment issue
7. Wait for a corrected build
8. Re-run smoke testing
9. Continue detailed testing only after the build is stable

### Key Interview Point

> A failed smoke test means the build may not be suitable for detailed testing.

---

# 60. Real-Time Scenario: Sanity Testing Passes but Regression Fails

This is possible because sanity testing has a narrow scope.

### Example

A developer fixes dealer search.

Sanity testing confirms:

```text
Dealer Search → PASS
```

But regression discovers:

```text
Appointment Booking → FAIL
```

This indicates the fix may have affected another area.

I would investigate the dependency and report the regression defect.

---

# 61. Real-Time Scenario: Retesting Passes but Regression Fails

This is one of the most common interview scenarios.

### Answer

> I would mark the original defect as fixed if the exact failed scenario now passes, but I would separately report the regression defect if another existing functionality has been impacted.

This clearly demonstrates the difference between retesting and regression.

---

# 62. Real-Time Scenario: Which Testing Would You Perform First After a Build Deployment?

My typical sequence would be:

```text
Build Deployment
      ↓
Smoke Testing
      ↓
Build Accepted?
   /       \
 No        Yes
 ↓          ↓
Reject    Functional Testing
            ↓
        Sanity/Focused Testing
            ↓
        Regression Testing
            ↓
        End-to-End Testing
            ↓
        Release Validation
```

The exact sequence may change depending on the project and release process.

---

# 63. Real-Time Scenario: How Would You Test a New Feature With No Existing Test Cases?

I would use a structured exploratory approach.

### Step 1

Understand the requirement.

### Step 2

Identify business-critical workflows.

### Step 3

Identify positive and negative scenarios.

### Step 4

Apply test design techniques:

* Boundary Value Analysis
* Equivalence Partitioning
* Decision Tables
* State Transition Testing

### Step 5

Explore unexpected behavior.

### Step 6

Document defects and test coverage.

### Step 7

Convert important scenarios into reusable regression cases.

---

# 64. What Is the Difference Between Test Level and Test Type?

This is a very common interview question.

### Test Level

Defines **where** testing occurs in the software lifecycle.

```text
Unit
Integration
System
Acceptance
```

### Test Type

Defines **what characteristic or behavior** is being tested.

```text
Functional
Performance
Security
Usability
Compatibility
Accessibility
Recovery
```

### Easy Way to Remember

> **Level = Where**

> **Type = What**

---

# 65. How Do You Choose Between Smoke, Sanity, Retesting, and Regression?

Use the situation.

| Situation                                   | Testing    |
| ------------------------------------------- | ---------- |
| New build received                          | Smoke      |
| Specific fix received                       | Retesting  |
| Small change/fix needs focused validation   | Sanity     |
| Verify existing functionality after changes | Regression |
| Complete business workflow                  | E2E        |
| Business acceptance                         | UAT        |

---

# 66. What Is the Most Important Testing Level for a QA Engineer?

There is no single universally most important level.

It depends on the project.

For a QA engineer working primarily with applications, **system and integration testing** may be particularly important because they validate real user workflows and interactions between services.

However, strong QA requires understanding all levels.

---

# 67. Can Smoke Testing Be Automated?

Yes.

Examples:

* Application launches
* Login
* API health
* Basic navigation
* Critical business flow

Automation is especially useful when smoke testing must be executed frequently after deployments.

---

# 68. Can Regression Testing Be Automated?

Yes, and regression testing is one of the strongest candidates for automation.

Good candidates include:

* Stable functionality
* Repetitive scenarios
* High-frequency tests
* Critical business flows
* Data-driven scenarios
* Cross-browser scenarios

However, not every regression test should be automated.

---

# 69. Should Every Test Case Be Automated?

No.

I would consider:

* Stability
* Repeatability
* Business value
* Maintenance cost
* Execution frequency
* Technical feasibility
* Test data complexity

Exploratory, usability, visual, and rapidly changing tests may benefit from manual testing.

---

# 70. What Is Risk-Based Testing?

Risk-based testing prioritizes testing based on the probability and impact of failure.

A simple model is:

```text
Risk = Probability × Impact
```

### Example

Payment processing:

```text
High Impact + High Probability
= Highest Priority
```

Minor cosmetic text:

```text
Low Impact + Low Probability
= Lower Priority
```

---

# 71. How Would You Prioritize Testing During a Critical Release?

I would prioritize:

1. Critical business workflows
2. Recent code changes
3. High-risk integrations
4. Customer-facing functionality
5. Production defect fixes
6. Security-sensitive areas
7. High-volume functionality
8. Lower-risk features

I would communicate the remaining risk rather than hiding incomplete coverage.

---

# 72. Scenario: A Feature Is Working in Android but Not iOS

I would first determine whether the issue is platform-specific.

I would compare:

* Application versions
* OS versions
* Device models
* API responses
* Configuration
* Permissions
* UI behavior
* Logs

Then I would reproduce the issue on multiple iOS devices if available.

If consistently reproducible only on iOS, I would report it as a platform-specific defect with complete environment information.

---

# 73. Scenario: A Feature Works in English but Fails in Spanish

I would perform localization testing.

I would verify:

* Translated text
* Missing translations
* Text truncation
* Button alignment
* Date formats
* Number formats
* Error messages
* Navigation
* Business rules
* Language switching

I would also verify that selecting English does not display Spanish content and vice versa.

---

# 74. Scenario: The Same Defect Appears in Multiple Regions

I would first determine whether the issue is:

* Global
* Region-specific
* Configuration-specific
* Data-specific
* Language-specific

I would test multiple regions and compare API/database data.

If the defect is common across regions, I would provide evidence showing the broader impact rather than logging duplicate defects unnecessarily.

---

# 75. Scenario: A Defect Happens Only With Specific Test Data

I would investigate whether the data itself is valid.

I would verify:

* Data format
* Data state
* Database records
* User permissions
* Region
* Environment
* Account state
* Dependencies

Then I would document the exact test data and preconditions required to reproduce the issue.

---

# 76. Scenario: You Have Only 30 Minutes Before Release

I would not attempt to execute the entire test suite.

I would perform a targeted risk-based validation:

```text
5 min  → Smoke
10 min → Critical changed functionality
10 min → Critical E2E workflow
5 min  → Known defect fixes / release checks
```

I would then communicate exactly what was tested and what remains unvalidated.

---

# 77. Scenario: Product Owner Says "Just Test the Happy Path"

I would validate the happy path first because it is business-critical.

However, I would also communicate the risk of not testing:

* Negative scenarios
* Boundary values
* Error handling
* Security
* Integration failures
* Compatibility

If time is limited, I would prioritize rather than completely ignore high-risk negative scenarios.

---

# 78. Scenario: Developer Says "It Works on My Machine"

I would respond professionally.

I would provide:

* Environment
* Application version
* Steps
* Test data
* Expected result
* Actual result
* Screenshots/video
* Logs
* API evidence if applicable

Then I would work with the developer to identify environmental differences.

The goal is to solve the problem, not prove someone wrong.

---

# 79. Scenario: QA Environment Is Unstable

I would first determine whether the issue is environmental or application-related.

I would document:

* Environment outage
* Failed services
* API availability
* Database availability
* Deployment state
* Frequency
* Impact

I would communicate the testing blockage and continue testing independent areas where possible.

---

# 80. Scenario: How Would You Explain Your Testing Approach as a Senior QA Engineer?

A strong answer is:

> I start by understanding the requirements, business workflows, architecture, dependencies, and risks. I identify the most critical areas and design functional and non-functional coverage accordingly. After deployment, I perform smoke testing to validate build stability, followed by focused testing of changes, retesting of defect fixes, and risk-based regression. I also validate important end-to-end workflows and cross-platform or integration scenarios where applicable. Before release, I communicate coverage, defects, remaining gaps, and overall release risk to stakeholders.

---

# Quick Interview Revision

## Test Levels

```text
Unit
  ↓
Integration
  ↓
System
  ↓
Acceptance
```

## Common Test Types

```text
Functional
Non-Functional
Smoke
Sanity
Regression
Retesting
E2E
Exploratory
Ad Hoc
Compatibility
Usability
Accessibility
Security
Performance
Recovery
Installation
Upgrade
```

## Most Important Comparisons

### Smoke vs Sanity

```text
Smoke  → Is the build stable?
Sanity  → Is the specific change/fix working correctly?
```

### Retesting vs Regression

```text
Retesting → Verify the defect fix
Regression → Verify existing functionality after changes
```

### Functional vs Non-Functional

```text
Functional     → What the system does
Non-Functional → How well the system behaves
```

### Test Level vs Test Type

```text
Test Level → WHERE we test
Test Type  → WHAT we test
```

### System vs End-to-End

```text
System Testing → Complete application/system behavior
E2E Testing    → Complete business workflow across dependencies
```

### Smoke vs Regression

```text
Smoke      → Build acceptance
Regression → Existing functionality validation
```

---

# Senior QA Interview Golden Rules

1. **Do not say you test everything equally.**
2. Use **risk-based prioritization**.
3. Always distinguish **retesting from regression**.
4. Understand the difference between **test levels and test types**.
5. Start a new build with **smoke testing**.
6. Validate fixes through **retesting**.
7. Validate surrounding functionality through **regression/sanity testing**.
8. Consider **business impact**, not only technical impact.
9. Include **negative, boundary, integration, and error scenarios**.
10. For production releases, communicate **coverage and residual risk**.
11. Use logs, API responses, database evidence, and monitoring when investigating issues.
12. Do not assume every failure is an application defect; first isolate **environment, data, configuration, network, and dependency issues**.
13. Automate stable, repetitive, high-value regression scenarios where practical.
14. Use exploratory testing when requirements are incomplete or when you need to discover unknown risks.
15. A senior QA engineer does not only execute test cases—they **identify risk, investigate failures, communicate impact, and protect the quality of the release**.
