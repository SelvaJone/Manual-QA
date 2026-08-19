# Test Traceability and Requirements Traceability Matrix – Scenario-Based Interview Questions

## 1. What is test traceability?

**Answer:**

Test traceability is the ability to establish a relationship between requirements, test scenarios, test cases, defects, and test results.

It helps QA teams prove that:

* Every requirement has corresponding test coverage.
* Every test case is linked to a requirement.
* Defects can be traced back to affected requirements and test cases.
* Test execution results can be reported against requirements.
* Changes in requirements can be assessed for testing impact.

### Real-Time Example

A requirement says:

> "Users should be able to reset their password using their registered email address."

QA should be able to trace:

```text
Requirement
   ↓
Test Scenario
   ↓
Test Cases
   ↓
Test Execution
   ↓
Defect (if any)
   ↓
Retest / Regression
   ↓
Final Result
```

---

# 2. What is an RTM?

**Answer:**

RTM stands for **Requirements Traceability Matrix**.

It is a document or tool-based mapping that establishes relationships between requirements and their corresponding test cases.

A typical RTM contains:

| Requirement ID | Requirement                  | Test Case ID | Test Scenario         | Test Result | Defect ID |
| -------------- | ---------------------------- | ------------ | --------------------- | ----------- | --------- |
| REQ-001        | Login with valid credentials | TC-001       | Verify valid login    | Pass        | -         |
| REQ-002        | Login with invalid password  | TC-002       | Verify invalid login  | Fail        | BUG-101   |
| REQ-003        | Forgot password              | TC-003       | Verify password reset | Pass        | -         |

---

# 3. Why is RTM important?

**Answer:**

RTM provides visibility into test coverage.

It helps answer:

* What requirements are covered?
* Which requirements are not tested?
* Which test cases validate each requirement?
* Which requirements have failed tests?
* Which requirements have open defects?
* What will be impacted if a requirement changes?

It is especially useful during release readiness and audit activities.

---

# 4. What are the different types of traceability?

**Answer:**

Common types are:

### Forward Traceability

Requirement → Test Case

It verifies that every requirement has test coverage.

### Backward Traceability

Test Case → Requirement

It verifies that every test case has a valid business requirement.

### Bi-Directional Traceability

Requirement ↔ Test Case

It provides both forward and backward traceability.

### Example

```text
REQ-101
   ↓
TC-101
   ↓
Execution Result
   ↓
BUG-201
```

---

# 5. What is forward traceability?

**Answer:**

Forward traceability verifies that all requirements are covered by test cases.

### Scenario

There are 100 requirements but only 90 have test cases.

The RTM identifies the remaining 10 requirements as having no test coverage.

This helps prevent requirements from being missed.

---

# 6. What is backward traceability?

**Answer:**

Backward traceability verifies that test cases are associated with valid requirements.

### Scenario

A QA engineer creates a test case for a feature that does not exist in the approved requirements.

Backward traceability can identify that the test case has no requirement mapping.

The QA engineer should confirm whether:

* The requirement is missing.
* The test case is unnecessary.
* The requirement exists in another document.
* The feature was introduced through an approved change.

---

# 7. What is bidirectional traceability?

**Answer:**

Bidirectional traceability connects requirements and tests in both directions.

For example:

```text
Requirement → Test Case
Test Case → Requirement
```

It provides stronger coverage and prevents both:

* Missing requirements
* Unnecessary/unmapped tests

---

# 8. How do you create an RTM?

**Answer:**

I normally follow these steps:

1. Collect approved requirements.
2. Assign or identify requirement IDs.
3. Identify test scenarios.
4. Create test cases.
5. Map test cases to requirements.
6. Execute the test cases.
7. Record execution status.
8. Link defects to failed test cases.
9. Review coverage.
10. Update the RTM when requirements or tests change.

---

# 9. What information do you include in an RTM?

**Answer:**

Depending on the project, I may include:

* Requirement ID
* Requirement description
* User story ID
* Acceptance criteria
* Test scenario ID
* Test case ID
* Test case description
* Test execution status
* Defect ID
* Defect status
* Requirement status
* Release/sprint information
* Comments

I avoid adding unnecessary columns that make the RTM difficult to maintain.

---

# 10. Is RTM always an Excel document?

**Answer:**

No.

RTM can be maintained in:

* Excel
* Jira
* Azure DevOps
* ALM
* Test management tools
* Confluence
* Specialized requirements management tools

The important thing is traceability, not the format.

---

# 11. Who is responsible for maintaining RTM?

**Answer:**

It depends on the organization's process.

Usually QA owns or manages test coverage, but requirements and traceability are often collaborative responsibilities involving:

* Business analysts
* Product owners
* Developers
* QA engineers
* Test leads
* Project managers

As a QA engineer, I make sure test coverage and execution information remain accurate.

---

# 12. What happens if a requirement changes after test cases are created?

**Answer:**

I first perform an impact analysis.

I identify:

* Existing test cases linked to the requirement
* Test scenarios affected
* Test data affected
* Automation affected
* Existing defects affected
* Regression areas affected

Then I update the affected test cases and RTM.

Finally, I execute the required regression tests.

---

# 13. Scenario: A requirement changed one day before release. What would you do?

**Answer:**

I would not simply modify the test case and continue testing.

I would:

1. Understand the exact requirement change.
2. Confirm the change is approved.
3. Perform impact analysis.
4. Identify affected test cases.
5. Identify affected regression areas.
6. Update test cases.
7. Update RTM.
8. Prepare or update test data.
9. Execute impacted tests.
10. Execute appropriate regression tests.
11. Report the risk to stakeholders.
12. Communicate whether the release is still safe.

---

# 14. Scenario: You find a requirement with no test case. What would you do?

**Answer:**

I would first verify whether the requirement is actually testable and approved.

If it is valid, I would:

* Create the appropriate test scenario.
* Create test cases.
* Add the mapping to the RTM.
* Execute the tests.
* Report any resulting defects.

I would also check whether the requirement was recently added and missed during test design.

---

# 15. Scenario: A test case has no requirement mapping. What would you do?

**Answer:**

I would investigate why the test case exists.

Possible reasons include:

* Requirement was missed.
* Requirement ID was entered incorrectly.
* Test case was created for regression.
* Test case validates a non-functional/business rule.
* Test case is obsolete.

I would not automatically delete it.

I would confirm its purpose and then either map, update, or retire the test case.

---

# 16. Scenario: One requirement maps to 20 test cases. Is that a problem?

**Answer:**

Not necessarily.

A single requirement can require multiple test cases for:

* Positive scenarios
* Negative scenarios
* Boundary conditions
* Validation
* Error handling
* Security
* Compatibility
* Different user roles

The number of test cases depends on the complexity and risk of the requirement.

---

# 17. Scenario: One test case maps to multiple requirements. Is that acceptable?

**Answer:**

It can be acceptable when the test case genuinely validates multiple related requirements.

However, I would avoid excessive many-to-many mapping because it can make traceability difficult.

If requirements are independent, separate test cases may provide clearer coverage.

---

# 18. How do you identify gaps using RTM?

**Answer:**

I look for:

* Requirements with no test cases.
* Test cases with no requirements.
* Requirements with only one weak test case.
* Requirements with failed tests.
* Requirements with open critical defects.
* Requirements not executed.
* Requirements added after test planning.

For example:

```text
Total Requirements = 100
Requirements Covered = 95

Coverage = 95 / 100 × 100
         = 95%
```

The remaining 5% requires investigation.

---

# 19. What is requirements coverage?

**Answer:**

Requirements coverage measures how many requirements have corresponding test coverage.

A common calculation is:

```text
Requirements Coverage %
=
(Number of requirements covered by tests
 / Total number of testable requirements)
× 100
```

Example:

```text
Total Requirements = 200
Covered Requirements = 190

Coverage = 190 / 200 × 100
         = 95%
```

---

# 20. Is 100% RTM coverage enough to declare the application high quality?

**Answer:**

No.

100% requirements coverage only indicates that requirements have corresponding tests.

It does not guarantee:

* Good test quality
* No defects
* Good usability
* Good performance
* Good security
* Good test data
* Production stability

I would evaluate RTM together with defect metrics, risk, test results, regression results, and other quality indicators.

---

# 21. Scenario: RTM shows 100% coverage, but production has serious defects. How is that possible?

**Answer:**

RTM measures traceability, not necessarily test effectiveness.

Possible causes include:

* Poorly designed test cases.
* Missing negative scenarios.
* Incomplete requirements.
* Incorrect acceptance criteria.
* Inadequate test data.
* Environment differences.
* Integration issues.
* Production-only configuration.
* Insufficient exploratory testing.
* Tests marked as Pass without meaningful validation.

Therefore, I would review the test design and requirements rather than assuming RTM was sufficient.

---

# 22. How do you handle requirements that are not testable?

**Answer:**

I raise the issue during requirement review.

For example:

> "The application should be user friendly."

This is vague.

I would ask the product/business team to define measurable acceptance criteria.

For example:

> "A new user should be able to complete registration within three minutes without assistance."

The requirement then becomes more testable.

---

# 23. Scenario: The business analyst says a requirement does not need testing. What do you do?

**Answer:**

I would understand the reason first.

If the requirement is truly non-testable or informational, I would document the rationale.

If it affects application behavior, I would explain the risk of having no validation.

I would work with the BA, PO, and QA lead to determine the appropriate coverage rather than creating unnecessary conflict.

---

# 24. Scenario: The developer implemented functionality that is not mentioned in the requirement. What would you do?

**Answer:**

I would not assume it is correct or incorrect.

I would:

1. Identify the functionality.
2. Ask the developer for the source of the requirement.
3. Check design documentation or acceptance criteria.
4. Discuss with the BA/PO.
5. Determine whether it is an approved enhancement.
6. Update requirements if appropriate.
7. Add test coverage.
8. Update RTM.

---

# 25. Scenario: A requirement is removed after test execution. What happens to its test cases?

**Answer:**

I would not simply delete the test cases.

I would:

* Confirm the requirement removal is approved.
* Mark the requirement as removed/deprecated.
* Identify linked test cases.
* Determine whether those tests are still useful.
* Retire obsolete tests.
* Preserve historical execution information where required.
* Update RTM.

Historical traceability should not be destroyed unnecessarily.

---

# 26. Scenario: A defect is found, but there is no requirement associated with it. What would you do?

**Answer:**

I would investigate whether:

* The requirement is missing.
* The requirement ID is incorrect.
* The defect belongs to an existing requirement.
* The behavior is a technical or usability issue.
* The feature is an approved enhancement.

I would then establish the correct traceability before closing the issue.

---

# 27. How do defects relate to RTM?

**Answer:**

Defects can be linked through the test case and requirement relationship.

Example:

```text
REQ-100
   ↓
TC-100
   ↓
BUG-500
```

This allows the team to determine which business requirement is affected by a defect.

---

# 28. Scenario: A critical defect is linked to a low-priority requirement. What would you do?

**Answer:**

I would not automatically assume the defect is low priority.

Requirement priority and defect severity/priority are different concepts.

I would evaluate:

* Business impact
* User impact
* Frequency
* Data impact
* Security impact
* Workaround availability
* Release impact

Then I would discuss the appropriate defect priority with stakeholders.

---

# 29. How does RTM help during regression testing?

**Answer:**

When a requirement changes, RTM helps identify the tests associated with that requirement.

For example:

```text
REQ-200 changed
       ↓
TC-201
TC-202
TC-203
       ↓
Regression Testing
```

I can then identify both direct and related regression areas.

---

# 30. Scenario: A developer fixes a defect. How do you use traceability during retesting?

**Answer:**

I trace:

```text
Requirement
   ↓
Failed Test Case
   ↓
Defect
   ↓
Developer Fix
   ↓
Retest
   ↓
Regression
```

I first execute the failed test case.

If it passes, I then execute appropriate related regression tests.

I update the defect and test execution results accordingly.

---

# 31. How do you maintain traceability in Agile?

**Answer:**

In Agile, traceability should be lightweight and continuously maintained.

A common relationship is:

```text
Epic
 ↓
Feature
 ↓
User Story
 ↓
Acceptance Criteria
 ↓
Test Scenario
 ↓
Test Case
 ↓
Defect
```

I update traceability as stories evolve instead of waiting until the end of the release.

---

# 32. Scenario: Acceptance criteria changed during the sprint. What would you do?

**Answer:**

I would:

1. Confirm the updated acceptance criteria.
2. Review existing test cases.
3. Identify impacted tests.
4. Update or create tests.
5. Update traceability.
6. Re-execute impacted tests.
7. Perform regression where necessary.
8. Communicate any timeline or risk impact.

---

# 33. How do you handle RTM in a fast-moving Agile project?

