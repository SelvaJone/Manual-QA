# Manual Testing – Defect Management & Bug Life Cycle Interview Questions

## 1. What is a defect?

A defect is a deviation between the expected behavior of an application and its actual behavior.

### Example

**Expected:**
User should be able to log in with valid credentials.

**Actual:**
Application displays "Invalid credentials" even though the username and password are correct.

This difference is a defect.

---

# 2. What is the difference between Error, Defect, Bug, Failure, and Incident?

| Term     | Meaning                                                             |
| -------- | ------------------------------------------------------------------- |
| Error    | Human mistake made during development or testing                    |
| Defect   | Problem introduced into the software                                |
| Bug      | Commonly used synonym for defect                                    |
| Failure  | Application does not perform the expected behavior during execution |
| Incident | Any unexpected event observed during testing                        |

### Interview Tip

In most real-world projects, **defect** and **bug** are used interchangeably.

---

# 3. What is the Defect Life Cycle?

The Defect Life Cycle describes the different states through which a defect passes from identification to closure.

### Typical Flow

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

If the defect still exists:

```text
Retest
 ↓
Failed
 ↓
Reopened
 ↓
Assigned
 ↓
Fixed
 ↓
Retest
```

---

# 4. Explain the defect life cycle in a real project.

Suppose QA finds that the **Login button does nothing** after entering valid credentials.

### Step 1 – New

QA creates a defect with:

* Summary
* Description
* Steps to reproduce
* Expected result
* Actual result
* Environment
* Severity
* Priority
* Screenshots
* Logs
* Video, if required

### Step 2 – Assigned

The defect is assigned to the appropriate developer/team.

### Step 3 – In Progress

Developer investigates the issue.

### Step 4 – Fixed

Developer implements a fix.

### Step 5 – Ready for QA

Developer moves the defect to a state indicating that QA can test the fix.

### Step 6 – Retest

QA executes the original reproduction steps.

### Step 7 – Verified

If the issue is fixed, QA verifies the result.

### Step 8 – Closed

QA closes the defect.

---

# 5. What is the difference between Severity and Priority?

This is one of the most common QA interview questions.

## Severity

Severity represents the **impact of the defect on the application**.

## Priority

Priority represents **how urgently the defect should be fixed**.

### Example

A company logo is incorrect on the home page.

* Severity: Low
* Priority: High

Why?

The functional impact is low, but the company may want the branding issue fixed immediately.

---

# 6. Give examples of Severity and Priority combinations.

| Severity | Priority | Example                                |
| -------- | -------- | -------------------------------------- |
| High     | High     | Application crashes during checkout    |
| High     | Low      | Rare crash in an obscure admin feature |
| Low      | High     | Wrong company name/logo on homepage    |
| Low      | Low      | Minor alignment issue                  |

---

# 7. Can a defect have High Severity and Low Priority?

Yes.

### Example

An application crashes when an administrator uses a rarely used legacy feature.

The impact is technically high because the application crashes.

However, because the functionality is rarely used and not required for the current release, the business may assign low priority.

---

# 8. Can a defect have Low Severity and High Priority?

Yes.

### Example

The company's legal disclaimer contains incorrect information on the login page.

The application still functions, so severity may be low.

However, because the content has legal/business importance, priority may be high.

---

# 9. What information should a good defect report contain?

A good defect report should contain:

1. Defect ID
2. Summary
3. Description
4. Environment
5. Build/version
6. Preconditions
7. Steps to reproduce
8. Test data
9. Expected result
10. Actual result
11. Severity
12. Priority
13. Attachments
14. Logs
15. Screenshots/video
16. Reproducibility
17. Component/module
18. Browser/device/OS information

---

# 10. How do you write a good defect summary?

The summary should be:

* Short
* Clear
* Specific
* Action-oriented
* Easy to understand

### Bad

```text
Login issue
```

### Good

```text
Login fails with valid credentials after password reset
```

### Better

```text
Login displays "Invalid credentials" for valid credentials after password reset
```

---

# 11. What are good steps to reproduce?

Steps should allow another person to reproduce the issue without asking unnecessary questions.

### Example

```text
1. Launch the application.
2. Navigate to Login.
3. Enter a valid username.
4. Enter a valid password.
5. Click Login.
6. Observe the result.
```

