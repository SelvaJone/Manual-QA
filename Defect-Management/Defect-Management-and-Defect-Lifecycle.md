# Defect Management and Defect Lifecycle – Scenario-Based Interview Questions

## 1. What is defect management?

Defect management is the process of identifying, documenting, prioritizing, assigning, tracking, retesting, and closing defects throughout the software development lifecycle.

A typical defect management flow is:

```text
Defect Found
    ↓
Defect Logged
    ↓
Defect Triaged
    ↓
Assigned to Developer
    ↓
In Progress
    ↓
Fixed
    ↓
Ready for Retest
    ↓
QA Retest
    ↓
 ┌───────────────┐
 │               │
Pass           Fail
 │               │
 ↓               ↓
Closed        Reopened
```

---

# 2. What is the defect lifecycle?

The defect lifecycle represents the different states a defect passes through from discovery to closure.

Common states are:

* New
* Open
* Assigned
* In Progress
* Fixed
* Ready for Retest
* Retest
* Reopened
* Deferred
* Rejected
* Duplicate
* Cannot Reproduce
* Won't Fix
* Closed

The exact workflow depends on the organization's Jira or defect-management process.

---

# 3. Scenario: You find a defect during testing. What do you do?

### Answer

I would first reproduce the issue and confirm that it is a genuine defect.

Then I would:

1. Reproduce the issue consistently.
2. Check whether it already exists.
3. Collect evidence such as screenshots, videos, logs, request/response details, and timestamps.
4. Identify the affected environment/build.
5. Determine severity and suggest priority.
6. Create a detailed defect.
7. Link the defect to the appropriate requirement, user story, or test case.
8. Notify the appropriate developer/lead if the issue is critical.
9. Track the defect through its lifecycle.
10. Retest the fix when it becomes available.
11. Run regression around the impacted functionality.
12. Close the defect if the fix passes.

---

# 4. What information should a good defect contain?

A good defect should contain enough information for another person to reproduce and understand the issue.

Typical fields include:

```text
Defect ID
Summary
Description
Environment
Application Version / Build
Platform
Region
Preconditions
Steps to Reproduce
Expected Result
Actual Result
Severity
Priority
Attachments
Logs
Test Data
Device / Browser
API Request / Response if applicable
Frequency
Reproducibility
Related Story
Related Test Case
Assignee
```

### Example

```text
Summary:
Service appointment cannot be booked after selecting a preferred dealer.

Environment:
Stage

Build:
Android 3.5.0 (214)

Steps:
1. Login with valid customer.
2. Open Service.
3. Select Make an Appointment.
4. Select a dealer.
5. Select an available appointment.
6. Tap Continue.

Expected:
User should proceed to appointment confirmation.

Actual:
Continue button remains disabled and user cannot proceed.

Severity:
High

Priority:
High
```

---

# 5. What is the difference between severity and priority?

### Severity

Severity represents the **technical/business impact of the defect**.

### Priority

Priority represents **how urgently the defect should be fixed**.

| Severity | Priority | Example                                        |
| -------- | -------- | ---------------------------------------------- |
| Critical | High     | Application crashes for all users              |
| High     | High     | Payment cannot be completed                    |
| High     | Medium   | Important workflow partially fails             |
| Medium   | High     | Frequently used UI issue before release        |
| Low      | High     | Minor issue required for a contractual release |
| Low      | Low      | Cosmetic alignment issue                       |

Severity is usually recommended by QA based on impact, while priority is determined by the team/business based on urgency.

---

# 6. Scenario: A typo exists on the login page. Is it high or low severity?

Usually it would be **Low severity** because the application functionality is not affected.

However, priority could be high if:

* It is a customer-facing production release.
* It violates a legal requirement.
* It appears on a major marketing page.
* The business explicitly requires it before release.

This demonstrates why severity and priority are separate concepts.

---

# 7. Scenario: The application crashes when the user clicks Login. What severity would you assign?

Normally this would be **Critical or High severity**, depending on scope.

If all users are unable to log in, it could be Critical.

If only a specific edge case causes the crash, High may be more appropriate.

I would support the severity with business impact rather than assigning it simply because the application crashes.

---

# 8. What is a blocker defect?

A blocker defect prevents QA or the team from continuing meaningful testing.

### Example

The application cannot launch after a new build is deployed.

QA cannot execute most test cases, so the issue blocks testing.

---

# 9. Is every blocker defect a critical defect?

Not necessarily.

A blocker describes the **impact on testing or progress**, while critical severity describes the **impact on the application/business**.

For example:

* A broken test environment could block QA.
* But the application itself may not have a critical functional defect.

---

# 10. What is a duplicate defect?

A duplicate defect is an issue that has already been reported.

### Scenario

You discover that checkout fails.

Before creating a new Jira ticket, you search existing defects and find:

```text
PAY-1234 – Checkout fails for valid credit cards.
```

If your issue has the same root problem, you should add relevant evidence to the existing defect rather than creating another one.

---

# 11. What is a rejected defect?

A defect may be rejected when the team determines that it is not actually a product defect.

Possible reasons:

* Requirement works as designed.
* Incorrect test data.
* Environment problem.
* Configuration issue.
* User misunderstanding.
* Expected behavior.
* Already handled elsewhere.

QA should not argue based only on opinion. The requirement, acceptance criteria, design, and business behavior should be used as evidence.

---

