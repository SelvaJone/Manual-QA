# Test Review and Inspection – Scenario-Based Interview Questions

## 1. What is Test Review?

A **test review** is a systematic examination of test artifacts such as requirements, test scenarios, test cases, test data, automation scripts, defect reports, and test plans to identify issues before or during test execution.

The primary goal is to detect problems early and improve the quality, completeness, and effectiveness of testing.

### Commonly reviewed artifacts

* Requirements
* User stories
* Acceptance criteria
* Test scenarios
* Test cases
* Test data
* Test plans
* Test strategy
* RTM
* Automation scripts
* Defect reports
* Test execution results
* Test summary reports

---

# 2. What is Inspection?

**Inspection** is a formal and structured review technique used to identify defects in a work product.

Inspection normally involves defined roles, preparation, review criteria, defect logging, and follow-up.

Unlike an informal review, an inspection is more disciplined and follows a predefined process.

### Typical inspection activities

1. Planning
2. Preparation
3. Individual examination
4. Inspection meeting
5. Defect recording
6. Rework
7. Follow-up
8. Closure

---

# 3. What is the Difference Between Review and Inspection?

| Review                                 | Inspection                                          |
| -------------------------------------- | --------------------------------------------------- |
| General term for examining an artifact | Formal review technique                             |
| Can be informal or formal              | Usually highly structured                           |
| May not require defined roles          | Defined roles are commonly used                     |
| Less documentation may be required     | Defects and results are formally recorded           |
| Can be performed quickly               | Requires preparation and defined process            |
| Example: peer review of test cases     | Example: formal inspection of critical requirements |

---

# 4. What is Peer Review?

Peer review is when another team member examines your work product to identify mistakes, omissions, inconsistencies, or improvements.

### Example

A QA engineer creates 50 test cases for a payment feature.

Another QA engineer reviews the test cases and identifies:

* Missing negative scenarios
* Missing boundary cases
* Incorrect expected results
* Missing validation for failed payments
* Missing security-related scenarios

The original QA engineer updates the test cases based on the review.

---

# 5. Why Should Test Cases Be Reviewed Before Execution?

Test case review helps identify defects before execution.

It can detect:

* Missing requirements
* Incorrect assumptions
* Duplicate test cases
* Incorrect expected results
* Missing negative scenarios
* Missing boundary conditions
* Incomplete test data
* Incorrect preconditions
* Missing validations

Finding these issues early reduces rework during execution.

---

# 6. Scenario: You Are Asked to Review Another QA Engineer's Test Cases. What Will You Check?

I would review the test cases systematically.

I would check:

1. Requirement coverage
2. Acceptance criteria coverage
3. Positive scenarios
4. Negative scenarios
5. Boundary conditions
6. Error handling
7. Preconditions
8. Test data
9. Expected results
10. Database/API validations where applicable
11. UI validations
12. Integration scenarios
13. Duplicate test cases
14. Traceability
15. Maintainability and readability

I would also verify whether the expected results are specific and measurable rather than vague.

---

# 7. Scenario: You Find That Several Test Cases Are Missing Negative Scenarios. What Will You Do?

I would first identify the requirement and determine which negative conditions are applicable.

For example, for a login feature I would add scenarios such as:

* Invalid username
* Invalid password
* Blank username
* Blank password
* Both fields blank
* Locked account
* Expired password
* Unsupported characters
* Multiple failed attempts
* Session timeout

I would communicate the gaps to the test case author and update the cases after agreement.

---

# 8. Scenario: The Developer Says Your Test Case Is Wrong During Review. How Will You Handle It?

I would not treat it as a personal disagreement.

I would:

1. Refer to the requirement or acceptance criteria.
2. Explain the reasoning behind the test case.
3. Ask the developer to explain the implementation behavior.
4. Check whether the requirement is ambiguous.
5. Involve the Product Owner/BA if clarification is required.
6. Update the test case based on the confirmed business behavior.

The objective is to establish the correct behavior, not to prove who is right.

---

# 9. Scenario: You Discover an Ambiguous Requirement During Test Case Review. What Will You Do?

I would not create assumptions and proceed silently.

I would raise the ambiguity with the appropriate stakeholder such as:

* Business Analyst
* Product Owner
* Product Manager
* Developer

I would document the clarification and then update:

* Requirement
* Acceptance criteria
* Test scenarios
* Test cases
* RTM if applicable

This prevents different team members from interpreting the requirement differently.

---

# 10. Scenario: A Critical Requirement Has No Test Case. What Will You Do?

I would identify the missing coverage and create the required test scenarios.

I would also check the RTM to determine whether the requirement is genuinely missing from testing or whether traceability is incomplete.

For a critical requirement, I would communicate the gap to the QA lead and ensure coverage is added before release.