Avoid:

```text
Login and check.
```

---

# 12. What is a blocker defect?

A blocker defect prevents further testing or prevents a critical business flow from continuing.

### Example

The application cannot launch after a new deployment.

QA cannot execute any functional test cases.

Therefore, this can be considered a blocker.

---

# 13. What is a Critical defect?

A critical defect causes severe business or system impact.

Examples:

* Application crashes during payment
* Data corruption
* Security vulnerability
* Complete checkout failure
* Loss of customer information

---

# 14. What is a Major defect?

A major defect significantly impacts functionality but does not necessarily bring down the entire application.

### Example

Users cannot create a new appointment, but existing appointments can still be viewed.

---

# 15. What is a Minor defect?

A minor defect has limited functional or UI impact.

Examples:

* Minor alignment issue
* Incorrect spacing
* Small font inconsistency
* Non-critical UI issue

---

# 16. What is a Cosmetic defect?

A cosmetic defect affects presentation rather than functionality.

Examples:

* Incorrect font size
* Misaligned icon
* Slight spacing issue
* Incorrect color
* Typographical error

---

# 17. What is a Rejected defect?

A defect may be rejected when the development team determines that it is:

* Not a valid defect
* Working as designed
* Not reproducible
* Duplicate
* Outside the agreed scope

### Important

QA should not immediately assume the developer is wrong.

The tester should review the requirement, acceptance criteria, and expected behavior.

---

# 18. What is a Duplicate defect?

A duplicate defect is an issue that has already been reported.

### Example

QA-101:

```text
Checkout fails when clicking Pay.
```

QA-125:

```text
Payment button does not complete checkout.
```

If both describe the same underlying issue, QA-125 may be marked as duplicate.

---

# 19. What is "Cannot Reproduce"?

A developer may mark a defect as **Cannot Reproduce** when the reported behavior does not occur in their environment.

### What should QA do?

Do not immediately reopen or argue.

Instead:

1. Verify the issue again.
2. Confirm environment.
3. Confirm application version/build.
4. Verify test data.
5. Check preconditions.
6. Attach screenshots/video.
7. Attach logs.
8. Provide timestamps.
9. Provide device/browser information.
10. Try reproducing again.

---

# 20. What do you do when a developer says "It's working as designed"?

First, review:

* Requirement
* Acceptance criteria
* Design document
* Business rules
* Previous behavior
* User story

If the requirement confirms the developer's behavior, QA should update the defect accordingly.

If the requirement confirms QA's expected behavior, discuss the issue with the developer and, if necessary, involve the BA/Product Owner.

### Strong Interview Answer

> "I would not make it a personal disagreement. I would refer to the documented requirement and acceptance criteria and work with the developer and product owner to establish the expected behavior."

---

# 21. What do you do when a developer rejects your defect?

I would:

1. Understand the reason for rejection.
2. Recheck the requirement.
3. Reproduce the issue.
4. Provide evidence.
5. Discuss with the developer.
6. Involve BA/Product Owner if the requirement is unclear.
7. Update the defect based on the final decision.

---

# 22. What is defect leakage?

Defect leakage occurs when a defect is missed during QA testing and is discovered later in another environment, typically production.

### Example

QA tests the payment flow successfully.

After production release, customers report that payment fails for certain cards.

This is a production defect that leaked through QA.

---

# 23. What is defect escape?

Defect escape is similar to defect leakage and generally refers to a defect that reaches a later testing stage or production without being detected in the earlier testing phase.

### Example

```text
Development
     ↓
QA
     ↓
UAT
     ↓
Production
```

If QA misses a defect and UAT discovers it, that is a QA escape.

If production discovers it, it is a production escape/leakage.

---

# 24. What is defect clustering?

Defect clustering means that a small number of modules contain a large percentage of defects.

### Example

Suppose an application has:

* Login
* Profile
* Search
* Payment
* Reports

Most defects are repeatedly found in the Payment module.

This indicates defect clustering.

### Interview Insight

When a module has many defects, QA should increase testing depth and consider regression testing around related functionality.

---

# 25. What is defect aging?

Defect aging refers to how long a defect remains unresolved.

### Example

```text
Defect created: August 1
Defect fixed: August 8

Defect age = 7 days
```

Long-aging defects may require management attention.

