# Requirement Analysis – Real-Time / Scenario-Based Interview Questions

## File Name

`Manual-QA/Requirement-Analysis-Real-Time-Scenario-Based-Interview-Questions.md`

---

# 1. What is Requirement Analysis in Software Testing?

Requirement Analysis is the process of understanding, reviewing, clarifying, and evaluating business and technical requirements before designing and executing test cases.

As a QA engineer, the goal is not just to understand **what the application should do**, but also to identify:

* Missing requirements
* Ambiguous requirements
* Conflicting requirements
* Missing validations
* Boundary conditions
* Negative scenarios
* Integration dependencies
* Business rules
* Data requirements
* Non-functional requirements
* Risks

### Interview Answer

> Requirement analysis is one of the most important activities in the testing lifecycle. I review the requirements from both business and testing perspectives, identify ambiguities, missing scenarios, dependencies, and risks, and clarify them with the BA, product owner, developers, or stakeholders before creating test cases.

---

# 2. What do you do when you receive a new requirement?

### Real-Time Approach

I generally follow these steps:

1. Read the requirement completely.
2. Understand the business objective.
3. Identify the application/module affected.
4. Identify impacted existing functionality.
5. Identify positive scenarios.
6. Identify negative scenarios.
7. Identify boundary conditions.
8. Identify validation rules.
9. Identify dependencies.
10. Identify required test data.
11. Identify API/database/integration dependencies.
12. Review acceptance criteria.
13. Raise questions for ambiguous requirements.
14. Discuss the requirement with BA/PO/developer.
15. Update my understanding based on clarification.
16. Prepare test scenarios and test cases.
17. Perform requirement traceability.

### Interview Answer

> Whenever I receive a new requirement, I first understand the business objective and acceptance criteria. Then I analyze positive, negative, boundary, integration, validation, and dependency scenarios. If anything is unclear, I raise questions with the BA or Product Owner before starting test case development.

---

# 3. What do you look for while reviewing requirements?

I check the following areas:

### Functional Requirements

* What should the feature do?
* What happens when the user performs an action?
* What are the expected results?
* What validations are required?

### Business Rules

* Who can use the feature?
* What conditions should be satisfied?
* Are there region-specific rules?
* Are there role-based restrictions?

### Input Validation

* Mandatory fields
* Optional fields
* Minimum length
* Maximum length
* Data type
* Special characters
* Invalid values
* Boundary values

### Error Handling

* What error message should appear?
* What happens when an API fails?
* What happens when data is unavailable?
* What happens during timeout?

### Integration

* API dependencies
* Database dependencies
* Third-party systems
* Authentication
* External services

### Non-Functional Requirements

* Performance
* Security
* Accessibility
* Compatibility
* Scalability
* Reliability

---

# 4. What is an ambiguous requirement?

An ambiguous requirement is a requirement that can be interpreted in more than one way.

### Example

Requirement:

> "The user should be able to search for a dealer."

This does not explain:

* Search by dealer name?
* Search by ZIP code?
* Search by city?
* Partial search?
* Case-sensitive search?
* What happens if no dealer exists?
* How many results should be displayed?

### Interview Answer

> An ambiguous requirement is one where the expected behavior is not clearly defined. I don't make assumptions. I document the question and clarify it with the appropriate stakeholder before finalizing test scenarios.

---

# 5. What would you do if the requirement is unclear?

### Scenario

The requirement says:

> "Password must contain special characters."

But it does not specify:

* Minimum length
* Maximum length
* Allowed special characters
* Number of special characters
* Whether spaces are allowed

### Approach

I would raise clarification questions.

### Example Questions

* What is the minimum password length?
* What is the maximum length?
* Which special characters are allowed?
* Is at least one special character mandatory?
* Are spaces allowed?
* Are consecutive special characters allowed?

### Interview Answer

> I would not proceed based on assumptions. I would document the ambiguity and discuss it with the BA or Product Owner. Once clarified, I would update the test scenarios and test cases accordingly.

---

# 6. What if the BA says, "Use your assumption"?