---

# 11. What is a Test Case Review Checklist?

A test case review checklist is a predefined set of criteria used to verify the quality and completeness of test cases.

### Example checklist

* [ ] Requirement is referenced
* [ ] Test case has a clear objective
* [ ] Preconditions are defined
* [ ] Test data is defined
* [ ] Steps are clear
* [ ] Expected results are specific
* [ ] Positive scenario is covered
* [ ] Negative scenario is covered
* [ ] Boundary conditions are covered
* [ ] Error messages are validated
* [ ] Database/API validation is included where required
* [ ] No unnecessary duplicate cases exist
* [ ] Test case is reusable and maintainable

---

# 12. Scenario: You Have 500 Test Cases to Review in One Day. How Will You Approach It?

I would prioritize instead of reviewing everything with the same level of detail.

I would prioritize:

1. Critical business functionality
2. High-risk features
3. Recently changed functionality
4. Customer-facing workflows
5. Regulatory/security-sensitive functionality
6. Integration-heavy areas
7. Complex test cases
8. Remaining lower-risk cases

I would also use a review checklist and divide the work among team members where possible.

---

# 13. Scenario: You Find 20 Duplicate Test Cases During Review. What Will You Do?

I would verify that they are genuinely duplicates before removing anything.

I would:

1. Compare their objectives.
2. Compare their test data.
3. Compare their expected results.
4. Determine whether the duplication is intentional.
5. Consolidate duplicate cases where appropriate.
6. Preserve unique coverage.
7. Update traceability.

The goal is to reduce unnecessary maintenance without accidentally removing coverage.

---

# 14. What is Formal Inspection?

Formal inspection is a structured review process where participants examine a work product against defined standards and record defects.

### Typical roles

* Moderator
* Author
* Reviewer/Inspector
* Recorder

The exact roles may vary depending on the organization's process.

---

# 15. What Does a Moderator Do During an Inspection?

The moderator facilitates the inspection process.

Responsibilities may include:

* Scheduling the inspection
* Distributing materials
* Ensuring participants prepare
* Explaining the review objective
* Controlling the meeting
* Ensuring defects are recorded
* Preventing unnecessary discussions
* Tracking follow-up activities
* Ensuring closure

---

# 16. What Does the Author Do During an Inspection?

The author is responsible for the work product being reviewed.

For example, if a QA engineer created the test cases, that QA engineer is the author.

The author:

* Provides the artifact
* Explains the artifact when necessary
* Receives review feedback
* Performs corrections
* Provides the updated artifact for follow-up

---

# 17. What Does the Recorder Do During an Inspection?

The recorder documents issues identified during the inspection.

The recorder may capture:

* Defect description
* Location
* Severity
* Category
* Owner
* Status
* Action required

The exact information depends on the organization's review process.

---

# 18. Scenario: A Review Meeting Is Turning Into a Technical Debate. What Will You Do?

I would keep the meeting focused on identifying defects rather than solving every defect immediately.

For example:

> "Let's record this as an issue and discuss the detailed solution separately with the relevant stakeholders."

This keeps the review efficient.

The review should identify problems; detailed problem-solving can happen afterward when necessary.

---

# 19. Scenario: A Developer Says, "The Test Case Is Not Required Because the Code Already Handles It." How Do You Respond?

I would explain that implementation behavior alone does not determine test coverage.

I would verify:

* Requirement
* Acceptance criteria
* Business risk
* Existing coverage
* Actual application behavior

If the requirement needs validation, the test case should remain unless equivalent coverage already exists elsewhere.

---

# 20. Scenario: A QA Engineer Creates Only Positive Test Cases. How Would You Review Them?

I would identify the missing negative and abnormal scenarios.

For example, for a registration form:

### Positive

* Valid user information
* Valid email
* Valid password

### Negative

* Invalid email
* Blank required fields
* Existing email
* Weak password
* Password mismatch
* Invalid characters
* Maximum-length values
* Minimum-length values

I would recommend adding appropriate negative and boundary scenarios.

---

# 21. Scenario: You Find Incorrect Expected Results in Test Cases. What Will You Do?

I would first compare the expected result with the approved requirement.

If the requirement confirms the expected behavior, I would update the test case.

If the requirement itself is incorrect or ambiguous, I would raise it for clarification instead of making assumptions.

---

# 22. Scenario: The Requirement Changes After Test Case Review. What Will You Do?

I would perform impact analysis.

I would identify affected:

* Test scenarios
* Test cases
* Test data
* Automation scripts
* RTM
* Regression suite
* Defects
* Test execution results

Then I would update the affected artifacts and ensure obsolete cases are removed or modified.

---

# 23. Scenario: How Do You Review Test Cases for Boundary Value Analysis?