# 12. Scenario: Developer says, "This is working as designed." What do you do?

I would not immediately argue.

I would:

1. Review the requirement.
2. Review acceptance criteria.
3. Check design documentation if available.
4. Reproduce the behavior.
5. Compare actual behavior with expected behavior.
6. Discuss it with the product owner/business analyst if the requirement is unclear.
7. Update the defect based on the agreed behavior.

If the current behavior is correct, I would close or reject the defect with appropriate comments.

---

# 13. What is "Cannot Reproduce"?

This status means the developer or another team member cannot reproduce the reported issue.

QA should provide additional information rather than simply reopening the argument.

Useful evidence includes:

* Exact test data
* Environment
* Build number
* Device
* OS version
* Browser version
* Timestamp
* Logs
* Network traces
* Video
* Screenshots
* API request/response
* Preconditions

---

# 14. Scenario: Developer cannot reproduce your defect. What do you do?

I would:

1. Reproduce it again.
2. Confirm the exact build/environment.
3. Capture a video.
4. Collect application logs.
5. Capture network/API information if relevant.
6. Provide test data.
7. Mention frequency.
8. Mention exact timestamp.
9. Verify whether the developer is using the same environment.
10. Pair with the developer if necessary.

If I can reproduce it consistently, I would provide strong evidence and continue investigation.

---

# 15. What is a reopened defect?

A defect is reopened when the reported issue still exists after the developer marks it as fixed.

### Example

Developer fixes:

```text
Login button issue
```

QA retests and finds the login button still fails.

QA changes:

```text
Fixed → Reopened
```

The defect goes back to development.

---

# 16. Scenario: Developer marks a defect as fixed, but you still see the problem. What do you do?

I would first verify:

* Correct build is installed.
* Correct environment is being tested.
* Latest code is deployed.
* Cache/data is not causing the issue.
* The original reproduction steps are followed.

If the issue still exists, I would reopen the defect with:

* Retest results
* Evidence
* Current build
* Exact steps
* Logs/screenshots/video

I would avoid reopening it without verifying the environment.

---

# 17. What is defect retesting?

Retesting means executing the failed test again after the defect has been fixed to verify that the specific defect is resolved.

### Example

Original defect:

```text
User cannot save profile changes.
```

After the fix:

```text
Repeat the exact steps and verify that profile changes can now be saved.
```

---

# 18. What is regression testing after a defect fix?

Regression testing checks whether the fix introduced problems in related or existing functionality.

For example, if a developer fixes:

```text
Payment calculation
```

QA should test not only the original payment scenario but also related areas such as:

* Discounts
* Taxes
* Refunds
* Order totals
* Payment confirmation
* Different payment methods

---

# 19. What is the difference between retesting and regression testing?

| Retesting                        | Regression Testing                      |
| -------------------------------- | --------------------------------------- |
| Verifies the specific defect fix | Verifies related/existing functionality |
| Focused                          | Broader                                 |
| Uses original failed scenario    | Uses impacted regression scenarios      |
| Confirms defect resolution       | Checks for side effects                 |

---

# 20. Scenario: Developer fixes one line of code. Do you still perform regression testing?

Yes.

The scope may be small, but I would perform risk-based regression.

I would identify:

* Directly impacted functionality.
* Related workflows.
* Shared components.
* APIs affected by the change.
* Database impact.
* UI areas using the same component.

The amount of regression should be proportional to the risk.

---

# 21. What is defect triage?

Defect triage is the process where the team reviews reported defects and determines:

* Validity
* Severity
* Priority
* Ownership
* Release impact
* Fix timeline
* Deferral decision

Participants can include:

* QA
* Developers
* Product Owner
* Business Analyst
* Engineering Lead
* Project Manager

---

# 22. Scenario: You have 20 open defects and the release is tomorrow. How do you prioritize them?

I would classify them based on business and technical risk.

First:

```text
Critical production-blocking defects
        ↓
High-impact business defects
        ↓
Major functional defects
        ↓
Medium-impact defects
        ↓
Cosmetic/minor defects
```

I would also consider:

* Number of affected users.
* Revenue impact.
* Security impact.
* Regulatory impact.
* Frequency.
* Workaround availability.
* Release scope.
* Customer visibility.

I would present the information to stakeholders rather than making a release decision independently.

---

# 23. Scenario: A critical defect is found one day before release. What do you do?

I would immediately communicate the issue to the relevant stakeholders.

I would provide:

```text
Impact
Severity
Affected functionality
Affected users
Reproduction rate
Business impact
Workaround
Evidence
Current environment/build
Recommended action
```

Then I would participate in triage.

Possible outcomes:

* Fix immediately.
* Delay release.
* Remove affected functionality.
* Release with approved workaround.
* Accept the risk with documented approval.

QA should provide objective risk information; the final release decision should follow the organization's governance process.

---

# 24. What is defect leakage?

Defect leakage occurs when a defect escapes one testing stage and is discovered in a later stage or by customers.

### Example

```text
QA Stage
   ↓
Defect not detected
   ↓
Production
   ↓
Customer reports issue
```

This is a production defect leakage.

---

# 25. What is defect escape?

Defect escape is similar to defect leakage and generally refers to defects that were not detected before moving to a later environment or release stage.

Teams analyze escapes to understand why the defect was missed.

---

# 26. Scenario: A customer finds a defect in production that QA missed. How do you respond?

I would avoid immediately blaming the tester.

I would investigate:

1. Why the defect occurred.
2. Why existing tests did not detect it.
3. Whether the requirement was covered.
4. Whether the test data represented the production scenario.
5. Whether the environment differed.
6. Whether automation coverage was missing.
7. Whether monitoring should have detected it.
8. Whether additional regression tests are required.

Then I would add appropriate test coverage to prevent recurrence.

---

# 27. What is root cause analysis for defects?

Root Cause Analysis identifies why the defect occurred rather than simply describing the symptom.

Common techniques include:

* 5 Whys
* Fishbone/Ishikawa
* Fault Tree Analysis
* Code analysis
* Requirement analysis

### Example

Problem:

```text
User cannot book an appointment.
```

Possible root cause:

```text
Incorrect dealer availability API mapping.
```

The visible UI problem is the symptom; the API mapping issue is closer to the root cause.

---

# 28. Scenario: The same type of defect keeps appearing. What do you do?

I would perform root cause analysis.

I would look for:

* Missing requirements.
* Incomplete test coverage.
* Repeated coding mistakes.
* Weak code review.
* Missing automation.
* Environment differences.
* Inadequate test data.
* Missing regression scenarios.

Then I would recommend preventive actions.

---

# 29. What is defect aging?

Defect aging measures how long a defect remains unresolved.

Example:

```text
Defect Created: August 1
Defect Closed: August 6

Age = 5 days
```

Defect aging helps identify defects that are remaining unresolved for too long.

---

# 30. Scenario: A high-severity defect has been open for two weeks. What do you do?

I would escalate based on the team's process.

I would review:

* Current owner.
* Reason for delay.
* Business impact.
* Workaround.
* Release impact.
* Dependencies.
* Planned fix date.

I would communicate the risk clearly and ensure the defect is visible during triage/status reporting.

---

# 31. What is defect density?

Defect density measures the number of defects relative to a size measure such as:

* Lines of code
* Function points
* Story points
* Modules
* Features

A simplified example:

```text
Defect Density =
Number of Defects / Size of Software
```

Example:

```text
20 defects / 100 story points
= 0.2 defects per story point
```

The exact measurement should be standardized within the organization.

---

# 32. What is defect rejection rate?

Defect rejection rate indicates how many reported defects were rejected compared with total reported defects.

```text
Defect Rejection Rate =
Rejected Defects / Total Reported Defects × 100
```

A high rejection rate may indicate:

* Poor defect reporting.
* Requirement misunderstanding.
* Incorrect test data.
* Duplicate reporting.
* Unclear requirements.

It should be investigated rather than used to blame QA.

---

# 33. What is defect reopen rate?

Defect reopen rate measures how frequently supposedly fixed defects are reopened.

```text
Reopen Rate =
Reopened Defects / Fixed Defects × 100
```

A high reopen rate can indicate:

* Incomplete fixes.
* Poor developer testing.
* Misunderstood requirements.
* Environment inconsistencies.
* Insufficient retesting.

---

# 34. Scenario: Developer says, "I already tested the fix. Close the ticket." What do you do?

I would explain that developer validation and independent QA verification serve different purposes.

I would verify the fix independently.

If the fix passes:

```text
Retest → Pass → Regression → Close
```

If it fails:

```text
Retest → Fail → Reopen
```

I would not close a defect without verifying it according to the team's process.

---

# 35. Scenario: The defect passes retesting but breaks another feature. What do you do?

I would:

1. Confirm the regression.
2. Capture evidence.
3. Identify the impacted feature.
4. Reopen the original defect if appropriate.
5. Create a separate defect if the new behavior is a distinct issue.
6. Link the defects.
7. Inform the developer and lead.
8. Execute additional impacted regression tests.

---

# 36. Should every defect have a separate ticket?

Not necessarily.

A separate defect should generally be created when the issue has:

* Different root cause.
* Different functionality.
* Different ownership.
* Different priority.
* Independent fix.

Multiple symptoms caused by the same underlying issue may belong in one defect, depending on the team's tracking standards.

---

# 37. Scenario: You find five UI issues on the same page. Do you create five defects?

It depends on the issues.

If they are independent:

```text
Defect 1 – Incorrect label
Defect 2 – Wrong alignment
Defect 3 – Missing button
Defect 4 – Incorrect validation
Defect 5 – Broken navigation
```

Separate defects provide better tracking.

If all five symptoms result from one common root cause, one defect may be more appropriate.

---

# 38. What is a defect workaround?

A workaround is an alternative method that allows the user to continue using the system despite a defect.

### Example

Problem:

```text
Search fails when using the browser's autocomplete.
```

Workaround:

```text
User can manually enter the complete value.
```

A workaround can influence priority and release decisions.

---

# 39. Scenario: A high-severity defect has a reliable workaround. Should it still block release?

Not automatically.

The team should consider:

* Business impact.
* Number of affected users.
* Workaround complexity.
* Customer experience.
* Frequency.
* Release commitments.
* Risk.

Severity alone should not determine release decisions.

---

# 40. What is a production defect?

A production defect is a defect discovered after the software has been released to customers or production users.

Production defects usually receive high attention because they directly affect real users and business operations.

---

# 41. Scenario: A production defect is reported by a customer. What should QA do first?

I would first assess:

```text
Is the issue reproducible?
How many users are affected?
What functionality is impacted?
Is there data loss?
Is there a security/business impact?
Is there a workaround?
Which production version is affected?
```