This can happen in real projects.

### Good Approach

I would document the assumption clearly.

For example:

> Assumption: Password must contain at least one special character and the supported special characters are `@`, `#`, `$`, `%`.

Then I would ensure the BA/PO agrees with the assumption.

### Interview Answer

> If the stakeholder asks me to proceed with an assumption, I document the assumption explicitly and get confirmation. This prevents future disagreements about expected behavior.

---

# 7. How do you identify missing requirements?

I analyze the requirement using different perspectives.

### Example

Requirement:

> "Customer can add a vehicle using VIN."

I would ask:

* What is the VIN format?
* How many characters?
* Are lowercase letters accepted?
* What if VIN is invalid?
* What if VIN does not exist?
* What if VIN already exists?
* Can the same VIN belong to multiple users?
* What happens if the backend is unavailable?
* What happens if the vehicle is already associated?
* Are there region restrictions?
* Are there model-year restrictions?
* What happens for an unsupported vehicle?

These questions help identify missing requirements.

---

# 8. What is Acceptance Criteria?

Acceptance Criteria defines the conditions that must be satisfied for a feature or user story to be considered complete and acceptable.

### Example

User Story:

> As a customer, I want to add my vehicle using VIN.

Acceptance Criteria:

```text
Given the user is logged in
When the user enters a valid VIN
And submits the request
Then the vehicle should be successfully added
```

Another:

```text
Given the user enters an invalid VIN
When the user submits the request
Then an appropriate validation message should be displayed
```

### QA Perspective

Acceptance criteria provides the foundation for:

* Test scenarios
* Test cases
* Automation
* Acceptance testing
* Requirement traceability

---

# 9. What if acceptance criteria is missing?

### Interview Answer

> I would not immediately assume the expected behavior. I would discuss it with the Product Owner or BA and request acceptance criteria. If the team follows a Definition of Ready, I would also verify whether the story meets the criteria required for QA analysis.

---

# 10. What is a good requirement?

A good requirement should be:

* Clear
* Complete
* Consistent
* Testable
* Feasible
* Unambiguous
* Traceable
* Measurable

### Example

Bad:

> System should load quickly.

Good:

> The dashboard should load within 3 seconds for 95% of requests under the defined normal load.

The second requirement is much easier to test.

---

# 11. How do you determine whether a requirement is testable?

Ask:

> Can I define a clear test condition and expected result?

### Example

Not easily testable:

> Application should be user-friendly.

Better:

> A new user should be able to complete vehicle registration within five steps without assistance.

The second requirement provides measurable behavior.

---

# 12. What is Requirement Traceability?

Requirement Traceability means mapping requirements to corresponding test scenarios/test cases.

A common representation is the **RTM – Requirement Traceability Matrix**.

### Example

| Requirement ID | Requirement    | Test Case IDs          |
| -------------- | -------------- | ---------------------- |
| REQ-001        | User login     | TC-001, TC-002, TC-003 |
| REQ-002        | Add vehicle    | TC-004, TC-005, TC-006 |
| REQ-003        | Delete vehicle | TC-007, TC-008         |

### Purpose

RTM helps ensure:

* Every requirement is tested.
* No requirement is missed.
* Test coverage can be measured.
* Impact analysis is easier.

---

# 13. What if one requirement has many test cases?

That is completely normal.

For example:

Requirement:

> User should be able to log in.

Possible test cases:

* Valid username/password
* Invalid username
* Invalid password
* Both invalid
* Empty username
* Empty password
* Both empty
* Locked account
* Expired password
* SQL injection
* Password case sensitivity
* Session timeout
* Remember-me behavior
* Multiple failed attempts

One requirement can therefore have many test cases.

---

# 14. What if one test case covers multiple requirements?

This can also happen.

For example:

A checkout test may validate:

* Login
* Cart
* Pricing
* Tax
* Payment
* Order creation

However, I prefer maintaining clear traceability so that each requirement has identifiable coverage.

---

# 15. What do you do when requirements conflict?

### Scenario

Requirement A says:

> Maximum username length is 20 characters.