I would verify that test cases cover values around the valid boundary.

For example, if age must be between 18 and 60:

| Value | Expected |
| ----: | -------- |
|    17 | Invalid  |
|    18 | Valid    |
|    19 | Valid    |
|    59 | Valid    |
|    60 | Valid    |
|    61 | Invalid  |

This helps identify boundary-related defects.

---

# 24. Scenario: How Do You Review Test Cases for Equivalence Partitioning?

I would check whether input data has been divided into meaningful groups where the system is expected to behave similarly.

For example, if an amount must be between $100 and $1,000:

* Below $100 → Invalid
* $100–$1,000 → Valid
* Above $1,000 → Invalid

Instead of testing every possible amount, representative values from each partition can be selected.

---

# 25. Scenario: A Test Case Contains 30 Steps. What Would You Check?

I would determine whether the test case is too large or whether the steps represent one meaningful business scenario.

I would check:

* Can it be divided?
* Are there unnecessary steps?
* Are unrelated validations included?
* Are preconditions being repeated?
* Can common setup steps be moved to reusable preconditions?

Long test cases are not automatically wrong, but they should remain understandable and maintainable.

---

# 26. Scenario: A Test Case Has the Expected Result "System Should Work Properly." Is That Acceptable?

No.

The expected result should be specific and measurable.

Instead of:

> System should work properly.

Use:

> The payment should be processed successfully and the transaction confirmation number should be displayed to the customer.

Specific expected results make execution and defect reporting much clearer.

---

# 27. Scenario: How Would You Review Test Data?

I would verify:

* Valid data
* Invalid data
* Boundary data
* Null/blank data
* Duplicate data
* Special characters
* Large data
* Expired data
* Role-specific data
* Region-specific data
* Language-specific data
* Environment-specific data

For integration testing, I would also verify that the required upstream and downstream data is available.

---

# 28. Scenario: How Would You Review an API Test Case?

I would check:

### Request

* HTTP method
* Endpoint
* Headers
* Authentication
* Query parameters
* Path parameters
* Request body

### Response

* Status code
* Response headers
* Response body
* Schema
* Mandatory fields
* Data types
* Business rules

### Negative scenarios

* Invalid authentication
* Missing parameters
* Invalid payload
* Invalid data types
* Unauthorized access
* Resource not found
* Duplicate request
* Unsupported method

---

# 29. Scenario: How Would You Review a UI Test Case?

I would verify:

* Page navigation
* UI elements
* Field validations
* Required fields
* Input restrictions
* Error messages
* Button behavior
* Positive flow
* Negative flow
* Boundary conditions
* Browser compatibility
* Responsive behavior
* Accessibility where applicable

---

# 30. Scenario: How Would You Review a Mobile Application Test Case?

I would additionally consider:

* Different screen sizes
* Orientation
* Network changes
* App background/foreground
* Application interruption
* Permissions
* Notifications
* Device compatibility
* OS versions
* Offline behavior
* Battery/resource considerations
* Deep links
* App installation/update behavior

---

# 31. Scenario: A Test Case Passes Review but Fails During Execution. Does That Mean the Review Failed?

Not necessarily.

A review evaluates the quality and completeness of the test artifact.

Execution can uncover:

* Application defects
* Environment problems
* Test data problems
* Requirement changes
* Infrastructure issues
* Unexpected system behavior

However, if the test case failed because the review missed an obvious issue, then the review process should be improved.

---

# 32. Scenario: You Find a Defect in a Requirement During Review. Should You Create a Bug?

It depends on the team's defect management process.

If requirements are treated as formal work products, the issue may be recorded as a requirement defect.

For example:

> Requirement says the field accepts 10 characters, while acceptance criteria says it accepts 20.

This should be raised and resolved before test execution.

---

# 33. Scenario: How Does Test Review Help Defect Prevention?

Test review identifies defects before execution.

For example:

Requirement:

> Customer cannot transfer more than $10,000 per day.

During test case review, the QA engineer notices that no test case validates the daily limit.

Adding that test before execution helps prevent a coverage gap.

This is an example of **defect prevention through early review**.

---

# 34. Scenario: What Metrics Can Be Used for Test Reviews?

Possible metrics include:

* Number of artifacts reviewed
* Number of defects found during review
* Defects per test case
* Review defect density
* Review effort
* Rework effort
* Review completion percentage
* Requirements covered
* Test cases reviewed
* Percentage of test cases requiring rework
* Review effectiveness

Metrics should be used to improve the process rather than simply measure individual performance.

---

# 35. What is Review Defect Density?

Review defect density measures the number of defects identified relative to the size of the artifact.

For example:

> 20 review defects identified across 200 test cases.

A simple measurement could be:

**Review Defect Density = Defects Found / Number of Test Cases**

In this example:

**20 / 200 = 0.10 defects per test case**

The exact organizational metric may differ.

---

# 36. What is Review Effectiveness?

Review effectiveness measures how effectively reviews identify defects before later stages.

For example:

If 100 defects are eventually discovered and 40 were identified during reviews:

**Review Effectiveness = 40 / 100 × 100 = 40%**

A higher percentage may indicate that reviews are successfully detecting issues early, although the metric should be interpreted in context.

---

# 37. Scenario: Reviewers Find Very Few Defects. Is That Always Good?

No.

A low defect count can mean:

* The artifact is high quality
* The artifact was already reviewed
* The review was ineffective
* Reviewers were not adequately prepared
* The checklist was incomplete
* Reviewers lacked domain knowledge
* The review was rushed

Metrics should always be analyzed with context.

---

# 38. Scenario: A Junior QA Engineer Is Afraid to Review a Senior QA Engineer's Work. What Would You Do?

I would create a collaborative review culture.

The review should focus on the artifact rather than the person's seniority.

I would encourage the junior engineer to use:

* Requirements
* Acceptance criteria
* Review checklist
* Testing standards

Everyone can identify defects regardless of experience level.

---

# 39. Scenario: The Author Becomes Defensive During Review. How Will You Handle It?

I would keep the discussion objective.

Instead of saying:

> "You made a mistake."

I would say:

> "This scenario doesn't appear to cover the requirement for invalid input. Can we verify whether this needs an additional test case?"

The focus should remain on the work product.

---

# 40. Scenario: Product Owner Says a Requirement Is Clear, but QA and Development Interpret It Differently. What Will You Do?

I would arrange a clarification discussion with:

* Product Owner
* Business Analyst
* Developer
* QA

I would document the agreed interpretation.

If necessary, I would update the acceptance criteria so that the behavior is unambiguous.

---

# 41. Scenario: How Do You Review an RTM?

I would verify that each requirement has appropriate test coverage.

For example:

| Requirement                  | Test Case | Status  |
| ---------------------------- | --------- | ------- |
| Login with valid credentials | TC-001    | Covered |
| Invalid password             | TC-002    | Covered |
| Account lockout              | TC-003    | Covered |
| Password expiration          | TC-004    | Missing |

I would identify:

* Requirements without test cases
* Test cases without requirements
* Incorrect mappings
* Missing coverage
* Obsolete mappings

---

# 42. Scenario: You Find a Test Case That Does Not Map to Any Requirement. What Will You Do?

I would determine why it exists.

Possible reasons:

* Requirement was missed
* Requirement changed
* Test case is obsolete
* Test case is an additional risk-based scenario
* Traceability is incomplete

If it is a valid test, I would ensure the requirement or rationale is properly documented.

---

# 43. Scenario: How Do You Review Regression Test Cases?

I would prioritize:

* Core business workflows
* High-risk functionality
* Frequently changed features
* Integration points
* Previously defective areas
* Customer-critical workflows

I would also identify obsolete or redundant regression cases.

---

# 44. Scenario: How Would You Review Automation Test Scripts?

I would check:

* Correct locator strategy
* Synchronization/waits
* Assertions
* Test data handling
* Reusability
* Maintainability
* Error handling
* Logging
* Screenshot/video capture where appropriate
* Avoidance of hard-coded values
* Cleanup
* Independent test execution
* Parallel execution safety
* Proper reporting

For automation frameworks, I would also review coding standards and framework architecture.

---

# 45. Scenario: An Automated Test Has No Assertion. What Would You Do?

I would consider it a major concern.

A test without meaningful validation may only perform actions without verifying the application's behavior.

I would identify the business outcome and add appropriate assertions.

For example:

Instead of only:

> Click Login.

Validate:

> User is successfully authenticated and redirected to the dashboard.

---

# 46. Scenario: How Do You Review Test Cases for Security?

Depending on the application, I would check scenarios such as:

* Authentication
* Authorization
* Role-based access
* Session timeout
* Password policies
* Sensitive data exposure
* Unauthorized URL access
* Input validation
* Access to another user's data
* Token/session handling

Security testing may require specialized security testers as well.

---

# 47. Scenario: How Do You Review Test Cases for Accessibility?

I would verify appropriate accessibility scenarios such as:

* Keyboard navigation
* Focus behavior
* Labels
* Screen-reader compatibility
* Color-independent information
* Accessible error messages
* Form controls
* Alternative text where applicable
* Zoom/responsive behavior

The exact coverage should align with the application's accessibility standards.

---

# 48. Scenario: A Critical Test Case Was Not Reviewed Before Execution. What Would You Do?

I would assess the risk immediately.

I would:

1. Identify the missing review.
2. Review the test case before further execution if possible.
3. Determine whether execution already occurred.
4. Check for coverage gaps.
5. Communicate the risk to the QA lead.
6. Perform retrospective review.
7. Improve the review process to prevent recurrence.

---

# 49. Scenario: You Have Very Limited Time Before Release. Would You Skip Test Case Review?

I would avoid completely skipping review for high-risk areas.

Instead, I would use **risk-based review**.

Priority:

1. Critical business functionality
2. High-risk changes
3. Customer-facing workflows
4. Security-sensitive functionality
5. Integration points
6. Remaining lower-risk functionality

A focused review is better than blindly skipping the process.

---

# 50. Scenario: What Would You Do If the Review Process Is Delaying the Release?

I would analyze whether the process itself is inefficient.

I would look for:

* Duplicate reviews
* Unnecessary approval layers
* Poorly defined checklists
* Manual repetitive work
* Late reviews
* Lack of ownership

I would propose shifting reviews earlier in the lifecycle and using risk-based review criteria.

The objective is not to eliminate reviews but to make them efficient.

---

# 51. Scenario: How Would You Conduct a Test Case Review in Agile?

In Agile, I would perform reviews continuously rather than waiting until the end of the sprint.

Typical flow:

1. Review user story
2. Review acceptance criteria
3. Identify test scenarios
4. Review test cases
5. Discuss with developers/PO
6. Update cases based on feedback
7. Execute tests
8. Review defects and coverage
9. Update regression coverage

This supports the Agile principle of early collaboration.

---

# 52. Scenario: Developer and QA Review a User Story Together. What Benefits Do You See?

Collaborative review can identify issues earlier.

Benefits include:

* Shared understanding
* Earlier ambiguity detection
* Better test coverage
* Better acceptance criteria
* Fewer implementation misunderstandings
* Faster defect resolution
* Improved team communication

---

# 53. Scenario: During Review You Identify a Missing Requirement, But Development Is Already Complete. What Will You Do?

I would not assume that the feature is correct simply because development is complete.

I would:

1. Raise the missing requirement.
2. Clarify expected behavior.
3. Perform impact analysis.
4. Determine whether development changes are needed.
5. Update test coverage.
6. Execute the appropriate tests.
7. Assess release risk.

---

# 54. Scenario: How Do You Prioritize Review Findings?

I would classify findings based on impact and risk.

### Critical

Could cause major business failure, security issue, or release blocker.

### High

Significant functional or customer impact.

### Medium

Important issue but with a workaround or limited impact.

### Low

Minor wording, formatting, or maintainability issue.

The classification should follow organizational standards.

---

# 55. Scenario: You Find a Typographical Error in a Test Case. Would You Report It?

Yes, but I would consider its impact.

If the typo could cause incorrect execution, I would definitely report it.

For example:

> Expected "Approve" but written as "Reject."

That is more serious than a simple spelling mistake.

---

# 56. Scenario: How Do You Review Test Cases for Internationalization?

I would check:

* Supported languages
* Translation accuracy
* Date formats
* Time formats
* Currency
* Number formats
* Address formats
* Character encoding
* Text expansion
* Right-to-left languages where applicable
* Locale-specific business rules

---

# 57. Scenario: How Do You Review Test Cases for Multiple Regions?

I would identify region-specific business rules.

For example:

* Country-specific validation
* Currency
* Language
* Address format
* Phone format
* Tax rules
* Dealer/service availability
* Regulatory requirements

I would avoid assuming that a test case valid for one region is automatically valid for every region.

---

# 58. Scenario: During Review You Find the Same Business Rule Tested in UI and API. Is That Duplicate Coverage?

Not necessarily.

UI and API tests validate different layers.

For example:

* API test validates backend business logic.
* UI test validates user-facing behavior and integration.

Some overlapping business validation may be intentional.

I would evaluate whether the coverage is valuable and whether each layer has a clear purpose.

---

# 59. Scenario: How Would You Review a Defect Report?

I would check:

* Clear title
* Environment
* Build/version
* Preconditions
* Steps to reproduce
* Actual result
* Expected result
* Reproducibility
* Severity
* Priority
* Evidence
* Logs
* Screenshots/video where useful
* Relevant test case
* Business impact

A good defect report should allow another person to understand and reproduce the issue.

---

# 60. Scenario: A Developer Cannot Reproduce Your Defect. What Will You Review?

I would review:

* Exact environment
* Application version
* Test data
* User account/role
* Preconditions
* Steps
* Timing
* Network conditions
* Logs
* Backend state
* Database data

I would attempt reproduction again and provide additional evidence.

I would avoid immediately assuming that the developer is wrong.

---

# 61. Scenario: What Is the Difference Between Review and Testing?