---

# 26. What is defect density?

Defect density measures the number of defects relative to the size of the software/module.

A common representation is:

```text
Defect Density =
Number of Defects / Size of Software
```

The size might be measured using:

* KLOC
* Function points
* Story points
* Modules

---

# 27. What is defect reopening?

A defect is reopened when the developer's fix does not actually resolve the issue.

### Example

Developer fixes:

```text
Login fails with valid credentials.
```

QA retests and finds:

```text
Login still fails with valid credentials.
```

QA reopens the defect.

---

# 28. What is a regression defect?

A regression defect occurs when a previously working feature breaks because of a new code change.

### Example

Developer fixes the appointment booking feature.

After the fix:

```text
Appointment booking works.
```

But now:

```text
Appointment cancellation fails.
```

The cancellation functionality has experienced a regression.

---

# 29. Scenario: Developer fixes a defect, but QA finds another issue. What do you do?

I first determine whether the new issue is:

* Part of the original defect
* A regression
* A completely new defect

If it is the same underlying issue, I update/reopen the existing defect.

If it is a separate issue, I create a new defect and link it to the original defect.

---

# 30. Scenario: A defect is intermittent. How do you report it?

I would not wait until I can reproduce it 100% of the time.

I would report:

```text
Reproducibility: Intermittent
Observed: 3 out of 10 attempts
```

I would include:

* Exact steps
* Timestamp
* Test data
* Environment
* Logs
* Screenshots/video
* Network information if applicable
* Device/browser information

This gives developers enough information to investigate.

---

# 31. Scenario: The defect occurs only in production. What would you do?

First, determine whether the production issue can be reproduced safely in a lower environment.

I would compare:

* Application version
* Configuration
* Database
* Feature flags
* Test data
* Environment variables
* API responses
* Third-party integrations

I would also collect production logs and monitoring information according to the team's process.

---

# 32. Scenario: A critical defect is found one hour before release. What do you do?

I would immediately communicate the defect to the appropriate stakeholders.

I would provide:

* Business impact
* Severity
* Reproduction steps
* Evidence
* Affected functionality
* Scope
* Workaround, if available

Then the release decision should be made collaboratively by the appropriate business/technical stakeholders.

### Important Interview Point

QA should **not independently decide** to release or cancel a production deployment unless that authority is explicitly part of the role.

---

# 33. Scenario: Developer says the defect is low priority, but you think it is high priority.

I would explain the business impact using evidence.

For example:

> "The issue prevents customers from completing payment, so although the technical change may be small, the business impact is high."

If there is still disagreement, I would involve the Product Owner/BA or appropriate triage team.

---

# 34. Scenario: You have 20 open defects and limited testing time. How do you prioritize?

I would prioritize based on:

1. Business-critical functionality
2. Severity
3. Priority
4. Customer impact
5. Production risk
6. Release-critical functionality
7. Areas affected by recent code changes

For example:

```text
Payment failure
   ↓
Login failure
   ↓
Appointment creation failure
   ↓
Search issue
   ↓
Minor UI alignment
```

The exact order depends on business impact and release priorities.

---

# 35. Scenario: You discover a defect, but the developer says it cannot be fixed in this release.

I would ask:

1. What is the impact?
2. Is there a workaround?
3. Is the defect release-blocking?
4. Does it affect customers?
5. Is there a business requirement?
6. Can Product Owner accept the risk?

If the defect is deferred, it should be properly documented and tracked for a future release.

---

# 36. Scenario: You find a defect in production. What information do you provide?

I would provide:

```text
Production Environment:
Application Version:
Device/Browser:
User Type:
Timestamp:
Steps:
Expected Result:
Actual Result:
Frequency:
Business Impact:
Logs:
Screenshots:
Video:
Request/Response:
Correlation ID:
```

Where applicable.

---

# 37. Scenario: The same defect works on Chrome but fails on Safari. What would you do?

I would identify this as a browser-specific defect.

I would verify:

* Browser versions
* Operating system
* Application version
* Browser console errors
* Network requests
* JavaScript errors
* Reproducibility

Then I would report the defect with the exact browser/environment combination.

---

# 38. Scenario: The application works on Android but fails on iOS. Is it one defect or two?

It depends on the underlying cause.