Requirement B says:

> Maximum username length is 30 characters.

### Approach

I would:

1. Identify the conflict.
2. Document it.
3. Notify the BA/PO.
4. Avoid making assumptions.
5. Get a confirmed decision.
6. Update the requirement/documentation.
7. Update test cases.

### Interview Answer

> I would never silently choose one requirement. Conflicting requirements need stakeholder clarification because testing against the wrong interpretation can result in incorrect defect reports.

---

# 16. What if the requirement changes after you create test cases?

This is common in Agile projects.

### Approach

1. Understand the change.
2. Perform impact analysis.
3. Identify affected test cases.
4. Update existing test cases.
5. Add new scenarios.
6. Remove obsolete scenarios.
7. Update automation if required.
8. Execute regression testing.

### Interview Answer

> Requirement changes are expected in Agile. I perform impact analysis first and determine which test cases, automation scripts, integrations, and regression areas are affected. Then I update the test assets and execute the appropriate regression suite.

---

# 17. What is Impact Analysis?

Impact Analysis identifies what existing functionality may be affected by a new requirement or code change.

### Example

A new requirement changes vehicle onboarding.

Potential impact:

```text
Vehicle Registration
        |
        +-- VIN Validation
        |
        +-- Customer Profile
        |
        +-- Vehicle Database
        |
        +-- Subscription
        |
        +-- Connected Services
        |
        +-- Notifications
        |
        +-- Mobile App
```

A seemingly small requirement can therefore affect multiple systems.

---

# 18. How do you identify regression scope from a requirement?

I look at:

* Changed functionality
* Direct dependencies
* APIs
* Database changes
* Shared components
* UI changes
* Authentication
* Notifications
* Downstream systems
* Existing automation
* Previous defects

Then I categorize regression testing into:

### Smoke

Basic application health.

### Functional Regression

Affected functionality.

### Integration Regression

Dependent systems.

### Full Regression

High-risk or major releases.

---

# 19. What if a requirement only describes the happy path?

### Example

> User enters valid VIN and vehicle is added successfully.

This describes only the positive scenario.

I would ask about:

* Invalid VIN
* Empty VIN
* Duplicate VIN
* Unsupported VIN
* Incorrect VIN length
* Backend failure
* Network failure
* Timeout
* Unauthorized user
* Vehicle already associated
* Region-specific behavior

### Interview Answer

> I don't limit testing to the happy path. I derive negative, boundary, validation, error-handling, security, and integration scenarios from the requirement.

---

# 20. How do you derive negative test cases from requirements?

I ask:

> "What can go wrong?"

### Example

Requirement:

> User can update phone number.

Negative scenarios:

* Empty phone number
* Invalid format
* Too short
* Too long
* Alphabetic characters
* Special characters
* Unsupported country code
* Duplicate number
* Backend failure
* Unauthorized request
* Session timeout

---

# 21. How do you derive boundary test cases?

Suppose requirement says:

> Username must contain 5–20 characters.

Boundary values:

```text
4   → Invalid
5   → Valid
6   → Valid
19  → Valid
20  → Valid
21  → Invalid
```

### Interview Answer

> I identify minimum, maximum, just below minimum, just above maximum, and valid values around the boundary. This helps identify defects that may not be found through normal positive testing.

---

# 22. How do you handle region-specific requirements?

This is especially important in applications operating across multiple countries or regions.

### Example

A vehicle onboarding requirement may behave differently for:

* US
* Canada
* Puerto Rico
* Hawaii
* Mexico

I would identify:

* Region-specific business rules
* Supported languages
* Currency
* Address format
* VIN rules
* Dealer availability
* API behavior
* Legal/compliance requirements
* Feature availability

### Interview Answer

> I treat region as an important test dimension. I don't assume that functionality working in one region automatically means it works in another region.

---

# 23. How do you handle language-specific requirements?

Suppose a requirement says:

> The application should support English and Spanish.

I would validate:

* UI labels
* Buttons
* Error messages
* Validation messages
* Dialogs
* Notifications
* Backend error translations
* Date format
* Number format
* Special characters
* Text truncation

