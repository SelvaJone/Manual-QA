# Integration Testing – Scenario-Based Interview Questions

## 1. What is Integration Testing?

Integration testing verifies that two or more modules, services, components, or systems work correctly together after they have been individually tested.

### Example

In an e-commerce application:

```text
Web/Mobile UI
     ↓
Order Service
     ↓
Payment Service
     ↓
Inventory Service
     ↓
Database
```

Integration testing validates the communication and data flow between these components.

---

# 2. Scenario-Based Integration Testing Questions

## Q1. The login UI works correctly, and the authentication API works correctly independently. How would you test their integration?

### Answer

I would validate the complete interaction between the UI and authentication API.

I would verify:

* Username/password entered in the UI are sent correctly.
* Correct API endpoint is called.
* Request headers and payload are correct.
* Authentication token is returned.
* UI stores or uses the token correctly.
* User is redirected after successful authentication.
* Invalid credentials return the expected error.
* Expired or invalid tokens are handled correctly.
* API errors are displayed properly in the UI.

The key point is that individual component testing is not enough; I need to validate the contract and data flow between them.

---

## Q2. An order service sends payment information to a payment service. What integration scenarios would you test?

### Answer

I would test:

* Successful payment.
* Declined payment.
* Timeout.
* Invalid payment request.
* Duplicate payment request.
* Payment service unavailable.
* Incorrect response format.
* Partial response.
* Network failure.
* Authentication failure between services.
* Currency mismatch.
* Incorrect transaction amount.
* Retry behavior.
* Idempotency.

I would also verify that the order status is updated correctly based on the payment response.

---

## Q3. The payment succeeds, but the order remains in "Payment Pending." How would you investigate?

### Answer

I would trace the transaction across the integrated systems.

```text
UI
 ↓
Order API
 ↓
Payment API
 ↓
Payment Provider
 ↓
Payment Response
 ↓
Order Status Update
 ↓
Database
```

I would check:

1. Request sent by Order Service.
2. Payment provider response.
3. Transaction/correlation ID.
4. Response received by Order Service.
5. Order status update API.
6. Database record.
7. Application logs.
8. Message queue/event if asynchronous processing is involved.

I would determine whether the issue is:

* Payment provider response handling.
* Event/message processing.
* Database update.
* Timeout.
* Retry failure.
* Incorrect status mapping.

---

# 3. API-to-Database Integration

## Q4. An API creates a customer successfully. How would you validate the integration with the database?

### Answer

I would:

1. Send the API request.
2. Validate the API response.
3. Capture the generated customer ID.
4. Query the database using that ID.
5. Verify the stored values.
6. Verify default fields.
7. Verify timestamps.
8. Verify relationships with other tables.
9. Verify transaction behavior.

For example:

```text
POST /customers
        ↓
Customer Service
        ↓
Customer Database
```

I would verify that the API response and database state are consistent.

---

## Q5. The API response says a customer was created, but no record exists in the database. What could be wrong?

### Answer

Possible causes include:

* Transaction rollback.
* Asynchronous database processing.
* Database connection failure.
* Incorrect database configuration.
* Wrong database/environment.
* Cache returning stale information.
* Exception after API response was generated.
* Message queue failure.
* Data validation failure.
* Incorrect database routing.

I would use logs, correlation IDs, database queries, and message/event tracking to isolate the issue.

---

# 4. Service-to-Service Integration

## Q6. Service A calls Service B, but Service B returns HTTP 500. What would you test?

### Answer

I would verify:

* Request payload.
* HTTP method.
* URL.
* Headers.
* Authentication.
* Content type.
* Required fields.
* Service B availability.
* Error response.
* Timeout configuration.
* Retry mechanism.
* Circuit breaker behavior.
* Logging.
* Error propagation to Service A.

I would also verify whether Service A handles the 500 response gracefully.

---

## Q7. Service A expects JSON, but Service B changes a response field from `customerName` to `name`. What type of integration problem is this?