**Review** is generally a static activity.

It examines work products without executing the software.

Examples:

* Requirement review
* Test case review
* Code review
* Documentation review

**Testing** generally involves executing the software or system to evaluate behavior.

Both activities complement each other.

---

# 62. Scenario: Why Is Static Testing Important?

Static testing can identify defects before execution.

Examples include:

* Ambiguous requirements
* Missing acceptance criteria
* Incorrect test cases
* Inconsistent specifications
* Coding standard violations

The earlier a defect is found, the cheaper it is generally to correct.

---

# 63. Scenario: What Would You Review Before Starting Test Execution?

I would verify:

* Approved requirements
* Acceptance criteria
* Test scenarios
* Test cases
* Test data
* Test environment
* Build/version
* Dependencies
* RTM
* Entry criteria
* Known limitations
* Required accounts/access

This ensures the team is ready for execution.

---

# 64. Scenario: A Test Case Review Reveals That the Environment Cannot Support the Scenario. What Will You Do?

I would identify the environmental dependency and communicate it before execution.

For example:

> The test requires a downstream payment gateway, but the test environment does not have the gateway configured.

I would determine whether to:

* Configure the environment
* Use a mock
* Use a stub
* Execute in another environment
* Mark the test as blocked

The decision depends on the testing objective.

---

# 65. Scenario: How Do You Handle Review Comments That You Disagree With?

I would first understand the reviewer's reasoning.

Then I would:

1. Refer to the requirement.
2. Explain my reasoning.
3. Discuss the business impact.
4. Seek clarification if needed.
5. Escalate only when necessary.

I would document the final decision when the issue affects test coverage or requirements.

---

# 66. Scenario: What Is a Walkthrough?

A walkthrough is generally an informal review where the author leads participants through a work product.

For example:

A QA engineer walks the team through newly created test cases and explains:

* Test objectives
* Scenarios
* Test data
* Expected results
* Coverage

Participants provide feedback and identify issues.

---

# 67. Scenario: What Is an Audit?

An audit evaluates whether processes, standards, and required procedures are being followed.

For example, a QA audit might verify:

* Required test artifacts exist
* Test execution evidence is maintained
* Defects are properly tracked
* Approvals are documented
* Required standards are followed

An audit is different from simply reviewing the correctness of an individual test case.

---

# 68. Scenario: What Would You Include in a Review Exit Criteria?

Possible exit criteria include:

* Required reviewers completed the review
* Findings are documented
* Critical issues are resolved
* Required corrections are completed
* Follow-up review is completed
* Approval is obtained where required
* Review results are recorded

---

# 69. Scenario: What Would You Do If Reviewers Missed a Major Defect?

I would treat it as a process improvement opportunity.

I would perform a root-cause analysis.

Possible causes:

* Incomplete checklist
* Lack of domain knowledge
* Insufficient preparation
* Time pressure
* Poor requirements
* Incorrect review technique
* Reviewer overload

Then I would improve the process rather than blaming individuals.

---

# 70. Scenario: How Would You Explain the Value of Test Reviews to Management?

I would explain that test reviews help:

* Detect defects early
* Improve requirement coverage
* Reduce test execution rework
* Improve test quality
* Reduce production risk
* Improve collaboration
* Increase confidence in release quality

For example:

> Finding a missing critical test scenario during test case review is much cheaper than discovering the missing coverage after production release.

---

# 71. Scenario: What Would You Do If a Test Case Has Good Coverage but Is Difficult to Understand?

I would improve readability.

I would check:

* Test case title
* Step clarity
* Expected result
* Terminology
* Preconditions
* Test data
* Formatting

A test case should be understandable to another tester without requiring extensive explanation from the author.

---

# 72. Scenario: What Is the Most Important Principle During Test Review?

The most important principle is:

> **Focus on the quality of the work product, not the person who created it.**

The purpose of review is defect prevention and quality improvement, not personal criticism.

---

# 73. Senior-Level Scenario: You Join a Project Where Test Reviews Are Not Being Performed. What Will You Do?

I would first understand why reviews are not happening.

I would assess:

* Current QA process
* Defect trends
* Production issues
* Test case quality
* Team capacity
* Release timelines

Then I would introduce a lightweight review process.

For example:

1. Requirement review
2. Test scenario review
3. Test case peer review
4. Risk-based review for critical areas
5. Review checklist
6. Review metrics

I would avoid introducing unnecessary bureaucracy.

---

# 74. Senior-Level Scenario: Production Defects Keep Escaping Despite Test Case Reviews. What Will You Investigate?

I would perform root-cause analysis.

I would investigate:

* Requirement quality
* Test coverage
* Review effectiveness
* Test data
* Environment differences
* Integration gaps
* Non-functional testing
* Regression coverage
* Production configuration
* Monitoring
* Automation coverage