I would also verify language consistency across the entire user journey.

---

# 24. How do you handle requirements involving APIs?

I identify:

* HTTP method
* Endpoint
* Request parameters
* Headers
* Authentication
* Request body
* Response status
* Response schema
* Error responses
* Timeout behavior
* Retry behavior
* Data persistence

### Example

Requirement:

> User submits VIN and system validates it through backend service.

I would test:

```text
UI
 ↓
API
 ↓
Validation Service
 ↓
Database
 ↓
API Response
 ↓
UI
```

Testing should cover the entire chain where appropriate.

---

# 25. How do you handle requirements involving database validation?

I identify:

* What data should be stored?
* Which table/collection?
* Which fields?
* Expected values?
* Data relationships?
* Insert/update behavior?
* Duplicate handling?

### Example

If the UI says:

> Vehicle added successfully.

I may verify:

```text
UI
 ↓
API
 ↓
Database
```

to confirm that the vehicle was actually persisted correctly.

---

# 26. What if the requirement says "system should send a notification"?

I would ask:

* Email?
* SMS?
* Push notification?
* When should it be sent?
* Who receives it?
* What content?
* What happens if notification service fails?
* Should it retry?
* How many times?
* Is duplicate notification allowed?

### Test Scenarios

* Successful notification
* Notification failure
* Delayed notification
* Duplicate notification
* Invalid recipient
* Service unavailable
* Retry behavior

---

# 27. What if the requirement has no error-handling information?

I would raise questions such as:

> What should happen if the backend service is unavailable?

> What message should the user see?

> Should the application retry?

> Should the transaction be rolled back?

> Should the user be allowed to continue?

This is important because error handling is part of expected behavior.

---

# 28. How do you identify dependencies during requirement analysis?

I look for:

### Internal Dependencies

* Authentication
* User profile
* Database
* APIs
* Other modules

### External Dependencies

* Payment gateway
* Notification service
* Dealer service
* Third-party API
* Identity provider

### Environment Dependencies

* Stage
* QA
* Production
* Test data
* Feature flags
* Configuration

I document these dependencies before test execution.

---

# 29. What if a requirement depends on another feature that is not ready?

### Scenario

Feature B depends on Feature A, but Feature A is still under development.

### Approach

I would:

1. Identify the dependency.
2. Notify the team.
3. Determine whether mocking/stubbing is possible.
4. Prepare test cases.
5. Test independent functionality where possible.
6. Track blocked scenarios.
7. Execute dependent testing once the dependency becomes available.

### Interview Answer

> I don't wait unnecessarily. I prepare test cases and test independent portions while tracking the dependency as a blocker for the dependent scenarios.

---

# 30. What is Requirement Review?

Requirement Review is a collaborative activity where team members examine requirements before implementation.

Participants may include:

* Product Owner
* Business Analyst
* QA
* Developer
* Architect
* Scrum Master
* Subject Matter Expert

### QA Contribution

QA should challenge the requirement from a testing perspective.

For example:

> What happens when the service returns HTTP 500?

> What happens when the user enters duplicate data?

> What happens if the network disconnects?

---

# 31. Should QA participate in requirement discussions?

### Strong Interview Answer

> Absolutely. QA involvement should start as early as possible. Early QA participation helps identify ambiguities, missing acceptance criteria, negative scenarios, dependencies, and risks before development begins. This reduces the cost of fixing defects later.

---

# 32. What is Shift-Left Testing?

Shift-left means moving testing activities earlier in the software development lifecycle.

Instead of:

```text
Development → QA → Defects
```

we try to have:

```text
Requirement
    ↓
QA Review
    ↓
Design Review
    ↓
Development
    ↓
Testing
```

### Benefits

* Earlier defect detection
* Lower cost of fixing defects
* Better requirements
* Better test coverage
* Reduced rework

---

# 33. Give an example where you found a defect during requirement analysis.

### Sample Senior QA Answer