Then I would reproduce it in a safe environment and collect evidence.

---

# 42. How do you handle a production-critical defect?

A typical approach is:

```text
Production Issue
       ↓
Immediate Triage
       ↓
Impact Assessment
       ↓
Reproduction / Log Analysis
       ↓
Root Cause Investigation
       ↓
Fix
       ↓
Focused Validation
       ↓
Regression
       ↓
Production Deployment
       ↓
Post-Deployment Validation
```

Communication should remain clear throughout the process.

---

# 43. Scenario: You cannot reproduce a production issue. What do you do?

I would not close it simply because it cannot be reproduced.

I would investigate:

* Production logs.
* Monitoring dashboards.
* Request/response data.
* User/session information where permitted.
* Timestamps.
* Application version.
* Database state.
* Feature flags.
* Configuration.
* Region.
* Device/browser.
* Network conditions.

If possible, I would reproduce using production-like data in a non-production environment.

---

# 44. What is a hotfix?

A hotfix is an urgent software change intended to address a critical issue, commonly in production.

QA should perform focused validation of the fix and appropriate regression before or after deployment according to the organization's emergency-release process.

---

# 45. Scenario: A hotfix is released. What testing would you perform?

I would perform:

### 1. Fix validation

Verify the exact production issue.

### 2. Smoke testing

Verify critical application functionality.

### 3. Impacted regression

Test functionality related to the changed code.

### 4. Production validation

After deployment, verify the fix in production where appropriate.

---

# 46. What is defect containment?

Defect containment means preventing a defect from moving further through the lifecycle or reaching customers.

Examples:

* QA catches the issue before release.
* Feature flag disables the problematic feature.
* Deployment is stopped.
* A release is rolled back.
* A workaround is provided.

---

# 47. Scenario: A defect is discovered during final regression. What do you do?

I would immediately determine:

* Severity.
* Priority.
* Affected functionality.
* Release impact.
* Reproduction rate.
* Workaround.
* Fix complexity.

Then I would report it during release triage.

I would not hide the defect simply because the release date is close.

---

# 48. Scenario: Product owner asks you to close a known defect to meet the release date. What do you do?

I would document the actual status and risk.

I would explain:

```text
Current behavior
Expected behavior
Business impact
Affected users
Workaround
Risk of release
```

If the business formally accepts the risk, the defect can be moved to the organization's approved status such as:

```text
Deferred
Accepted Risk
Won't Fix
```

The defect should not be falsely marked as fixed or passed.

---

# 49. What is a deferred defect?

A deferred defect is a valid defect that will not be fixed in the current release or iteration.

Possible reasons:

* Low priority.
* Low business impact.
* Limited resources.
* Release deadline.
* Dependency on another feature.
* Planned redesign.

The reason and target release should be documented.

---

# 50. Scenario: A low-severity defect is deferred repeatedly. What do you do?

I would monitor its age and business impact.

If the defect becomes significant because:

* It affects more users.
* It creates customer complaints.
* It impacts a new feature.
* It becomes a compliance issue.
* The workaround is no longer effective.

I would raise it again during triage and recommend reprioritization.

---

# 51. How do you decide whether a defect is valid?

I compare:

```text
Requirement
    +
Acceptance Criteria
    +
Design / Expected Behavior
    +
Actual Behavior
```

If actual behavior does not meet the agreed expectation, the defect is likely valid.

If requirements are ambiguous, I clarify with the product owner or business analyst.

---

# 52. Scenario: Requirement and implementation disagree. What do you do?

I would determine which source represents the current approved behavior.

If the requirement says:

```text
User must enter numeric values.
```

but the application accepts alphabetic values, I would report the discrepancy.

If the product owner confirms the requirement has changed, I would update the requirement/test coverage and determine whether a defect is still appropriate.

---

# 53. What is defect traceability?

Defect traceability connects defects with:

```text
Requirement
   ↓
User Story
   ↓
Test Case
   ↓
Defect
   ↓
Fix
   ↓
Retest
```

This helps determine:

* Which requirements are affected.
* Which tests failed.
* Which defects remain open.
* Whether regression is required.

---

# 54. Scenario: A defect is fixed but the related test case is missing. What do you do?

I would create or update the test case so the scenario becomes part of the regression suite.

The goal is not just to verify today's fix but to prevent the same defect from returning.

---

# 55. What is a defect prevention strategy?

Defect prevention focuses on preventing defects rather than only detecting them.

Practices include:

* Requirement reviews.
* Design reviews.
* Code reviews.
* Static analysis.
* Test planning.
* Early test involvement.
* Automation.
* Risk-based testing.
* Root cause analysis.
* Regression suites.
* Production monitoring.

---

# 56. Scenario: The same defect appears after every release. How would you prevent it?

I would investigate why the existing process is not detecting it.

Possible actions:

```text
Root Cause Analysis
        ↓
Add Regression Test
        ↓
Automate Where Valuable
        ↓
Improve Test Data
        ↓
Improve Environment Validation
        ↓
Add Monitoring
        ↓
Review Release Checklist
```

---

# 57. How do you handle intermittent defects?

Intermittent defects require additional evidence.

I would record:

* Frequency.
* Exact timestamps.
* Environment.
* Test data.
* Device/browser.
* Network condition.
* Logs.
* API behavior.
* Database state.
* Correlation/request IDs where available.

I would look for patterns rather than treating each occurrence independently.