If the same underlying issue affects both platforms, one defect may be appropriate depending on project tracking standards.

If the implementations or causes are different, separate defects may be more appropriate.

The key is to avoid duplicate or unclear defect tracking.

---

# 39. Scenario: A developer asks you to close a defect without fixing it.

I would not close it simply because the developer requested it.

I would determine the reason:

* Requirement changed?
* Feature removed?
* Duplicate?
* Not reproducible?
* Business accepted risk?
* Fix deferred?

The defect should be closed only according to the team's agreed workflow and with appropriate documentation/approval.

---

# 40. Scenario: You cannot reproduce a developer-reported issue.

I would:

1. Review the original defect.
2. Confirm environment.
3. Confirm build/version.
4. Verify test data.
5. Follow the exact steps.
6. Check logs.
7. Try multiple times.
8. Ask the developer for additional information if needed.
9. Document my findings.

I would avoid simply saying:

> "Works for me."

Instead:

> "I could not reproduce the issue in QA environment using build X after 10 attempts. I have attached the test details and environment information."

---

# 41. Scenario: You discover 50 defects during regression. What do you do?

I would not simply report all 50 and stop.

I would analyze:

* Which modules are affected?
* Are they related?
* Are they caused by the same change?
* How many are critical?
* Are there common patterns?
* Is the build stable enough for continued testing?

I would communicate the overall risk to the team.

---

# 42. Scenario: A build has many critical defects. Would you continue testing?

It depends on the situation.

If the defects prevent meaningful testing, I would recommend stopping or returning the build to development.

If enough functionality remains testable, I would continue testing unaffected areas while clearly communicating the risk.

---

# 43. Scenario: A developer fixes 10 defects in one build. What testing do you perform?

I would perform:

### 1. Retesting

Verify each fixed defect.

### 2. Impact analysis

Identify functionality affected by the changes.

### 3. Regression testing

Test related functionality.

### 4. Smoke testing

Confirm that the build is stable enough for deeper testing.

---

# 44. What is the difference between Retesting and Regression Testing?

## Retesting

Testing the **specific defect again** after the fix.

```text
Defect → Fix → Retest
```

## Regression Testing

Testing existing functionality to ensure that the new change has not broken anything else.

```text
Code Change
    ↓
Changed Feature
    ↓
Related Features
    ↓
Existing Features
```

---

# 45. Scenario: A developer fixes a login defect. What regression tests would you perform?

I would test:

* Valid login
* Invalid username
* Invalid password
* Empty username
* Empty password
* Password masking
* Forgot password
* Account lockout
* Logout
* Session timeout
* Remember-me functionality, if available
* Role-based access
* Navigation after login

The exact scope depends on the application.

---

# 46. What is Defect Triage?

Defect triage is the process of reviewing and prioritizing defects.

Typical participants include:

* QA
* Developers
* Product Owner
* Business Analyst
* Engineering Manager
* Technical Lead

They may discuss:

* Severity
* Priority
* Business impact
* Release impact
* Fix complexity
* Dependencies
* Target release

---

# 47. What happens during a defect triage meeting?

A typical triage process:

```text
Review New Defects
       ↓
Validate Defect
       ↓
Determine Severity
       ↓
Determine Priority
       ↓
Assign Owner
       ↓
Decide Release
       ↓
Track Progress
```

---

# 48. What is a blocker versus a critical defect?

A **blocker** prevents testing or prevents a critical workflow from continuing.

A **critical defect** has severe impact on functionality/business behavior.

A critical defect may not necessarily block all testing.

---

# 49. How do you decide whether a defect should block a release?

I consider:

* Customer impact
* Business impact
* Severity
* Priority
* Affected users
* Frequency
* Workaround
* Security/data implications
* Release scope
* Regulatory/legal impact
* Product Owner/business decision

QA provides the risk assessment; the final release decision follows the organization's process.

---

# 50. How do you communicate a high-risk defect to management?

I keep the communication factual and concise.

Example:

```text
Issue:
Customers cannot complete payment using saved cards.

Impact:
Approximately 30% of checkout scenarios are affected.

Severity:
Critical

Reproducibility:
100%

Environment:
Production-like QA environment

Status:
Developer investigation in progress

Risk:
Release payment functionality may be impacted.
```

---