> During requirement review, I noticed that a feature described the successful flow but did not specify what should happen when the backend service returned an error. I raised the question with the BA and Product Owner. We clarified the expected error message and retry behavior before development was completed. I then added positive, negative, and service-failure scenarios to the test coverage.

This demonstrates **preventive QA**, not just defect detection.

---

# 34. What is Requirement Risk Analysis?

Requirement Risk Analysis identifies areas where incorrect behavior could have a significant business or customer impact.

### High-Risk Examples

* Payment
* Authentication
* Customer data
* Vehicle registration
* Subscription
* Security
* Data deletion
* Financial calculations
* Regulatory workflows

### Low-Risk Examples

* Minor UI alignment
* Cosmetic text changes
* Non-critical styling

Testing priority should reflect risk.

---

# 35. How do you prioritize requirements for testing?

I consider:

1. Business impact
2. Customer impact
3. Technical complexity
4. Change frequency
5. Defect history
6. Integration complexity
7. Security risk
8. Regulatory impact
9. Probability of failure

### Example

A payment requirement would generally receive higher priority than a minor UI color change.

---

# 36. What if the Product Owner says there is no time for complete testing?

### Senior-Level Answer

> I would communicate the risk rather than simply saying testing cannot be completed. I would prioritize critical business flows, high-risk functionality, integration points, and areas affected by the change. I would document what was tested, what was not tested, and the associated risks so stakeholders can make an informed release decision.

---

# 37. What is a Requirement Coverage Gap?

A coverage gap exists when a requirement does not have adequate test coverage.

### Example

Requirements:

```text
REQ-001 Login
REQ-002 Password Reset
REQ-003 MFA
```

Test cases:

```text
TC-001 Login
TC-002 Password Reset
```

MFA has no coverage.

Therefore:

```text
REQ-003 → Coverage Gap
```

---

# 38. Scenario: Requirement says "User should be able to delete an account." What would you ask?

I would ask:

* Is deletion permanent?
* Is soft deletion used?
* Is confirmation required?
* Is password verification required?
* Is MFA required?
* What happens to associated data?
* What happens to subscriptions?
* What happens to vehicles?
* Can the account be recovered?
* What happens to active sessions?
* What notification is sent?
* Are there regulatory/data-retention requirements?

This demonstrates real-world requirement analysis.

---

# 39. Scenario: Requirement says "User can upload a document." What scenarios would you derive?

### Positive

* Valid file
* Supported file type
* Maximum allowed size

### Negative

* Unsupported file type
* Empty file
* Corrupted file
* Oversized file
* Duplicate file
* Filename with special characters
* Very long filename
* Network interruption

### Security

* Malicious file
* Executable file
* Unauthorized upload
* Path traversal attempts

---

# 40. Scenario: Requirement says "Search should return matching results." What would you clarify?

I would ask:

* Exact match or partial match?
* Case-sensitive?
* Starts-with or contains?
* Minimum search characters?
* Maximum search characters?
* Special characters?
* Spaces?
* Numeric values?
* Pagination?
* Sorting?
* No-result behavior?
* Maximum result count?
* Search timeout?

---

# 41. Scenario: Requirement says "User should be able to book an appointment."

I would analyze:

### Preconditions

* User must be logged in.
* Vehicle must exist.
* Dealer must be available.