**Answer:**

I avoid maintaining unnecessary manual documents.

Instead, I use the team's test management or ALM tools to maintain links between:

* User stories
* Acceptance criteria
* Test cases
* Test executions
* Defects

I focus on maintaining useful traceability rather than creating documentation for its own sake.

---

# 34. What is the difference between RTM and test coverage?

**Answer:**

**RTM** is the mechanism/document used to establish traceability.

**Test coverage** measures how much of the requirement scope is covered by tests.

Example:

```text
RTM:
REQ-001 → TC-001
REQ-002 → TC-002

Coverage:
2 of 2 requirements covered = 100%
```

---

# 35. Scenario: Your manager asks for proof that all requirements were tested. What would you provide?

**Answer:**

I would provide:

* RTM or equivalent traceability report.
* Requirement-to-test mapping.
* Test execution report.
* Failed test details.
* Open/closed defect report.
* Regression results.
* Requirement coverage summary.

I would also explain any excluded or untested requirements and their business justification.

---

# 36. How do you verify RTM accuracy?

**Answer:**

I periodically review:

* Requirement IDs.
* Test case IDs.
* Mapping correctness.
* Missing mappings.
* Obsolete requirements.
* Obsolete test cases.
* Execution status.
* Defect links.
* Changed acceptance criteria.

I also compare the RTM against the latest approved requirements.

---

# 37. Scenario: Two test cases are mapped to the wrong requirement. How would you fix it?

**Answer:**

I would:

1. Identify the correct requirement.
2. Review the test case objective.
3. Correct the mapping.
4. Check whether other test cases have the same issue.
5. Recalculate coverage if necessary.
6. Communicate the correction if the report has already been shared.

I would also look for the process issue that caused the incorrect mapping.

---

# 38. How do you handle duplicate requirements?

**Answer:**

I would raise the duplication during requirement review.

I would determine whether:

* They represent the same business rule.
* One is an updated version.
* They apply to different workflows.
* They have different acceptance criteria.

If they are genuinely duplicates, the BA/PO should consolidate or clarify them.

Then the traceability mappings should be updated.

---

# 39. Scenario: A requirement has 100% test coverage but no test case has been executed. Is it covered?

**Answer:**

It has **test design coverage**, but it does not have **execution coverage**.

For example:

```text
Requirement Coverage = 100%
Execution Coverage = 0%
```

I would clearly distinguish these metrics in reporting.

---

# 40. What is the difference between test design coverage and test execution coverage?

**Answer:**

### Test Design Coverage

Measures whether requirements have corresponding tests.

### Test Execution Coverage

Measures how many planned tests have actually been executed.

Example:

```text
100 requirements
95 covered by test cases

Design Coverage = 95%

100 test cases
80 executed

Execution Coverage = 80%
```

Both metrics provide different information.

---

# 41. Scenario: A test case is blocked because the environment is unavailable. How should RTM reflect it?

**Answer:**

The requirement remains covered by the test case, but the execution status should show **Blocked** or the appropriate project status.

I would not mark it as Pass.

I would document:

* Environment issue
* Blocked test case
* Dependency
* Impact
* Planned execution date

---

# 42. Scenario: A requirement is tested manually, but the automation team has not automated it. Is traceability affected?

**Answer:**

No.

Manual and automated tests can both provide traceability.

The RTM can show:

```text
REQ-101
 ↓
Manual TC-101
 ↓
Automated Test AT-101
```

Automation status can be tracked separately.

---

# 43. How can RTM help during audits?

**Answer:**

RTM provides evidence that requirements were systematically validated.

Auditors can trace:

```text
Requirement
 → Test Case
 → Execution Result
 → Defect
 → Retest
```

This is especially useful in regulated or compliance-driven projects.

---

# 44. Scenario: An auditor asks why one requirement has no test case. What would you do?

**Answer:**

I would provide the documented rationale.

Possible reasons:

* Requirement is informational.
* Requirement is not testable.
* Requirement was removed.
* Requirement is covered by another approved test.
* Testing is performed through another validation mechanism.

I would never create a fake test case simply to show 100% coverage.

---

# 45. How do you use RTM for release readiness?

**Answer:**

Before release, I review:

* Requirement coverage.
* Test execution status.
* Failed tests.
* Blocked tests.
* Critical defects.
* High-priority open defects.
* Regression results.
* Requirement changes.