# 51. Senior-Level Scenario: Developer says, "I cannot reproduce the defect."

### Strong Answer

> "I would first verify the issue again and provide complete reproduction information, including build, environment, test data, timestamps, screenshots, logs, and video if available. I would also check whether the issue is environment-specific or intermittent. If we still cannot agree on the expected behavior or root cause, I would involve the Product Owner or BA rather than turning it into a personal disagreement."

---

# 52. Senior-Level Scenario: Product Owner says, "This is not important. Close the defect."

### Strong Answer

> "I would document the business decision and ensure the defect is closed according to the team's process. However, if I believe the issue creates significant technical, security, customer, or production risk, I would clearly communicate that risk before closure."

---

# 53. Senior-Level Scenario: A defect passes in QA but fails in production.

### Possible Causes

* Configuration difference
* Database difference
* Environment variables
* Feature flags
* Third-party service differences
* Production-only data
* Traffic/load
* Deployment differences
* Missing configuration
* API version mismatch

### QA Approach

```text
Compare QA vs Production
        ↓
Application Version
        ↓
Configuration
        ↓
Database/Data
        ↓
API/Services
        ↓
Logs/Monitoring
        ↓
Reproduce
        ↓
Identify Root Cause
```

---

# 54. Senior-Level Scenario: How do you reduce defect leakage?

I would focus on:

* Better requirement analysis
* Requirement traceability
* Risk-based testing
* Boundary-value testing
* Negative testing
* Integration testing
* Regression automation
* Production-like test data
* Environment validation
* Exploratory testing
* Better test coverage
* Root-cause analysis
* Defect trend analysis
* Strong developer-QA collaboration

---

# 55. Senior-Level Scenario: How do you perform root cause analysis for recurring defects?

I would analyze:

```text
Defect Pattern
      ↓
Affected Module
      ↓
Common Code Change
      ↓
Requirement Gap?
      ↓
Test Coverage Gap?
      ↓
Environment Issue?
      ↓
Development Process Issue?
      ↓
Corrective Action
```

For example, if the same type of API validation defect repeatedly reaches QA, I would investigate whether API contract testing or unit-test coverage is missing.

---

# 56. What metrics can be used for defect management?

Common metrics include:

* Defect density
* Defect leakage
* Defect escape rate
* Defect aging
* Defect reopen rate
* Defect closure rate
* Severity distribution
* Priority distribution
* Defects by module
* Defects by release
* Defects by environment
* Mean time to resolution

---

# 57. What is Defect Reopen Rate?

It measures how frequently defects are reopened after being marked as fixed.

A high reopen rate may indicate:

* Incomplete fixes
* Poor root-cause analysis
* Insufficient developer testing
* Requirement misunderstanding
* Regression issues

---

# 58. What is Mean Time to Resolution (MTTR)?

MTTR measures the average time required to resolve defects.

A simplified formula:

```text
MTTR =
Total Resolution Time / Number of Resolved Defects
```

Lower MTTR generally indicates faster defect resolution, but it should not be optimized at the expense of fix quality.

---

# 59. Real-Time Interview Scenario

### Interviewer:

> "You found a critical defect, but the developer says it is not reproducible. The Product Owner says the release must go out today. What will you do?"

### Strong Answer

> "I would first make sure I have strong evidence and verify the issue again. I would provide the developer with the exact environment, build, test data, timestamps, logs, screenshots or video, and reproduction frequency. I would communicate the customer and business impact to the Product Owner and explain the release risk. If the issue remains intermittent, I would document that clearly. I would not independently make the release decision unless that authority is part of my role. The appropriate stakeholders would make the final go/no-go decision based on the documented risk."

---

# 60. Real-Time Interview Scenario

### Interviewer:

> "You have 2 hours left before production deployment and discover 10 defects. What do you do?"

### Strong Answer

> "I would immediately classify the defects based on severity, priority, business impact, and affected functionality. I would identify any release blockers or critical issues and communicate them immediately. I would avoid spending equal time on all ten defects. I would focus first on customer-facing and business-critical flows, verify any available fixes, and provide the release stakeholders with a clear risk assessment."

---

# 61. Real-Time Interview Scenario

### Interviewer:

> "A developer fixes one defect but breaks three other features. What do you do?"

### Strong Answer