### Positive Flow

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
Appointment Created
```

### Negative Scenarios

* Dealer unavailable
* No available slots
* Invalid vehicle
* Expired session
* Network failure
* Appointment conflict
* Backend failure
* Slot becomes unavailable during booking

### Integration

* Dealer service
* Appointment API
* Database
* Notification service

---

# 42. How would you analyze a requirement for a mobile application?

I consider:

* iOS
* Android
* OS versions
* Device sizes
* Orientation
* Network conditions
* Permissions
* Push notifications
* Deep links
* Background/foreground behavior
* App restart
* Session persistence
* Offline behavior
* Localization
* Accessibility

A mobile requirement should not be tested only on the happy path.

---

# 43. What questions do you ask during backlog refinement?

Typical QA questions include:

* What is the expected behavior?
* What are the acceptance criteria?
* What are the negative scenarios?
* What are the boundary conditions?
* Are there dependencies?
* Are there region-specific rules?
* Are there role-based restrictions?
* What happens when the API fails?
* What test data is required?
* Are there UI/UX specifications?
* Are there security requirements?
* Are there performance expectations?
* What existing functionality could be impacted?

---

# 44. What is Definition of Ready?

Definition of Ready is a team's agreed criteria for determining whether a story is sufficiently prepared for development.

Typical criteria:

* Requirement is clear.
* Acceptance criteria are available.
* Dependencies are identified.
* Designs are available if required.
* Testability is understood.
* Business rules are defined.
* Required data is understood.

### Interview Answer

> As QA, I use Definition of Ready as a quality gate to make sure a story is sufficiently clear and testable before development begins.

---

# 45. What is Definition of Done?

Definition of Done defines the conditions that must be satisfied for a story to be considered completed.

Typical items:

* Development completed
* Code reviewed
* Unit tests passed
* QA testing completed
* Regression completed
* Defects resolved
* Acceptance criteria satisfied
* Documentation updated

---

# 46. Difference Between Requirement Analysis and Test Case Design

| Requirement Analysis       | Test Case Design                           |
| -------------------------- | ------------------------------------------ |
| Understand requirements    | Convert requirements into executable tests |
| Identify ambiguities       | Define test steps                          |
| Identify risks             | Define expected results                    |
| Identify dependencies      | Prepare test data                          |
| Identify business rules    | Map test cases to requirements             |
| Identify missing scenarios | Cover positive/negative/boundary cases     |

### Simple Explanation

```text
Requirement
    ↓
Requirement Analysis
    ↓
Questions / Clarifications
    ↓
Test Scenarios
    ↓
Test Cases
    ↓
Execution
```

---

# 47. Senior QA Scenario: Developer says, "Requirement is clear. Why are you asking so many questions?"

### Strong Answer

> My goal is not to delay development. I want to make sure the expected behavior is understood before implementation. Clarifying questions during requirement analysis can prevent defects, rework, and misunderstandings later in the cycle.

---

# 48. Senior QA Scenario: BA changes the requirement verbally

### What should you do?

Do not rely only on a verbal discussion.

I would request the requirement or acceptance criteria to be updated in the team's official documentation or tracking system.

### Interview Answer

> I prefer requirements and decisions to be documented so that development, QA, and stakeholders have a common source of truth.

---

# 49. Senior QA Scenario: Developer says, "That's not a bug; requirement didn't mention it."

This is a common interview scenario.

### Response

I would check:

1. Requirement
2. Acceptance criteria
3. Design
4. Business rules
5. Previous behavior
6. Product Owner clarification

If expected behavior is genuinely undefined, I would discuss it with the BA/PO instead of arguing based solely on assumptions.

### Strong Answer

> I focus on establishing the expected behavior rather than arguing whether something is a bug. Once the expected behavior is confirmed, we can correctly classify the issue.

---

# 50. Senior QA Scenario: Requirement is technically correct but difficult to test

### What would you do?

I would discuss testability with the team.

Possible solutions:

* Add logging
* Add API-level validation
* Add test hooks
* Improve error messages
* Add test data controls
* Add environment configuration
* Add observability
* Provide mock services

### Senior QA Perspective

> Testability should be considered during requirement and design discussions, not after development is complete.

---

# 51. How do you document requirement clarification?

I prefer documenting:

```text
Requirement ID:
Question:
Business Impact:
Clarification:
Decision:
Decision Owner:
Date:
Test Cases Impacted:
```

### Example

```text
Requirement: Vehicle Search

Question:
Should search support partial dealer names?

Clarification:
Yes, partial and case-insensitive search are supported.

Decision Owner:
Product Owner

Test Impact:
Add partial-search and case-insensitive-search scenarios.
```

---

# 52. How do you handle requirements with external dependencies?

I document:

```text
Requirement
   ↓
Dependency
   ↓
Expected Dependency Response
   ↓