Example:

```text
Requirements                100
Requirements covered       100
Test execution              98
Blocked tests                 2
Critical defects              0
High defects                  1
Regression                   Pass
```

I would then provide a risk-based release recommendation.

---

# 46. Scenario: Product owner says, "RTM is 100%, so we can release." Do you agree?

**Answer:**

Not automatically.

I would explain that RTM coverage is only one release-readiness indicator.

I would also evaluate:

* Test execution.
* Defect severity.
* Regression results.
* Performance.
* Security.
* Environment stability.
* Business acceptance.
* Known risks.

A release decision should be based on overall quality and risk.

---

# 47. What are common RTM mistakes?

**Answer:**

Common mistakes include:

* Missing requirements.
* Incorrect requirement IDs.
* Incorrect test mappings.
* Duplicate test cases.
* Outdated mappings.
* Test cases without requirements.
* Requirements without tests.
* Not updating RTM after changes.
* Treating 100% coverage as 100% quality.
* Maintaining RTM manually without ownership.
* Ignoring execution status.
* Not linking defects.

---

# 48. How would you improve a poorly maintained RTM?

**Answer:**

I would first understand the current process.

Then I would:

1. Identify the source of truth for requirements.
2. Remove obsolete requirements.
3. Correct mappings.
4. Identify missing coverage.
5. Link defects.
6. Add execution status.
7. Define ownership.
8. Establish an update process.
9. Automate reporting where possible.
10. Review the RTM regularly.

---

# 49. Scenario: You inherit a project with no RTM. What would you do?

**Answer:**

I would not immediately create a huge spreadsheet.

First, I would identify:

* Approved requirements.
* Existing test cases.
* Existing test executions.
* Existing defects.
* Current release scope.

Then I would establish the most important traceability links.

For a large project, I would prioritize critical and high-risk requirements first.

---

# 50. How would you explain RTM to a non-technical stakeholder?

**Answer:**

I would explain:

> "RTM is like a checklist that connects every business requirement to the tests we performed. It helps us demonstrate that the functionality requested by the business was actually validated."

This makes the purpose easier to understand than explaining the technical structure first.

---

# 51. Scenario: The requirement says the system must support three user roles. What traceability would you create?

**Answer:**

I would create separate test coverage for each role if their permissions or behavior differ.

```text
REQ-101
 ├── TC-101 → Admin
 ├── TC-102 → Manager
 └── TC-103 → Standard User
```

I would also include positive and negative authorization scenarios.

---

# 52. Scenario: A new browser is added to the supported-browser list. What traceability impact would you assess?

**Answer:**

I would identify:

* Browser compatibility requirements.
* Existing browser test cases.
* UI-specific test cases.
* Automation coverage.
* Known browser-specific defects.
* Regression scope.

Then I would add/update test cases and traceability accordingly.

---

# 53. Scenario: A new region is added to an application. How would you use traceability?

**Answer:**

I would identify requirements affected by the new region:

* Registration.
* Login.
* Language.
* Localization.
* Dealer information.
* Address formats.
* Date/time formats.
* Currency.
* Region-specific business rules.
* Notifications.
* Legal/privacy requirements.

Then I would map the new regional test cases to those requirements.

---

# 54. Scenario: A requirement is satisfied through API testing rather than UI testing. Does it need traceability?

**Answer:**

Yes.

Traceability is independent of the test layer.

For example:

```text
REQ-301
 ↓
API Test
 ↓
Execution Result
 ↓
BUG-701
```

The requirement can be validated through API, UI, integration, database, or other appropriate testing methods.

---

# 55. How do you handle non-functional requirements in RTM?

**Answer:**

I include them if they are part of the approved test scope.

Examples:

* Performance.
* Security.
* Availability.
* Scalability.
* Compatibility.
* Reliability.

For example:

```text
NFR-001
 ↓
Performance Test PT-001
 ↓
Execution Result
```

---

# 56. Scenario: Performance requirement says response time must be under two seconds. How would you trace it?

**Answer:**

I would create a measurable performance test.

```text
NFR-001
Response time < 2 seconds
       ↓
PT-001
       ↓
Performance Execution
       ↓
Result: 1.6 sec
       ↓
Pass
```

If the result is 3.5 seconds, I would raise a defect or performance issue based on project process.

---