> "I would report the newly broken functionality as regression defects if they are separate issues. I would also identify the relationship between the original change and the regressions. I would communicate the impact and recommend that the affected areas be investigated before release. I would perform targeted regression around the changed functionality rather than only retesting the original defect."

---

# 62. Real-Time Interview Scenario

### Interviewer:

> "The same production defect happens every release. What would you do differently?"

### Strong Answer

> "I would treat it as a process and root-cause problem rather than repeatedly fixing the symptom. I would analyze when and why the defect escapes, identify the missing test coverage or process gap, add appropriate regression coverage, improve test data or environment validation, and consider automation where it provides value."

---

# 63. Real-Time Interview Scenario

### Interviewer:

> "You disagree with the developer about the severity of a defect. How do you handle it?"

### Strong Answer

> "I would explain my severity assessment using objective evidence such as customer impact, business impact, affected functionality, frequency, and data/security implications. If we still disagree, I would involve the appropriate triage owner or Product Owner. I would focus on the risk rather than making it a personal disagreement."

---

# 64. Real-Time Interview Scenario

### Interviewer:

> "How do you know when a defect is ready to be closed?"

### Strong Answer

> "I verify that the original issue is resolved, confirm the expected behavior against the requirement or acceptance criteria, perform appropriate regression testing, and make sure there are no remaining related issues. Only then would I close the defect according to the team's workflow."

---

# 65. Best Interview Answer Framework

For scenario-based defect questions, use this structure:

```text
1. Understand the issue
2. Reproduce the issue
3. Validate the requirement
4. Assess business impact
5. Determine severity
6. Determine priority
7. Provide evidence
8. Communicate with stakeholders
9. Track the defect
10. Retest the fix
11. Perform regression
12. Verify and close
```

---

# 66. Key Senior QA Interview Takeaways

Remember these points:

### Defect ≠ Argument

A defect should be discussed using:

```text
Requirement + Evidence + Business Impact
```

### Severity ≠ Priority

```text
Severity = Impact
Priority = Urgency
```

### Retesting ≠ Regression

```text
Retesting = Verify the fix

Regression = Verify nothing else broke
```

### QA does not work in isolation

A senior QA engineer collaborates with:

```text
QA
 ↓
Developer
 ↓
BA/Product Owner
 ↓
Technical Lead
 ↓
Release/Business Stakeholders
```

### Strong QA engineers focus on risk

The goal is not simply:

> "Find as many bugs as possible."

The goal is:

> **"Identify and communicate product risk early enough for the team to make informed decisions."**

---

# 67. Quick Interview Revision

| Question                | Short Answer                                  |
| ----------------------- | --------------------------------------------- |
| What is Severity?       | Impact of defect                              |
| What is Priority?       | Urgency of fixing defect                      |
| What is Retesting?      | Testing the fixed defect                      |
| What is Regression?     | Checking existing functionality after changes |
| What is Defect Leakage? | Defect missed by QA and found later           |
| What is Defect Escape?  | Defect reaches a later stage                  |
| What is Defect Triage?  | Reviewing/prioritizing defects                |
| What is Defect Aging?   | Time defect remains unresolved                |
| What is Duplicate?      | Already reported defect                       |
| What is Rejected?       | Not accepted as a valid defect                |
| What is Reopened?       | Defect still exists after fix                 |
| What is Blocker?        | Prevents testing/critical progress            |
| What is Critical?       | Severe business/system impact                 |
| What is MTTR?           | Average resolution time                       |
| What is Defect Density? | Defects relative to software size             |

---

# 68. Final Senior-Level Interview Question

### "What makes a good QA defect report?"

### Best Answer

> "A good defect report should be clear, reproducible, evidence-based, and useful to the development team. It should contain a concise summary, environment and build information, prerequisites, exact reproduction steps, expected and actual results, severity, priority, test data, and supporting evidence such as screenshots, video, logs, or API details. Most importantly, the defect should explain the business or customer impact so the team can make the right prioritization decision."

---

## Next Recommended Topic

`Manual Testing/Requirements-Analysis-and-Test-Case-Design-Interview-Questions.md`

This will cover **real-world requirement analysis, test scenario identification, test case design, positive/negative testing, boundary values, equivalence partitioning, traceability, and senior-level scenario questions.**