I would compare escaped defects against review findings to determine where the process is failing.

---

# 75. Senior-Level Scenario: How Would You Improve an Ineffective Test Review Process?

I would use a continuous improvement approach.

### Step 1 – Identify the problem

Analyze escaped defects and review findings.

### Step 2 – Identify root causes

Determine whether issues are related to:

* Reviewers
* Process
* Requirements
* Tools
* Knowledge
* Time constraints

### Step 3 – Improve the process

Introduce:

* Risk-based reviews
* Checklists
* Early reviews
* Pair reviews
* Requirement walkthroughs
* Review metrics

### Step 4 – Measure

Track:

* Review defects
* Escaped defects
* Rework
* Coverage
* Review completion

### Step 5 – Continuously improve

Update the checklist and review approach based on lessons learned.

---

# 76. Senior-Level Scenario: How Would You Handle Test Review in a Large Distributed Team?

I would use collaboration tools and a defined review workflow.

For example:

1. Store test artifacts in a shared repository.
2. Assign reviewers.
3. Use comments for review findings.
4. Define review deadlines.
5. Conduct short review meetings for complex issues.
6. Track unresolved comments.
7. Maintain approval status.
8. Document final decisions.

This provides traceability even when team members are in different locations.

---

# 77. Senior-Level Scenario: How Would You Review Testing for a High-Risk Financial Transaction?

I would apply risk-based and detailed review.

I would check:

* Business rules
* Authorization
* Transaction limits
* Duplicate transactions
* Currency
* Rounding
* Failure handling
* Timeout behavior
* Retry behavior
* Audit logs
* Security
* Database consistency
* API responses
* UI confirmation
* Notifications
* Reconciliation

I would also ensure that critical test cases receive appropriate peer or formal review.

---

# 78. Senior-Level Scenario: A Requirement Has 10 Acceptance Criteria but Only 5 Test Cases. Is That a Problem?

Not automatically.

One test case may cover multiple acceptance criteria.

I would inspect the actual traceability rather than comparing the numbers.

The important question is:

> Is every acceptance criterion adequately validated?

If five acceptance criteria are not covered, then there is a coverage gap.

---

# 79. Senior-Level Scenario: How Would You Review Test Coverage for a New Feature?

I would start from the requirements and build coverage systematically.

### Coverage areas

* Functional
* Negative
* Boundary
* Integration
* API
* UI
* Database
* Security
* Performance
* Compatibility
* Accessibility
* Localization
* Regression

The exact scope depends on the feature's risk and architecture.

---

# 80. Senior-Level Scenario: How Do You Balance Review Quality Against Sprint Time?

I would use **risk-based review** rather than applying the same review depth to every artifact.

### High risk

Detailed review with multiple reviewers.

### Medium risk

Peer review using a checklist.

### Low risk

Lightweight review.

This maintains quality without creating unnecessary delays.

---

# 81. Interview Question: What Is Your Approach to Test Case Review?

### Sample Senior QA Answer

> "I start by understanding the requirement and acceptance criteria. Then I verify that the test cases provide complete coverage, including positive, negative, boundary, integration, and error scenarios. I also review preconditions, test data, expected results, traceability, and maintainability. For high-risk functionality, I perform a deeper review and involve appropriate domain or technical stakeholders. I document review findings, follow up on corrections, and continuously improve the review checklist based on defects and lessons learned."

---

# 82. Interview Question: How Do You Handle Disagreements During Test Reviews?

### Sample Answer

> "I keep the discussion objective and refer to the requirement, acceptance criteria, business rules, or technical evidence. I listen to the other person's reasoning and try to reach a common understanding. If the requirement is ambiguous, I involve the Product Owner or Business Analyst. My goal is not to prove that my test case is correct but to ensure that the final coverage reflects the intended product behavior."

---

# 83. Interview Question: How Do You Ensure Test Cases Have Complete Coverage?

### Sample Answer

> "I trace test cases back to requirements and acceptance criteria using the RTM where applicable. I verify positive, negative, boundary, error-handling, integration, and risk-based scenarios. I also consider changes to existing functionality and previously identified production defects. For high-risk features, I perform peer reviews and use a checklist to reduce the chance of missing important scenarios."

---

# 84. Interview Question: What Would You Do If a Team Does Not Have Time for Test Reviews?

### Sample Answer

> "I would not recommend eliminating reviews completely. Instead, I would prioritize reviews based on risk. Critical functionality and major changes would receive detailed reviews, while low-risk changes could receive lightweight peer reviews. I would also look for ways to move reviews earlier in the sprint so that issues are identified before test execution."

---

# 85. Interview Question: How Do Reviews Help Shift Testing Left?