### Answer

This is a **contract compatibility issue**.

The services have an incompatible API contract.

I would verify:

* Response schema.
* Mandatory fields.
* Field names.
* Data types.
* Nullable fields.
* Backward compatibility.

Contract testing can help detect this problem before deployment.

---

# 5. Frontend-to-Backend Integration

## Q8. The backend API returns the correct data in Postman, but the UI displays incorrect data. What would you investigate?

### Answer

I would compare:

```text
API Response
     ↓
Frontend Mapping
     ↓
UI Display
```

I would check:

* Browser network request.
* Actual API response received by UI.
* JSON field mapping.
* Data transformation.
* Null handling.
* Date formatting.
* Currency formatting.
* Localization.
* Caching.
* UI state management.

If Postman works but the UI does not, the problem may be in the frontend integration layer rather than the backend service.

---

# 6. Database and API Integration

## Q9. An update API returns 200, but the old value is still returned by the GET API. How would you investigate?

### Answer

I would check:

1. PUT/PATCH request.
2. Update response.
3. Database record.
4. GET API query.
5. Cache.
6. Read replica synchronization.
7. Transaction commit.
8. Environment configuration.

A common cause in distributed systems is eventual consistency or stale caching.

---

# 7. Third-Party Integration

## Q10. An insurance application integrates with an external identity verification provider. How would you test it?

### Answer

I would test:

* Valid customer verification.
* Invalid customer.
* Provider timeout.
* Provider unavailable.
* Invalid response.
* Duplicate request.
* Authentication failure.
* Rate limiting.
* Incorrect customer data.
* Partial response.
* Retry behavior.
* Provider error codes.

I would also verify that sensitive information is not exposed in logs or error messages.

---

# 8. E-Commerce Integration

## Q11. An e-commerce application integrates Order, Payment, Inventory, and Shipping services. How would you test the integration?

### Answer

I would validate the complete business flow:

```text
Customer
   ↓
Order Service
   ↓
Payment Service
   ↓
Inventory Service
   ↓
Shipping Service
   ↓
Order Completion
```

Scenarios include:

* Successful order.
* Payment failure.
* Inventory unavailable.
* Shipping service failure.
* Payment success but inventory failure.
* Duplicate order.
* Payment timeout.
* Shipping address validation failure.
* Order cancellation.
* Refund.
* Partial fulfillment.

I would verify the final state across all participating services.

---

# 9. Insurance Application Integration

## Q12. An insurance application integrates with a customer profile service and a policy service. What would you validate?

### Answer

I would verify:

* Customer information retrieval.
* Policy information retrieval.
* Customer-policy relationship.
* Policy creation.
* Policy update.
* Policy cancellation.
* Invalid customer ID.
* Invalid policy ID.
* Service timeout.
* Authentication failure.
* Data consistency between systems.

For example:

```text
Customer Service
       ↓
Policy Service
       ↓
Claims Service
       ↓
Database
```

I would validate both successful and failure paths.

---

# 10. Connected Vehicle / Automotive Integration

## Q13. A mobile application retrieves vehicle information from a backend service. How would you test the integration?

### Answer

I would validate:

```text
Mobile App
    ↓
API Gateway
    ↓
Vehicle Service
    ↓
Vehicle Database
```

I would test:

* Valid VIN.
* Invalid VIN.
* VIN not found.
* Vehicle ownership validation.
* Vehicle region validation.
* Vehicle data retrieval.
* Subscription information.
* Authentication.
* Expired token.
* Backend timeout.
* Incorrect vehicle data.
* Database inconsistency.

I would also validate that the correct vehicle is displayed for the authenticated customer.

---

# 11. VIN-Based Integration Scenario

## Q14. A user adds a VIN to a connected vehicle application, but another vehicle's information is displayed. How would you investigate?

### Answer

I would trace the VIN through the complete system.