---

# 58. Scenario: An API returns 500 only once out of 20 attempts. Is it a defect?

Potentially yes.

Intermittent behavior can still represent a serious reliability problem.

I would determine:

* Failure rate.
* Conditions that trigger it.
* Backend logs.
* Request payload.
* Dependencies.
* Whether retries hide the issue.
* Customer impact.

The defect severity should be based on impact and reliability risk.

---

# 59. Scenario: UI shows an error, but backend API succeeds. How do you investigate?

I would isolate the layers:

```text
UI
 ↓
Frontend logic
 ↓
API request
 ↓
Backend
 ↓
Database / External service
```

I would verify:

* API request.
* API response.
* HTTP status.
* Response payload.
* Frontend parsing.
* Console errors.
* Network logs.
* UI state handling.

If the API succeeds but the UI displays an error, the defect may be in frontend processing.

---

# 60. Scenario: API fails but UI displays success. What is the defect?

This is potentially a serious data-integrity or user-trust issue.

The UI should normally represent the actual outcome of the transaction.

I would capture:

```text
Request
Response
HTTP status
UI behavior
Database state
Logs
```

Then report the mismatch with appropriate severity.

---

# 61. Scenario: Database update succeeds, but UI still shows old data. How do you investigate?

I would determine whether the problem is:

* UI caching.
* API response.
* Database synchronization.
* Backend processing.
* Incorrect query.
* Stale session.
* Event/message processing delay.

I would compare:

```text
Database
   ↓
Backend/API
   ↓
Network Response
   ↓
UI State
```

This helps isolate the layer causing the discrepancy.

---

# 62. How do you communicate a critical defect to stakeholders?

I keep the communication concise and evidence-based.

Example:

```text
Issue:
Users cannot complete service appointment booking.

Impact:
Appointment booking is blocked for affected users.

Environment:
Production

Frequency:
100% reproducible for the affected scenario.

Severity:
Critical

Workaround:
No reliable workaround identified.

Evidence:
Attached video, logs, and request/response details.

Recommendation:
Immediate triage before release continuation.
```

---

# 63. Scenario: Developer asks for more information about your defect. What should you provide?

I would provide:

* Exact steps.
* Test data.
* Environment.
* Build.
* Device/browser.
* Expected result.
* Actual result.
* Logs.
* Screenshots/video.
* API details if applicable.
* Timestamp.
* Frequency.
* Preconditions.

The objective is to make reproduction as easy as possible.

---

# 64. What makes a defect report effective?

A good defect should be:

### Clear

Anyone should understand the problem.

### Reproducible

The developer should be able to reproduce it.

### Specific

Avoid vague descriptions.

### Evidence-based

Include logs/screenshots/video where useful.

### Traceable

Link the relevant story, requirement, or test case.

### Actionable

The developer should know what needs investigation.

---

# 65. Bad defect vs. good defect

### Bad

```text
Login is not working.
Please check.
```

### Good

```text
Summary:
Login fails when a valid user enters a password containing a special character.

Steps:
1. Open Login.
2. Enter valid username.
3. Enter valid password containing @.
4. Click Login.

Expected:
User should be authenticated successfully.

Actual:
Login API returns 400 and the UI displays "Invalid credentials."

Environment:
Stage

Build:
3.5.0

Frequency:
100%

Evidence:
Attached network trace and screenshot.
```

---

# 66. Scenario: You find a defect but the test case itself is wrong. What do you do?

I would first determine the expected behavior from the approved requirement.

If the test case is incorrect, I would:

1. Validate the requirement.
2. Correct the test case.
3. Determine whether the application behavior is actually defective.
4. Avoid logging a false defect.
5. Communicate the test-case correction to the team.

---

# 67. Scenario: The requirement is missing. Can you raise a defect?

I would avoid making assumptions.

I would clarify the expected behavior with:

* Product Owner.
* Business Analyst.
* Technical Lead.
* Approved design/documentation.

If the team confirms the behavior, I would update the test case and determine whether a defect should be logged.

---

# 68. How do you handle defects found during exploratory testing?

I follow the same defect-management principles.

I document:

```text
Exploratory Test Objective
Test Conditions
Steps / Actions Performed
Observed Behavior
Expected Behavior
Evidence
Environment
Build
Impact
```

Exploratory testing does not mean informal defect reporting.

---

# 69. Scenario: You discover a defect outside your assigned module. What do you do?

I would report it if it is a genuine issue.

I would:

1. Verify the defect.
2. Collect evidence.
3. Identify the responsible component/team.
4. Create the defect.
5. Assign/link it according to team process.
6. Inform the relevant owner.

QA ownership should not prevent reporting legitimate product risks.

---

# 70. How do you handle defects across multiple teams?

I use clear ownership and traceability.

For example:

```text
Mobile App
    ↓
API Team
    ↓
Backend Service
    ↓
Database Team
```

I would identify where the failure occurs, provide evidence, and link dependent defects where necessary.

---

# 71. Scenario: A defect occurs only in one region. How do you report it?

The region should be explicitly included.

Example:

```text
Summary:
Dealer search fails for Hawaii region.

Region:
HI

Environment:
Stage

Platform:
iOS

Language:
English

Frequency:
100% for affected HI test data
```

Region-specific information is especially important for applications with different configurations, services, dealers, or business rules.

---

# 72. Scenario: A defect occurs only in one language. What information should you include?