### Sample Answer

> "Reviews are one of the key activities that support shift-left testing because they allow the team to identify defects before code execution. Reviewing requirements, acceptance criteria, and test scenarios early helps prevent misunderstandings and coverage gaps. This reduces downstream rework and improves overall quality."

---

# 86. Interview Question: What Is the Difference Between Verification and Validation?

### Verification asks:

> **Are we building the product right?**

Examples:

* Requirement review
* Test case review
* Design review
* Code review
* Documentation review

Validation asks:

> **Are we building the right product?**

Examples:

* Executing functional tests
* User acceptance testing
* System testing
* End-to-end testing

---

# 87. Interview Question: Which Review Technique Do You Prefer?

### Sample Answer

> "I don't use one review technique for every situation. For routine test cases, I prefer lightweight peer review using a checklist. For complex or high-risk functionality, I prefer a more structured review involving QA, development, and business stakeholders. The technique should be based on risk, complexity, and project needs."

---

# 88. Interview Question: How Do You Know Whether a Review Process Is Effective?

### Sample Answer

> "I look at review completion, review defects, rework, escaped defects, and defect trends. I also analyze whether the defects found in later phases could reasonably have been detected during reviews. The goal is not simply to maximize the number of review defects, but to identify meaningful issues early and reduce downstream defects."

---

# 89. Interview Question: What Are Common Mistakes During Test Case Reviews?

Common mistakes include:

* Reviewing without understanding requirements
* Focusing only on formatting
* Ignoring negative scenarios
* Ignoring boundary conditions
* Not validating expected results
* Not checking test data
* Ignoring integration scenarios
* Not reviewing recently changed functionality
* Treating review as an approval formality
* Failing to follow up on review comments

---

# 90. Final Senior QA Interview Scenario

## Scenario

You are the QA lead for a major release. The team has completed 1,000 test cases. Only 20% have been peer-reviewed. The release is scheduled for tomorrow, and management asks whether testing is ready.

### How would you respond?

I would not simply say "yes" or "no" based only on the percentage reviewed.

I would assess:

1. Which unreviewed cases are high risk?
2. Which features have changed?
3. Which business-critical workflows are involved?
4. What percentage of critical test cases are reviewed?
5. Are there known coverage gaps?
6. Are there unresolved review findings?
7. What defects have already been identified?
8. Are entry and exit criteria satisfied?
9. What is the remaining testing risk?

I would then provide management with a risk-based status.

### Example response

> "Testing is progressing, but I would not consider the release risk-free because only 20% of the test cases have been peer-reviewed. I am currently prioritizing reviews for critical business workflows, high-risk changes, and integration areas. I will provide the remaining review gaps, known defects, coverage status, and associated release risks so that the release decision can be made based on evidence."

This demonstrates senior-level QA ownership because it focuses on **risk, coverage, evidence, and transparency** rather than simply reporting a percentage.

---

# Key Takeaways for QA Interviews

Remember these points:

1. **Review is primarily a static quality activity.**
2. **Inspection is a formal and structured review technique.**
3. **Peer review helps detect defects early.**
4. **Requirements and acceptance criteria should drive test coverage.**
5. **Positive, negative, boundary, and error scenarios should be considered.**
6. **RTM helps verify traceability and coverage.**
7. **Review comments should focus on the artifact, not the person.**
8. **Ambiguous requirements should be clarified rather than assumed.**
9. **Risk-based reviews are useful when time is limited.**
10. **Review effectiveness should be measured using meaningful metrics.**
11. **Reviews support shift-left testing and defect prevention.**
12. **High-risk functionality deserves deeper review.**
13. **A low number of review defects does not automatically mean a good review.**
14. **Review processes should continuously improve based on escaped defects and lessons learned.**
15. **A senior QA engineer communicates release risk clearly rather than simply saying "testing is complete."**

---

# Quick Interview Framework

When answering any **Test Review / Inspection scenario**, use this structure:

### 1. Understand

* Requirement
* Acceptance criteria
* Business objective

### 2. Analyze

* Risk
* Coverage
* Dependencies
* Test data
* Environment

### 3. Review

* Positive scenarios
* Negative scenarios
* Boundary conditions
* Error handling
* Integration
* Non-functional considerations

### 4. Communicate

* Document findings
* Discuss disagreements professionally
* Escalate ambiguities

### 5. Correct

* Update test artifacts
* Update requirements when necessary
* Update RTM
* Re-review critical changes

### 6. Improve

* Analyze escaped defects
* Update review checklist
* Improve review process
* Apply lessons learned

> **Senior QA mindset:** A good review is not about finding the maximum number of comments. It is about finding meaningful defects early, improving test coverage, reducing downstream risk, and creating shared understanding across the team.