```text
Mobile App
   ↓
Add Vehicle API
   ↓
VIN Validation
   ↓
Vehicle Service
   ↓
Database
   ↓
Vehicle Response
   ↓
Mobile App
```

I would verify:

* VIN sent by the mobile application.
* VIN received by backend.
* VIN lookup query.
* Customer-VIN relationship.
* Database record.
* Cached vehicle information.
* API response.
* UI mapping.

I would also check logs using the correlation ID.

---

# 12. Asynchronous Integration

## Q15. An order service publishes an event to Kafka after an order is created. How would you test this integration?

### Answer

I would verify:

1. Order creation.
2. Event creation.
3. Topic.
4. Event payload.
5. Message key.
6. Consumer processing.
7. Database update.
8. Error handling.
9. Retry behavior.
10. Duplicate message handling.

Example:

```text
Order Service
     ↓
Kafka Topic
     ↓
Inventory Consumer
     ↓
Inventory Database
```

---

# 13. Message Queue Integration

## Q16. A consumer fails while processing a message. What scenarios would you test?

### Answer

I would test:

* Retry.
* Dead-letter queue.
* Message acknowledgment.
* Duplicate processing.
* Message ordering.
* Poison messages.
* Consumer restart.
* Temporary database failure.
* Permanent validation failure.
* Message reprocessing.

I would verify that the system does not lose messages.

---

# 14. Integration Failure

## Q17. Service B is unavailable while Service A is processing a customer request. What should you validate?

### Answer

I would validate:

* Timeout.
* Retry.
* Circuit breaker.
* Fallback response.
* Error message.
* Logging.
* Monitoring.
* Transaction rollback.
* User experience.

The system should fail gracefully instead of hanging indefinitely.

---

# 15. Authentication Integration

## Q18. Multiple microservices use OAuth/JWT authentication. What integration scenarios would you test?

### Answer

I would test:

* Valid token.
* Expired token.
* Invalid token.
* Missing token.
* Incorrect audience.
* Incorrect issuer.
* Insufficient permissions.
* Token refresh.
* Service-to-service authentication.
* Role-based authorization.

I would verify that each service correctly validates the token.

---

# 16. Integration Testing with Different Environments

## Q19. The integration works in QA but fails in staging. What would you investigate?

### Answer

I would compare:

* API URLs.
* Database configuration.
* Credentials.
* Environment variables.
* Certificates.
* Network access.
* Firewall rules.
* Third-party endpoints.
* Feature flags.
* Service versions.
* Database schema.
* Test data.
* Configuration files.

Environment configuration differences are a common cause of integration failures.

---

# 17. Version Compatibility

## Q20. Service A is upgraded to version 2, but Service B still uses version 1. How would you test compatibility?

### Answer

I would verify:

* API contract.
* Request compatibility.
* Response compatibility.
* Deprecated fields.
* New mandatory fields.
* Data types.
* Error codes.
* Backward compatibility.

I would test both:

```text
Service A v2 → Service B v1
Service A v2 → Service B v2
```

if both combinations are expected to be supported.

---

# 18. Integration Regression

## Q21. A developer changes the payment service. What integration regression tests would you execute?

### Answer

I would identify all dependent systems:

```text
Payment Service
 ├── Order Service
 ├── Refund Service
 ├── Invoice Service
 ├── Notification Service
 └── Reporting Service
```

I would run regression tests for:

* Payment success.
* Payment failure.
* Refund.
* Order status.
* Invoice generation.
* Notifications.
* Reporting.
* Retry behavior.
* Error handling.

The regression scope should be based on dependency and impact analysis.

---

# 19. Data Consistency

## Q22. Customer data exists in three different services. How would you test data consistency?

### Answer

I would identify the source of truth and compare the data across services.

For example:

```text
Customer Service
       ↓
Order Service
       ↓
Notification Service
```

I would validate:

* Customer ID.
* Name.
* Email.
* Address.
* Status.
* Update propagation.
* Event processing.
* Synchronization delay.

