# Manual QA – Real-Time / Scenario-Based Interview Questions

## 1. Introduction

Scenario-based questions are commonly asked in Senior QA, SDET, and Automation QA interviews.

Interviewers use these questions to evaluate:

- Real-world testing experience
- Analytical thinking
- Defect investigation skills
- Risk-based testing
- Communication
- Debugging ability
- Test planning
- Production issue handling
- Decision-making under pressure

A strong answer should usually follow this pattern:

1. Understand the requirement
2. Identify the risk
3. Define test scenarios
4. Execute tests
5. Analyze failures
6. Collect evidence
7. Report defects
8. Communicate impact
9. Retest the fix
10. Perform regression testing

---

# 2. Application Works in QA but Fails in Production

### Question

The application works correctly in QA but users report that it is failing in production. What would you do?

### Answer

I would first determine whether the issue is reproducible and identify the differences between QA and production.

I would check:

- Application version
- Configuration
- Database
- API endpoints
- Environment variables
- Feature flags
- Authentication
- Network configuration
- Third-party integrations
- Test data
- Logs and monitoring tools

I would collect:

- User ID
- Timestamp
- Request/response details
- Screenshots or videos
- Error messages
- Device/browser information
- Application version

Then I would check production logs and monitoring tools to identify the root cause.

If the issue is critical, I would immediately communicate the impact to the development and product teams instead of waiting for a complete investigation.

### Interview Tip

Do not simply say:

> "I will reproduce the issue."

A senior QA should explain **how they will investigate an environment-specific failure**.

---

# 3. Developer Says "It Works on My Machine"

### Question

A developer says the defect cannot be reproduced and says, "It works on my machine." How do you handle it?

### Answer

I would not argue with the developer.

I would provide clear evidence and compare the environments.

I would provide:

- Exact steps
- Test data
- Environment
- Application build/version
- Browser/device
- Expected result
- Actual result
- Screenshot/video
- Console logs
- Network logs
- API request/response if applicable

Then I would try to reproduce the issue together with the developer.

I would also compare:

```text
QA Environment
    ↓
Application Version
    ↓
Configuration
    ↓
Database/Test Data
    ↓
Browser/Device
    ↓
API/Service Dependencies