Include:

* Language.
* Region.
* Device.
* OS.
* App version.
* User configuration.
* Exact translated text.
* Expected translation.
* Actual translation.
* Screenshots.

Example:

```text
Preferred Language: Spanish
Region: Mexico
Actual: English text displayed
Expected: Spanish text displayed
```

---

# 73. Scenario: Defect occurs only on Android but not iOS. How do you investigate?

I would compare:

```text
Android vs iOS
App versions
OS versions
UI implementation
API behavior
Device configuration
Permissions
Network behavior
```

I would determine whether the issue is:

* Platform-specific.
* Backend-related.
* Configuration-related.
* Data-related.

I would include the platform limitation clearly in the defect.

---

# 74. Scenario: A defect is fixed in Stage but fails in Production. What could be wrong?

Possible causes include:

* Different configuration.
* Different database data.
* Feature flags.
* Environment variables.
* API versions.
* Deployment mismatch.
* Missing migration.
* External service differences.
* Production-only data.
* Caching.

I would compare the environments rather than assuming the code fix itself is incorrect.

---

# 75. How do you decide the regression scope for a defect?

I consider:

```text
Changed Code
+
Affected Feature
+
Dependent Components
+
Shared Services
+
Business Risk
+
Historical Defects
```

Then I select targeted regression scenarios.

---

# 76. Scenario: A developer says only one field changed, so no regression is needed. Do you agree?

Not automatically.

A small code change can affect:

* Validation.
* API payloads.
* Database mapping.
* Shared components.
* Other workflows.

I would perform risk-based regression rather than assuming the change is isolated.

---

# 77. What is defect clustering?

Defect clustering means a relatively small number of modules often contain a large proportion of defects.

This is related to the Pareto principle.

For example:

```text
Module A → 40 defects
Module B → 8 defects
Module C → 5 defects
Module D → 3 defects
```

Module A deserves additional investigation and testing.

---

# 78. How can defect metrics help a QA team?

Defect metrics can help identify:

* Quality trends.
* High-risk modules.
* Process weaknesses.
* Release readiness.
* Defect aging.
* Reopen trends.
* Production escapes.
* Testing effectiveness.

Metrics should be used for improvement rather than individual blame.

---

# 79. What defect metrics would you present to management?

Depending on the project, I might report:

```text
Total Defects
Open Defects
Closed Defects
Critical/High Defects
Defect Aging
Defect Density
Reopen Rate
Defect Rejection Rate
Defect Leakage
Defect Escape Rate
Defects by Module
Defects by Release
Defects by Environment
```

I would focus on trends and risks rather than simply reporting large numbers.

---

# 80. Scenario: Number of defects increased significantly this sprint. Is that necessarily bad?

No.

A higher number of defects could mean:

* More testing was performed.
* Test coverage increased.
* New functionality was introduced.
* QA became more effective at detecting issues.

I would analyze the context and trend rather than concluding that quality automatically decreased.

---

# 81. Scenario: QA reports 100 defects, but developers say most are low quality. How do you respond?

I would review the defects objectively.

I would analyze:

* Rejection rate.
* Duplicate rate.
* Reproduction rate.
* Requirement clarity.
* Defect quality.
* Evidence completeness.

If QA reporting quality is poor, I would improve the defect-reporting process.

If developers are rejecting valid defects incorrectly, I would use requirements and evidence during triage.

---

# 82. Scenario: A defect is marked "Won't Fix." What does that mean?

It means the team has decided not to fix the defect, usually because:

* Business impact is low.
* Cost is too high.
* Behavior is acceptable.
* Feature is being removed.
* Fix introduces greater risk.
* Product direction has changed.

The decision should be documented.

---

# 83. Scenario: A defect is marked duplicate, but you believe it is different. What do you do?

I would compare:

* Reproduction steps.
* Expected behavior.
* Actual behavior.
* Environment.
* Root cause.
* Affected functionality.

If it is genuinely different, I would explain the distinction and request separate tracking.

---

# 84. Scenario: A defect happens only with production data. How do you test it safely?

I would avoid copying sensitive production data unnecessarily.

Instead I would:

* Use sanitized data.
* Mask sensitive information.
* Reproduce using equivalent synthetic data.
* Use controlled environments.
* Follow data-access and privacy policies.

The goal is to reproduce the condition without exposing sensitive customer information.

---

# 85. What is defect prioritization in Agile?

In Agile, defects are usually prioritized based on:

* Customer impact.
* Business value.
* Severity.
* Risk.
* Sprint/release commitments.
* Dependencies.
* Workaround availability.

Defects may be discussed during backlog refinement, sprint planning, daily discussions, or defect triage.

---

# 86. Scenario: You discover a critical defect during the last day of a sprint. What do you do?

I would immediately communicate it and create the defect.

Then the team decides whether to:

* Fix within the sprint.
* Move the story.
* Carry the defect forward.
* Change scope.
* Delay release.

I would provide test evidence and impact information.

---

# 87. How do you link defects with user stories in Jira?

Typically:

```text
User Story
   ↓
Test Case
   ↓
Defect
```

The exact Jira relationship depends on the team's workflow.

I would link the defect to the relevant story and, where supported, the failed test case.

---

# 88. What is a blocker vs. high-priority defect?

A blocker prevents meaningful progress.

A high-priority defect requires urgent attention but may not completely prevent testing or release.

Example:

```text
Blocker:
Application cannot start.

High Priority:
One important report cannot be generated.
```

---

# 89. Scenario: A defect is difficult to reproduce but has severe customer impact. Would you still prioritize it?

Yes.

Difficulty of reproduction does not automatically reduce business impact.

I would use:

* Production logs.
* Monitoring.
* Customer evidence.
* Telemetry.
* Request IDs.
* Frequency.
* Affected users.

The priority should reflect business risk.

---

# 90. What is a defect trend?

A defect trend shows how defect counts or characteristics change over time.

Example:

```text
Sprint 1 → 30 defects
Sprint 2 → 24 defects
Sprint 3 → 15 defects
Sprint 4 → 8 defects
```

A decreasing trend may indicate improving stability, but it should be evaluated alongside test coverage and scope.

---

# 91. Scenario: Defect count is zero before release. Is the product defect-free?

No.

Zero reported defects does not prove zero defects exist.

Possible reasons:

* Insufficient testing.
* Missing test coverage.
* Incorrect test data.
* Untested requirements.
* Environment limitations.
* Undetected defects.

Quality should be evaluated using multiple indicators.

---

# 92. What is defect escape analysis?

Defect escape analysis investigates why defects were not caught before reaching a later environment or production.

Questions include:

```text
Was the requirement covered?
Was there a test case?
Was the test executed?
Was test data correct?
Was the environment representative?
Was automation missing?
Was regression incomplete?
Was the defect introduced after testing?
```

---

# 93. Scenario: A production defect was caused by missing test data. What preventive action would you take?

I would:

1. Identify the missing data condition.
2. Create appropriate test data.
3. Add the scenario to test coverage.
4. Add automation if valuable.
5. Include the scenario in regression.
6. Review whether similar data conditions exist elsewhere.

---

# 94. Scenario: A production defect was caused by an environment configuration difference. What would you improve?

Possible improvements:

* Configuration validation.
* Environment parity checks.
* Deployment verification.
* Configuration-as-code.
* Automated smoke tests.
* Release checklists.
* Monitoring.
* Environment-specific test coverage.

---

# 95. Scenario: A defect is caused by a third-party API. Is it still your application's defect?

It depends on where the responsibility lies.

I would first establish:

```text
Our Request
      ↓
Third-Party Response
      ↓
Our Application Handling
```

If the third party returns an unexpected response but our application should handle it gracefully and does not, there may still be an application defect.

If the third party itself is failing, it may be an external dependency incident rather than an application defect.

---

# 96. Scenario: A defect occurs only under heavy load. How should it be handled?

I would provide:

* Load level.
* Number of users/requests.
* Duration.
* Response times.
* Error rate.
* Server/resource metrics.
* Logs.
* Environment.
* Expected performance criteria.

This may become a performance or scalability defect rather than a functional defect.

---

# 97. Scenario: A defect is caused by invalid input that users should never enter. Should QA report it?

Potentially yes.

Even if the input is invalid, the application should behave safely according to requirements.

For example:

```text
Invalid input
     ↓
Expected validation message
```

If instead:

```text
Invalid input
     ↓
Application crash
```

that should likely be reported.

---

# 98. Scenario: You find a security-related defect. What should you do?

I would follow the organization's security incident and vulnerability-reporting process.

I would avoid exposing sensitive details broadly.

I would provide the security team with appropriate evidence and follow the approved escalation path.

---

# 99. Scenario: You find a data-loss defect. What severity would you assign?

Potentially Critical or High, depending on:

* Number of users.
* Data affected.
* Recoverability.
* Business impact.
* Regulatory impact.
* Frequency.

Data loss generally represents significant risk and should be escalated quickly.

---

# 100. Scenario: You have one hour before release and find a critical defect. What do you do?

I would not ignore or hide the defect.

I would:

```text
1. Confirm the defect.
2. Determine scope and impact.
3. Capture evidence.
4. Notify stakeholders immediately.
5. Participate in release triage.
6. Identify workaround if available.
7. Support focused validation of any fix.
8. Perform targeted regression.
9. Provide an objective release-risk assessment.
```

The release decision should be made through the team's established approval process.

---

# 101. Senior-Level Scenario: Developer says the defect is caused by bad test data. How do you prove it?

I would reproduce using:

```text
Known-good data
Known-bad data
Production-like data
Boundary data
```

Then compare:

```text
Input
↓
API Request
↓
API Response
↓
Database State
↓
UI Behavior
```

If the application behaves correctly with valid data but fails only because the test data violates an agreed precondition, the reported defect may not be valid.

---

# 102. Senior-Level Scenario: The defect is not reproducible anymore. Should you close it?

Not automatically.

I would investigate:

* Build changes.
* Environment changes.
* Configuration changes.
* Data changes.
* Dependency changes.
* Feature flags.

If the team uses a status such as "Cannot Reproduce," I would document the investigation before closing or moving the defect according to process.

---

# 103. Senior-Level Scenario: A developer fixes the defect but introduces another issue. How do you handle it?

I would identify whether the new issue is:

* Directly related to the original fix.
* A separate defect.
* A regression.

Then I would:

1. Document the new behavior.
2. Capture evidence.
3. Link the issues.
4. Reopen the original defect if appropriate.
5. Create a separate defect if necessary.
6. Expand regression coverage.

---

# 104. Senior-Level Scenario: How would you handle a disagreement with a developer about severity?

I would make the discussion evidence-based.