# 57. Scenario: A security requirement has no functional test case. Is that necessarily a gap?

**Answer:**

Not necessarily.

Security requirements may be validated through:

* Security testing.
* Penetration testing.
* Vulnerability scanning.
* API security testing.
* Code analysis.
* Specialized security tools.

The requirement should still have appropriate validation evidence.

---

# 58. How do you handle requirements that are intentionally out of scope?

**Answer:**

I document them as out of scope rather than leaving them ambiguous.

The RTM or requirements tracking system should clearly indicate:

```text
Requirement Status = Out of Scope
Reason = Not included in Release 5.0
Approved By = Product Owner
```

This prevents stakeholders from assuming that the requirement was accidentally missed.

---

# 59. Scenario: A requirement was missed and discovered during system testing. What would you do?

**Answer:**

I would:

1. Notify the appropriate stakeholders.
2. Determine the business impact.
3. Confirm the requirement.
4. Identify why it was missed.
5. Create test scenarios and test cases.
6. Update RTM.
7. Execute the tests.
8. Add regression coverage.
9. Perform root-cause analysis.
10. Improve the requirement-review/test-design process.

---

# 60. What is the most important principle when maintaining traceability?

**Answer:**

The most important principle is:

> **Every approved testable requirement should have appropriate validation, and every test should have a clear reason for existing.**

Traceability should provide meaningful visibility into coverage and risk rather than becoming a documentation exercise.

---

# Senior-Level Rapid-Fire Questions

## 61. Can RTM identify missed requirements?

**Answer:** Yes. Requirements without mapped test cases are immediately visible.

## 62. Can RTM identify redundant test cases?

**Answer:** It can help identify suspicious duplication, but test-case review is still required.

## 63. Can RTM prove that there are no defects?

**Answer:** No. It proves traceability, not defect absence.

## 64. Should exploratory testing always appear as individual RTM test cases?

**Answer:** Not necessarily. Exploratory testing can be tracked through sessions, charters, findings, and related requirements.

## 65. Should regression tests be linked to requirements?

**Answer:** Yes, where practical. This improves visibility into regression coverage.

## 66. Should negative tests be included in RTM?

**Answer:** Yes, when they validate requirement behavior or business rules.

## 67. What happens to RTM when a requirement is deleted?

**Answer:** Preserve historical traceability where required and mark the requirement/test relationship appropriately rather than blindly deleting history.

## 68. Is RTM mandatory in every Agile project?

**Answer:** No. The level and mechanism of traceability should match project risk, compliance, and organizational needs.

## 69. Can Jira provide traceability?

**Answer:** Yes, when configured appropriately using links between stories, requirements, test artifacts, executions, and defects.

## 70. What would you say in an interview if asked whether RTM is a QA responsibility?

**Answer:**

> "QA usually owns test coverage and ensures that the test artifacts are properly traced to requirements, but traceability itself is a cross-functional responsibility. Business, product, development, and QA teams all contribute to keeping the information accurate."

---

# Real-Time Interview Scenario: Complete Example

## Scenario

A banking application has a requirement:

> "A customer should be able to transfer up to $5,000 per day."

### How would you create traceability?

```text
REQ-501
Daily transfer limit = $5,000
        ↓
        ├── TC-501
        │   Transfer exactly $5,000
        │
        ├── TC-502
        │   Transfer $5,000.01
        │
        ├── TC-503
        │   Multiple transfers totaling $5,000
        │
        ├── TC-504
        │   Multiple transfers exceeding $5,000
        │
        └── TC-505
            Verify daily limit reset
```

If TC-502 fails:

```text
REQ-501
   ↓
TC-502
   ↓
BUG-801
   ↓
Developer Fix
   ↓
Retest
   ↓
Regression
```

This provides complete traceability from the business requirement through final validation.

---

# Final Interview Tip

When answering RTM questions in a senior QA interview, avoid saying only:

> "RTM maps requirements to test cases."

A stronger answer is:

> "RTM provides end-to-end traceability between requirements and validation artifacts. I use it to identify coverage gaps, assess the impact of requirement changes, connect failed tests to defects, support regression planning, and provide release-readiness evidence. In Agile projects, I prefer lightweight tool-based traceability that stays synchronized with stories, acceptance criteria, tests, executions, and defects."

That demonstrates **practical QA experience**, not just a definition.