Application Behavior
```

Then I test:

* Dependency available
* Dependency unavailable
* Slow response
* Invalid response
* Timeout
* HTTP error
* Empty response
* Unexpected response

---

# 53. How do you handle requirements with feature flags?

I consider both states:

```text
Feature Flag ON
    ↓
New functionality

Feature Flag OFF
    ↓
Existing functionality
```

### Important Scenarios

* Flag enabled
* Flag disabled
* Flag changes dynamically
* Incorrect configuration
* Different environments
* Region-specific flag
* User-specific flag

Feature flags can significantly increase test combinations.

---

# 54. How do you analyze requirements for backward compatibility?

I ask:

> Will the new change affect existing users or existing functionality?

Examples:

* Existing API consumers
* Existing database records
* Existing mobile app versions
* Existing user sessions
* Existing integrations

Then I include backward-compatibility regression testing.

---

# 55. How do you explain Requirement Analysis in a real project?

### Senior-Level Sample Answer

> In my projects, I participate in backlog refinement and requirement review sessions before development starts. I analyze the user story and acceptance criteria from functional, negative, boundary, integration, data, and risk perspectives. I identify dependencies and region or platform-specific behavior where applicable. When requirements are unclear, I raise questions with the BA or Product Owner and document the decisions. After clarification, I derive test scenarios and test cases and maintain traceability between requirements and tests. When requirements change, I perform impact analysis and update both manual and automation coverage.

---

# 56. Real-Time Interview Scenario – New Feature With Incomplete Requirement

### Interviewer

You receive a story:

> "Customer should be able to add a vehicle using VIN."

What will you do?

### Strong Answer

> First, I would understand the complete business flow and acceptance criteria. I would clarify the VIN format, valid and invalid VIN behavior, duplicate VIN handling, unsupported vehicles, region-specific rules, authentication requirements, backend dependencies, database persistence, and error handling. I would also identify positive, negative, boundary, integration, and security scenarios. Once the requirements are clarified, I would create the test scenarios and maintain traceability to the story.

---

# 57. Real-Time Interview Scenario – Requirement Changes Mid-Sprint

### Interviewer

The Product Owner changes the acceptance criteria after development has started. What do you do?

### Answer

> I first understand exactly what changed and perform impact analysis. I identify affected test cases, automation scripts, APIs, test data, and regression areas. I then update the test coverage and communicate any additional testing effort or risks. After the development change is available, I execute focused testing followed by appropriate regression.

---

# 58. Real-Time Interview Scenario – No Acceptance Criteria

### Interviewer

The developer completed the story, but there is no acceptance criteria. What do you do?

### Answer

> I would not create expected results based purely on assumptions. I would review the available business requirement, design, and existing behavior and then discuss the expected behavior with the BA or Product Owner. Once clarified, I would document the decision and proceed with testing.

---

# 59. Real-Time Interview Scenario – Requirement vs Existing Behavior

### Interviewer

The requirement says one thing, but the existing application behaves differently. What do you do?

### Answer

> I would first determine whether the new requirement intentionally changes the existing behavior. I would review the requirement, acceptance criteria, previous functionality, and business decision. If the new behavior is confirmed, I would treat the old behavior as expected change and update regression coverage accordingly. If the requirement is unclear, I would seek clarification before raising a defect.

---

# 60. Real-Time Interview Scenario – Requirement Has High Business Risk

### Interviewer

You identify a payment-related requirement with incomplete error handling. What do you do?

### Answer

> I would immediately raise the gap because payment is a high-risk business area. I would clarify failure scenarios such as timeout, duplicate payment, declined payment, partial transaction, retry behavior, and rollback. I would prioritize these scenarios and communicate the release risk if the behavior remains undefined.

---

# 61. Real-Time Interview Scenario – Requirement Has 100% Happy Path

### Interviewer

The BA provides only positive scenarios. What will you do?

### Answer

> I would use the happy path as the starting point, but I would independently derive negative, boundary, validation, error-handling, security, integration, and recovery scenarios. I would also confirm critical business rules with the BA or Product Owner.

---

# 62. Real-Time Interview Scenario – Requirement Is Too Large

### Interviewer

A user story contains login, profile, vehicle, appointment, payment, and notification functionality. What do you recommend?

### Answer

> I would recommend splitting the story into smaller, independently testable units if possible. Large stories increase complexity, make estimation difficult, increase regression scope, and make it harder to identify the source of failures.

---

# 63. Real-Time Interview Scenario – Requirements Are Frequently Changing

### Interviewer

How do you maintain quality when requirements change frequently?

### Answer

> I use traceability and impact analysis. I keep test scenarios and automation modular so changes can be incorporated efficiently. I also maintain communication with the BA and Product Owner and identify regression areas affected by each change. In Agile, change is expected, so the focus is on managing change efficiently rather than trying to eliminate it.

---

# 64. Top Requirement Analysis Questions to Practice

## Beginner

1. What is requirement analysis?
2. Why is requirement analysis important?
3. What is a requirement?
4. What is an acceptance criterion?
5. What is an ambiguous requirement?
6. What is RTM?
7. What is requirement traceability?
8. What makes a requirement testable?
9. What is Definition of Ready?
10. What is Definition of Done?

## Intermediate

11. How do you identify missing requirements?
12. How do you derive negative scenarios?
13. How do you identify boundary conditions?
14. What do you do when requirements conflict?
15. How do you handle requirement changes?
16. How do you perform impact analysis?
17. How do you identify dependencies?
18. How do you prioritize requirements?
19. How do you identify requirement risks?
20. How do you handle incomplete acceptance criteria?

## Senior-Level

21. How do you challenge a requirement?
22. How do you handle verbally communicated requirements?
23. What if BA and developer have different interpretations?
24. What if the requirement conflicts with existing behavior?
25. How do you perform requirement risk analysis?
26. How do you determine regression scope?
27. How do you handle region-specific requirements?
28. How do you analyze integration requirements?
29. How do you handle third-party dependencies?
30. How do you maintain quality when requirements change frequently?

---

# 65. Quick Interview Cheat Sheet

```text
Requirement Received
        ↓