I would explain:

```text
Affected functionality
+
Number of users
+
Business impact
+
Reproduction frequency
+
Workaround
+
Release impact
```

If we still disagree, I would involve the appropriate QA lead/product owner during triage.

The objective is correct risk classification, not winning an argument.

---

# 105. Senior-Level Scenario: How do you know when a defect is ready to close?

I would close it when:

* The fix is deployed to the correct environment.
* Original defect scenario passes.
* Required regression passes.
* No related blocker remains.
* Evidence is captured.
* Acceptance criteria are satisfied.
* The team's closure criteria are met.

---

# 106. What is a good defect closure comment?

Example:

```text
Retested on build 3.5.0 (214) in Stage.

Original issue is no longer reproducible.

Verified:
- Preferred dealer selection
- Appointment continuation
- Confirmation flow

Impacted regression scenarios passed.

Closing the defect.
```

---

# 107. What are common mistakes QA engineers make in defect management?

Common mistakes include:

* Logging defects without reproducing them.
* Missing environment details.
* Poor defect summaries.
* No evidence.
* Incorrect severity.
* Confusing severity and priority.
* Not checking duplicates.
* Closing without retesting.
* Reopening without verification.
* Not performing regression.
* Not linking requirements.
* Ignoring intermittent issues.
* Not communicating critical defects quickly.
* Treating metrics as individual performance measurements.

---

# 108. What are the qualities of a senior QA engineer in defect management?

A senior QA engineer should:

* Identify defects accurately.
* Understand business impact.
* Communicate clearly.
* Perform root cause analysis.
* Prioritize based on risk.
* Challenge assumptions professionally.
* Drive effective triage.
* Identify regression scope.
* Analyze production defects.
* Improve test coverage.
* Track quality trends.
* Help prevent recurring defects.

---

# 109. How would you explain your defect-management experience in an interview?

A strong answer could be:

> "In my projects, I follow the complete defect lifecycle from identification through closure. I first reproduce and validate the issue, check for duplicates, collect evidence, and create a detailed defect with severity and priority based on business impact. During triage, I work with developers, product owners, and other stakeholders to determine ownership and release impact. Once a fix is available, I perform retesting followed by risk-based regression. For production defects, I also analyze logs, API behavior, database state, and environment differences to identify the root cause. I focus not only on finding defects but also on preventing recurring defects by improving regression coverage and test scenarios."

---

# 110. Senior-Level Scenario: How do you demonstrate that you are not just a defect reporter?

A senior QA engineer should demonstrate ownership beyond defect creation.

I would explain that I:

```text
Find the defect
      ↓
Understand the business impact
      ↓
Provide actionable evidence
      ↓
Help isolate the root cause
      ↓
Drive triage
      ↓
Validate the fix
      ↓
Perform regression
      ↓
Identify missing coverage
      ↓
Prevent recurrence
```

This demonstrates quality ownership rather than simply counting defects.

---

# Quick Interview Revision

## Defect Lifecycle

```text
New
 ↓
Open
 ↓
Assigned
 ↓
In Progress
 ↓
Fixed
 ↓
Ready for Retest
 ↓
Retest
 ↓
Pass → Closed
Fail → Reopened
```

## Common Alternate States

```text
Duplicate
Rejected
Deferred
Cannot Reproduce
Won't Fix
Accepted Risk
```

## Severity vs Priority

```text
Severity = Impact

Priority = Urgency
```

## Retesting vs Regression

```text
Retesting
= Verify the specific fix

Regression
= Verify related/existing functionality
```

## Strong Defect Report

```text
Clear Summary
+
Environment
+
Build
+
Preconditions
+
Steps
+
Expected Result
+
Actual Result
+
Severity
+
Priority
+
Evidence
+
Logs
+
Test Data
```

## Senior QA Mindset

```text
Detect
  ↓
Validate
  ↓
Communicate
  ↓
Prioritize
  ↓
Investigate
  ↓
Retest
  ↓
Regress
  ↓
Prevent Recurrence
```

---

# Top 15 Questions to Practice First

1. Explain the complete defect lifecycle.
2. Difference between severity and priority?
3. How do you decide defect severity?
4. Developer says "Not a bug." What do you do?
5. Developer cannot reproduce your defect. What do you do?
6. What is the difference between retesting and regression testing?
7. How do you handle a critical defect just before release?
8. What is defect triage?
9. What is defect leakage?
10. How do you handle production defects?
11. How do you perform root cause analysis?
12. What defect metrics do you track?
13. What do you do when the same defect repeatedly returns?
14. How do you decide regression scope after a fix?
15. How do you handle disagreement with a developer about severity or priority?

---

# Final Interview Tip

For scenario-based QA interviews, avoid answering only with definitions.

Use this structure:

```text
Situation
   ↓
Investigation
   ↓
Evidence
   ↓
Risk / Impact
   ↓
Action
   ↓
Validation
   ↓
Prevention
```

For example:

> "First I would reproduce and validate the issue. Then I would collect evidence and determine the business impact. I would log the defect with appropriate severity and priority and discuss it during triage. After the fix, I would retest the original scenario and perform risk-based regression. If the issue escaped to production, I would also perform root cause analysis and add appropriate regression coverage to prevent recurrence."

This structure demonstrates **real-world QA ownership, technical investigation, communication, risk assessment, and quality mindset** rather than simply memorizing defect-management terminology.