I would specifically test what happens when one service is temporarily unavailable.

---

# 20. Duplicate Requests

## Q23. The mobile application sends the same request twice because of a network retry. How would you test the system?

### Answer

I would test whether the backend supports **idempotency**.

For operations such as:

* Payment.
* Order creation.
* Appointment booking.
* Vehicle registration.

The system should prevent duplicate business transactions.

I would verify the use of:

* Idempotency keys.
* Transaction IDs.
* Unique constraints.
* Duplicate request detection.

---

# 21. Timeout Scenario

## Q24. An API depends on a third-party service that takes 60 seconds to respond. What would you test?

### Answer

I would validate:

* Connection timeout.
* Read timeout.
* Retry policy.
* Maximum retry count.
* Circuit breaker.
* User-facing error.
* Transaction rollback.
* Logging.
* Monitoring.

The application should not wait indefinitely.

---

# 22. Partial Integration Failure

## Q25. Payment succeeds but notification service fails. Should the order fail?

### Answer

Not necessarily.

I would understand the business requirement.

For example:

```text
Order → Payment → SUCCESS
              ↓
        Notification → FAILED
```

The order may still remain successful while the notification is retried asynchronously.

I would verify that:

* Order status remains correct.
* Notification is retried.
* Failed messages are not lost.
* Customer eventually receives notification.
* Monitoring reports the failure.

---

# 23. API Contract Testing

## Q26. What is contract testing and why is it useful?

### Answer

Contract testing verifies that the communication contract between two services remains compatible.

It validates things such as:

* Request structure.
* Response structure.
* Field names.
* Data types.
* Required fields.
* Error responses.

It helps detect integration-breaking changes before services are deployed together.

---

# 24. Integration Testing vs API Testing

## Q27. What is the difference between API testing and integration testing?

### Answer

**API testing** focuses primarily on validating an API's behavior.

**Integration testing** validates interactions between multiple components.

Example:

```text
API Testing:
POST /payment
       ↓
Payment Service

Integration Testing:
Order Service
       ↓
Payment Service
       ↓
Payment Provider
       ↓
Database
```

API testing can be part of integration testing, but integration testing has a broader scope.

---

# 25. Integration Testing vs End-to-End Testing

## Q28. What is the difference between integration testing and end-to-end testing?

### Answer

Integration testing focuses on communication between components.

End-to-end testing validates the complete business journey.

Example:

### Integration

```text
Order Service → Payment Service
```

### End-to-End

```text
Login
 ↓
Search Product
 ↓
Add to Cart
 ↓
Checkout
 ↓
Payment
 ↓
Order Confirmation
 ↓
Shipping
```

---

# 26. Testing Strategy

## Q29. How would you design an integration testing strategy for a microservices application?

### Answer

I would:

1. Identify service dependencies.
2. Identify critical business flows.
3. Define service contracts.
4. Prepare test data.
5. Identify synchronous and asynchronous integrations.
6. Validate positive scenarios.
7. Validate negative scenarios.
8. Test timeout and retry behavior.
9. Test authentication.
10. Test data consistency.
11. Automate stable integration tests.
12. Run integration tests in CI/CD.
13. Monitor failures and trends.

---

# 27. Integration Test Automation

## Q30. How would you automate integration testing?

### Answer

Depending on the architecture, I could use:

* Java + Rest Assured.
* Selenium/Playwright for UI-level integration validation.
* Postman/Newman.
* TestNG/JUnit.
* Database validation.
* Kafka test utilities.
* WireMock or similar service virtualization tools.
* Docker/Testcontainers.

Example:

```text
TestNG
   ↓
Rest Assured
   ↓
Order API
   ↓
Payment API
   ↓
Database
```

The automation should validate both the API response and resulting system state.

---

# 28. Mocking External Dependencies

## Q31. When would you mock an external service during integration testing?

### Answer

I would mock an external dependency when:

* The real service is unavailable.
* It is expensive to call.
* It has strict rate limits.
* Test data cannot be controlled.
* I need deterministic failures.
* I need to simulate rare scenarios.

For example:

```text
Application
    ↓
Mock Payment Provider
```

I could simulate:

* Success.
* Decline.
* Timeout.
* HTTP 500.
* Malformed response.

---

# 29. Real Service vs Mock

## Q32. Should integration testing always use real external services?

### Answer

No.

I would use real dependencies where practical and mocks/service virtualization where control or availability is a problem.

A balanced strategy could be:

```text
Unit Tests
   ↓
Component Tests
   ↓
Mock-based Integration Tests
   ↓
Real-Service Integration Tests
   ↓
End-to-End Tests
```

This provides good coverage without making the entire test suite dependent on external systems.

---

# 30. Defect Investigation

## Q33. How do you determine which service caused an integration failure?

### Answer

I would use:

* Correlation ID.
* Request ID.
* Application logs.
* API traces.
* DataDog or monitoring dashboards.
* Database records.
* Message queue logs.
* HTTP status codes.
* Response payloads.
* Distributed tracing.

I would reconstruct the transaction:

```text
Request
  ↓
Service A
  ↓
Service B
  ↓
Service C
  ↓
Database
```

Then identify the first point where the expected behavior diverged.

---

# 31. Production Integration Issue

## Q34. A production integration issue occurs but cannot be reproduced in QA. What would you do?

### Answer

I would compare:

* Configuration.
* Service versions.
* Database data.
* Feature flags.
* Traffic volume.
* Authentication.
* Network configuration.
* External provider behavior.
* Logs.
* Request payload.
* Correlation ID.

I would avoid making production changes without proper approval.

I would first gather evidence and identify the difference between environments.

---

# 32. Interview Scenario – Senior QA

## Q35. A developer says, "All APIs are working, so integration testing is not required." How would you respond?

### Answer

I would explain that API-level validation does not guarantee that services work correctly together.

For example:

```text
Order API → 200
Payment API → 200
Inventory API → 200
```

All three APIs can pass independently while the integrated flow still fails because:

* Incorrect data mapping.
* Wrong transaction ID.
* Incorrect status handling.
* Authentication mismatch.
* Event not published.
* Database update failure.
* Timing issue.

Integration testing validates the interaction and business data flow between those components.

---

# 33. Senior-Level Scenario

## Q36. An application has 20 microservices. How would you decide which integrations need the highest test coverage?

### Answer

I would prioritize based on:

* Business criticality.
* Customer impact.
* Transaction volume.
* Failure impact.
* Service dependency.
* Historical defects.
* Security sensitivity.
* Financial impact.
* Regulatory requirements.
* Frequency of changes.

For example, in an e-commerce system:

```text
Payment
Inventory
Order
Shipping
```

would normally receive higher integration coverage than a low-impact reporting service.

---

# 34. Integration Test Execution Order

## Q37. How would you structure integration tests?

### Answer

I would generally use:

```text
Component Validation
       ↓
Service-to-Service Tests
       ↓
Database Integration
       ↓
External Integration
       ↓
Critical Business Flow
       ↓
End-to-End Regression
```

This allows failures to be detected at the appropriate level before running expensive end-to-end tests.

---

# 35. Integration Testing in CI/CD

## Q38. Where would you execute integration tests in a CI/CD pipeline?

### Answer

A typical pipeline could be:

```text
Code Commit
    ↓
Build
    ↓
Unit Tests
    ↓
Component Tests
    ↓
Integration Tests
    ↓
API Tests
    ↓
UI Tests
    ↓
Deployment
    ↓
Smoke Tests
```

Critical integration tests should run early enough to prevent broken builds from progressing.

---

# 36. Database Transaction Scenario

## Q39. An order creation operation updates three database tables, but the third update fails. What should you test?

### Answer

I would verify transaction behavior.

If the operation is supposed to be atomic:

```text
Table A → SUCCESS
Table B → SUCCESS
Table C → FAILED
```

then the earlier updates should be rolled back.

I would verify:

* Commit.
* Rollback.
* Partial updates.
* Retry behavior.
* Error handling.
* Data consistency.

---

# 37. Concurrent Integration Requests

## Q40. Two users attempt to purchase the last available product simultaneously. What would you test?

### Answer

I would test concurrency and data consistency.

Expected behavior:

```text
User A → Product available → Purchase SUCCESS
User B → Product unavailable → Purchase FAILED
```

I would verify:

* Inventory locking.
* Transaction handling.
* Race conditions.
* Duplicate reservations.
* Database consistency.
* Order status.

---

# 38. Eventual Consistency

## Q41. An order is created immediately, but inventory updates a few seconds later. How would you test this?

### Answer

I would test eventual consistency.

I would verify:

* Event is published.
* Consumer receives the event.
* Inventory eventually reflects the change.
* Temporary intermediate states are acceptable.
* Failed events are retried.
* Duplicate events do not create incorrect inventory.
* Final state is consistent.

---

# 39. Integration Test Data

## Q42. What type of test data is important for integration testing?

### Answer

I would prepare:

* Valid data.
* Invalid data.
* Boundary data.
* Missing data.
* Duplicate data.
* Related records.
* Inactive records.
* Expired records.
* Large-volume data.
* Region-specific data.
* Role-specific data.

The test data should represent realistic business relationships across systems.

---

# 40. Final Senior-Level Question

## Q43. If you joined a new project tomorrow, how would you start integration testing?

### Answer

I would first understand the architecture.

```text
UI
 ↓
API Gateway
 ↓
Microservices
 ↓
Message Broker
 ↓
External Systems
 ↓
Databases
```

Then I would:

1. Identify all system dependencies.
2. Understand critical business flows.
3. Review API contracts.
4. Understand synchronous and asynchronous communication.
5. Identify databases and data ownership.
6. Review authentication mechanisms.
7. Identify external integrations.
8. Review existing automation.
9. Identify high-risk integration points.
10. Create integration test scenarios.
11. Prepare controlled test data.
12. Automate repeatable scenarios.
13. Add integration tests to CI/CD.
14. Monitor failures.
15. Perform risk-based regression.

My primary objective would be to verify **correct data, correct communication, correct sequencing, correct error handling, and correct final system state across integrated components.**

---

# Quick Interview Revision

## Key Areas to Remember

| Area                  | What to Validate                 |
| --------------------- | -------------------------------- |
| UI ↔ API              | Request, response, mapping       |
| API ↔ API             | Contract, payload, errors        |
| API ↔ DB              | Data persistence                 |
| Service ↔ Service     | Communication and business flow  |
| API ↔ External System | Timeout, retry, errors           |
| Kafka/Queue           | Events, retries, duplicates      |
| Authentication        | Token and authorization          |
| Transactions          | Commit and rollback              |
| Caching               | Stale data                       |
| Microservices         | Dependencies                     |
| Third Party           | Availability and failures        |
| CI/CD                 | Automated integration validation |
| Production            | Logs, tracing, configuration     |
| Data Consistency      | Cross-service synchronization    |
| Idempotency           | Duplicate requests               |
| Eventual Consistency  | Delayed updates                  |

## Important Senior QA Keywords

* Integration testing
* Contract testing
* API integration
* Service-to-service communication
* Microservices
* REST API
* Message queues
* Kafka
* Event-driven architecture
* Database integration
* Transaction management
* Rollback
* Idempotency
* Retry
* Timeout
* Circuit breaker
* Eventual consistency
* Data consistency
* Service virtualization
* Mocking
* Distributed tracing
* Correlation ID
* CI/CD
* Risk-based testing

## One-Line Interview Definition

> **Integration testing verifies that independently developed components, services, databases, APIs, and external systems communicate correctly and produce the expected business outcome when they work together.**