Understand Business Objective
        ↓
Review Acceptance Criteria
        ↓
Identify Ambiguities
        ↓
Identify Business Rules
        ↓
Identify Positive Scenarios
        ↓
Identify Negative Scenarios
        ↓
Identify Boundary Conditions
        ↓
Identify Dependencies
        ↓
Identify Data Requirements
        ↓
Identify Integration Points
        ↓
Identify Risks
        ↓
Clarify With BA / PO
        ↓
Document Decisions
        ↓
Create Test Scenarios
        ↓
Create Test Cases
        ↓
Maintain RTM
        ↓
Perform Testing
        ↓
Regression / Impact Analysis
```

---

# 66. Golden Rule for Senior QA Interviews

When answering requirement-analysis questions, avoid saying:

> "I will test what is written."

Instead say:

> **"I will understand what is written, challenge gaps and ambiguities, clarify expected behavior, identify risks and dependencies, derive positive and negative scenarios, and ensure complete test coverage."**

This demonstrates a **Senior QA mindset** rather than simply a test-execution mindset.

---

# 67. Key Points to Remember

* QA should participate from the requirement stage.
* Never silently assume unclear behavior.
* Ask questions early.
* Document clarifications.
* Analyze positive and negative scenarios.
* Always consider boundary conditions.
* Identify dependencies.
* Identify business risks.
* Consider region and platform differences.
* Consider API and database impacts.
* Maintain requirement traceability.
* Perform impact analysis when requirements change.
* Prioritize high-risk functionality.
* Focus on preventing defects, not just finding defects.
* Requirement analysis is one of the strongest indicators of senior QA maturity.

---

# End of Document

**Next Recommended Topic:**

`Manual-QA/Test-Scenario-Design-Real-Time-Scenario-Based-Interview-Questions.md`

This topic will cover how to convert requirements into strong test scenarios, including **positive, negative, boundary, integration, end-to-end, risk-based, and real-world interview scenarios**.
