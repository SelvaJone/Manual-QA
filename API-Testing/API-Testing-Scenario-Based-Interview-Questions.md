# API Testing – Scenario-Based Interview Questions

## 1. API Testing Fundamentals

### Q1. What is API testing, and why is it important?

**Answer:**

API testing validates the functionality, reliability, security, performance, and data correctness of application programming interfaces without depending on the UI.

API testing is important because:

* APIs are the primary communication layer between applications and services.
* API defects can affect multiple clients such as web, mobile, and third-party applications.
* API tests execute faster than UI tests.
* Business rules can be validated directly.
* Backend defects can be identified before UI testing.
* APIs can be tested independently of frontend availability.

**Real-time scenario:**

Suppose a mobile application displays a customer's vehicle information.

The UI may show:

```text
Vehicle
VIN: 1ABC123456789
Model: RAV4
Year: 2026
```

The QA engineer should validate the API response directly and verify:

* HTTP status code
* VIN
* Vehicle model
* Model year
* Required fields
* Data types
* Business rules
* Database consistency

---

# 2. HTTP Methods

### Q2. Explain GET, POST, PUT, PATCH, and DELETE with a real-time example.

**Answer:**

| Method | Purpose                          | Example                 |
| ------ | -------------------------------- | ----------------------- |
| GET    | Retrieve data                    | Get vehicle details     |
| POST   | Create new data                  | Create appointment      |
| PUT    | Replace/update complete resource | Replace vehicle profile |
| PATCH  | Partially update resource        | Update vehicle nickname |
| DELETE | Delete resource                  | Delete saved vehicle    |

Example:

```http
GET /vehicles/VIN123
```

```http
POST /appointments
```

```http
PUT /vehicles/VIN123
```

```http
PATCH /vehicles/VIN123
```

```http
DELETE /vehicles/VIN123
```

---

# 3. GET API Scenario

### Q3. A GET API returns HTTP 200, but the data displayed in the application is incorrect. What will you do?

**Answer:**

I would not consider the API passed simply because it returned `200`.

I would validate:

1. Request parameters.
2. Request headers.
3. Response status code.
4. Response body.
5. Required fields.
6. Data types.
7. Business rules.
8. Database values.
9. Transformation/mapping logic.
10. UI mapping.

For example:

```json
{
  "vin": "VIN123",
  "model": "RAV4",
  "year": 2026
}
```

If the UI displays `2025`, I would determine whether:

* API returned the wrong value.
* UI mapped the wrong field.
* Cached data is being displayed.
* Database contains stale data.

---

# 4. POST API Scenario

### Q4. You send a POST request and receive HTTP 201. How do you verify that the record was actually created?

**Answer:**

I would validate at multiple levels:

### API level

Verify:

* Status code = `201 Created`
* Response body
* Generated ID
* Request data
* Response headers

Example:

```json
{
  "id": "APP12345",
  "status": "CREATED"
}
```

### Database level

Query the database using the generated ID:

```sql
SELECT *
FROM appointments
WHERE appointment_id = 'APP12345';
```

Then verify:

* Record exists.
* Values match the request.
* Default values are correct.
* Audit fields are populated.
* Status is correct.

### Business level

Verify that the newly created appointment is visible through the corresponding GET API and UI.

---

# 5. PUT vs PATCH

### Q5. What is the difference between PUT and PATCH?

**Answer:**

`PUT` is generally used to replace the complete resource, while `PATCH` is used for partial modification.

Example:

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "phone": "1234567890"
}
```

A PUT request may require the complete object.

A PATCH request might update only:

```json
{
  "phone": "9999999999"
}
```

### Scenario

If the requirement says only the phone number should be changed, I would prefer PATCH if the API contract supports it.

I would also verify that unrelated fields remain unchanged.

---

# 6. HTTP Status Codes

### Q6. Which HTTP status codes do you commonly validate during API testing?

**Answer:**

### Success

```text
200 OK
201 Created
202 Accepted
204 No Content
```

### Client errors

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Unprocessable Entity
429 Too Many Requests
```

### Server errors

```text
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
504 Gateway Timeout
```

The expected status code depends on the API contract.

---

# 7. Status Code Mismatch

### Q7. An API returns 200 for invalid input. Is that a defect?

**Answer:**

Not necessarily based only on the status code.

I would first check the API specification.

If the contract says invalid input must return:

```text
400 Bad Request
```

but the API returns:

```text
200 OK
```

then it is a defect.

I would validate:

* Status code
* Error response
* Error code
* Error message
* API contract
* Business requirement

---

# 8. Negative Testing

### Q8. How would you perform negative testing for a POST API?

**Answer:**

I would test:

* Missing mandatory fields
* Null values
* Empty strings
* Invalid data types
* Invalid formats
* Invalid IDs
* Duplicate requests
* Invalid authentication
* Expired token
* Unauthorized user
* Invalid enum values
* Boundary values
* Very large payloads
* Malformed JSON
* Unsupported HTTP method

Example:

```json
{
  "appointmentDate": "",
  "dealerId": "INVALID",
  "vehicleId": null
}
```

Expected behavior should match the API specification.

---

# 9. Mandatory Field Validation

### Q9. The API requires VIN, but the request does not contain VIN. What should you validate?

**Answer:**

I would verify:

```text
Status Code = 400
```

and validate the error response:

```json
{
  "errorCode": "INVALID_REQUEST",
  "message": "VIN is required"
}
```

I would also verify that no incomplete database record was created.

---

# 10. JSON Validation

### Q10. What validations do you perform on a JSON response?

**Answer:**

I validate:

* JSON syntax
* Required fields
* Field names
* Data types
* Nullability
* Field values
* Nested objects
* Arrays
* Array size
* Duplicate elements where applicable
* Date formats
* Enum values
* Business rules

Example:

```json
{
  "customerId": 1001,
  "active": true,
  "vehicles": []
}
```

I would verify:

```text
customerId → number
active → boolean
vehicles → array
```

---

# 11. JSON Schema Validation

### Q11. Why is JSON schema validation useful?

**Answer:**

JSON schema validation verifies that the response structure follows the agreed API contract.

It can validate:

* Required properties
* Data types
* Nested structures
* Array structures
* Allowed values
* String formats
* Minimum/maximum values

This is especially useful when APIs are consumed by multiple applications.

---

# 12. Headers

### Q12. Which request and response headers do you commonly validate?

**Answer:**

Common request headers include:

```text
Content-Type
Accept
Authorization
Correlation-ID
User-Agent
API-Version
```

Common response headers include:

```text
Content-Type
Cache-Control
ETag
Location
Correlation-ID
```

Security-related headers may also need validation depending on the application.

---

# 13. Content-Type Scenario

### Q13. The API expects JSON, but the Content-Type is incorrect. What will you test?

**Answer:**

I would send requests with different content types:

```http
Content-Type: application/json
```

```http
Content-Type: text/plain
```

```http
Content-Type: application/xml
```

Then verify that unsupported content types are handled according to the API contract.

---

# 14. Authentication

### Q14. How do you test an authenticated API?

**Answer:**

I would test:

1. Valid token.
2. Missing token.
3. Invalid token.
4. Expired token.
5. Token belonging to another user.
6. Incorrect authentication scheme.
7. Revoked token.
8. Insufficient permissions.

For example:

```http
Authorization: Bearer <token>
```

Expected behavior must match the authentication specification.

---

# 15. Authentication vs Authorization

### Q15. What is the difference between authentication and authorization?

**Answer:**

**Authentication** verifies who the user is.

**Authorization** verifies what the user is allowed to access.

Example:

A customer successfully logs in.

Authentication:

```text
Is this user valid?
```

Authorization:

```text
Can this user access another customer's vehicle?
```

A security test should verify that changing an ID in the request does not expose another user's data.

---

# 16. Token Expiration Scenario

### Q16. What happens if your access token expires during API testing?

**Answer:**

I would verify:

* API returns the expected unauthorized response.
* No protected data is returned.
* Appropriate error code/message is returned.
* Client can refresh the token if refresh-token functionality exists.
* Retry behavior is correct.
* Expired tokens are not accepted.

---

# 17. API Chaining

### Q17. What is API chaining? Give a real-time example.

**Answer:**

API chaining means using data from one API response as input to another API request.

Example:

### Step 1

Create customer:

```http
POST /customers
```

Response:

```json
{
  "customerId": "C123"
}
```

### Step 2

Create vehicle:

```http
POST /customers/C123/vehicles
```

### Step 3

Create appointment:

```http
POST /customers/C123/appointments
```

The `customerId` from the first API is dynamically passed into subsequent requests.

---

# 18. API Chaining Failure

### Q18. The first API in a chain fails. Should you execute the second API?

**Answer:**

Normally, no.

If the second API depends on data generated by the first API, I would stop the dependent flow.

For example:

```text
Create Customer
       ↓
Create Vehicle
       ↓
Create Appointment
```

If customer creation fails, vehicle creation cannot be meaningfully validated using that newly created customer.

I would report the first failure and mark dependent tests appropriately.

---

# 19. API and Database Validation

### Q19. How do you validate API data against the database?

**Answer:**

I would:

1. Send API request.
2. Capture response.
3. Identify the relevant database record.
4. Execute SQL query.
5. Compare API response with database values.
6. Validate transformations/business rules.

Example:

```sql
SELECT vin, model, model_year
FROM vehicle
WHERE vin = 'VIN123';
```

Then compare:

```text
API VIN        = DB VIN
API Model      = DB Model
API Model Year = DB Model Year
```

I would account for expected transformations such as formatting or calculated fields.

---

# 20. API Response vs Database Mismatch

### Q20. API returns the correct data, but the database contains incorrect data. Is the API passed?

**Answer:**

The API may appear functionally correct from the response perspective, but the underlying data issue still needs investigation.

I would determine:

* Whether the API calculates/transforms the value.
* Whether it reads from cache.
* Whether another service is the source of truth.
* Whether the database value is expected to differ.

If the database is the source of truth and contains incorrect data, I would raise or route the defect appropriately.

---

# 21. API and UI Validation

### Q21. The API response is correct, but the UI displays incorrect information. How would you debug it?

**Answer:**

I would trace the complete flow:

```text
Database
   ↓
API
   ↓
Service/Mapping
   ↓
UI
```

If API is correct but UI is incorrect, I would inspect:

* UI mapping
* API response parsing
* Cached data
* Transformation logic
* Feature flags
* Browser/mobile logs
* Network requests

This helps isolate whether the defect belongs to backend or frontend.

---

# 22. Query Parameters

### Q22. How would you test an API that supports filtering and sorting?

**Answer:**

For:

```http
GET /vehicles?model=RAV4&year=2026
```

I would test:

* Valid model
* Invalid model
* Multiple filters
* Missing filter
* Empty filter
* Case sensitivity
* Special characters
* Boundary values
* Sorting ascending
* Sorting descending
* Pagination
* Combination of filters

I would also verify that the returned records actually satisfy all requested filters.

---

# 23. Pagination

### Q23. How do you test pagination?

**Answer:**

I would validate:

* Default page size
* Custom page size
* First page
* Middle page
* Last page
* Page beyond available records
* Zero page
* Negative page
* Very large page size
* Total count
* Duplicate records between pages
* Missing records
* Ordering consistency

Example:

```http
GET /vehicles?page=1&size=20
```

Then:

```http
GET /vehicles?page=2&size=20
```

I would ensure records are neither duplicated nor skipped unexpectedly.

---

# 24. Duplicate Data

### Q24. An API returns duplicate records. How would you investigate?

**Answer:**

I would check:

1. Request parameters.
2. Pagination.
3. Database query.
4. JOIN conditions.
5. API aggregation logic.
6. Caching.
7. Duplicate database records.
8. Service integration.
9. Sorting/pagination implementation.

I would reproduce with the same request and capture the response and correlation ID.

---

# 25. Sorting

### Q25. How would you test API sorting?

**Answer:**

For:

```http
GET /vehicles?sort=model&order=asc
```

I would verify that the response is actually sorted alphabetically.

I would test:

```text
Ascending
Descending
Invalid sort field
Missing sort field
Multiple sort fields
Case sensitivity
Null values
```

---

# 26. Date Validation

### Q26. How would you test an API that accepts appointment dates?

**Answer:**

I would test:

* Valid future date
* Current date
* Past date
* Leap date
* Invalid date
* Invalid format
* Null
* Empty value
* Time zone differences
* Daylight saving transitions where applicable
* Boundary booking dates

Example:

```json
{
  "appointmentDate": "2026-08-20"
}
```

I would verify both format and business rules.

---

# 27. Time Zone Scenario

### Q27. The API returns an appointment at 10:00 AM, but the UI shows 9:00 AM. How would you investigate?

**Answer:**

I would verify:

* API timestamp.
* Time zone included in the response.
* User/device time zone.
* Backend server time zone.
* Database timestamp.
* UTC conversion.
* UI conversion logic.

For example:

```text
Database → UTC
API → UTC
UI → Local Time
```

A one-hour difference could be related to time-zone or daylight-saving conversion.

---

# 28. Idempotency

### Q28. What is idempotency, and why is it important in API testing?

**Answer:**

An operation is idempotent when repeating the same operation produces the same intended result without creating unintended additional effects.

For example, sending the same update request multiple times should not unexpectedly create multiple records.

For payment or appointment APIs, idempotency is especially important.

I would test repeated requests using the same idempotency key when supported.

---

# 29. Duplicate POST Request

### Q29. A user clicks Submit twice and two appointments are created. How would you investigate?

**Answer:**

I would determine:

* Whether the UI sent two requests.
* Whether the backend supports idempotency.
* Whether duplicate requests are allowed.
* Whether a unique constraint exists.
* Whether the API processed both requests independently.
* Whether the client should disable the button after submission.

If duplicate creation violates the requirement, I would raise a defect with:

* Request payload
* Timestamps
* Response details
* Correlation IDs
* Database records
* Reproduction steps

---

# 30. Error Handling

### Q30. What makes a good API error response?

**Answer:**

A good error response should provide a consistent structure, for example:

```json
{
  "errorCode": "INVALID_VEHICLE",
  "message": "Vehicle could not be found",
  "correlationId": "abc-123"
}
```

I would verify:

* Correct HTTP status.
* Stable error code.
* Useful message.
* No sensitive information.
* Correlation/reference ID where applicable.
* Consistent structure.

---

# 31. Sensitive Data

### Q31. What sensitive information should not be exposed in API responses or errors?

**Answer:**

Depending on the application, APIs should avoid exposing:

* Passwords
* Access tokens
* Secret keys
* Internal database credentials
* Personally sensitive information not required by the client
* Internal stack traces
* SQL statements
* Internal server paths

I would specifically test error responses for accidental information leakage.

---

# 32. 500 Internal Server Error

### Q32. An API returns 500 for a valid request. What would you do?

**Answer:**

I would:

1. Reproduce the issue.
2. Capture request and response.
3. Check correlation ID.
4. Verify environment.
5. Check application/service logs if available.
6. Check dependent services.
7. Check database state.
8. Determine whether the issue is reproducible.
9. Raise a defect with evidence.

I would avoid concluding that the database is responsible without evidence.

---

# 33. 404 Scenario

### Q33. When should an API return 404?

**Answer:**

Typically when the requested resource does not exist, according to the API contract.

Example:

```http
GET /vehicles/INVALID-VIN
```

If the vehicle does not exist, the expected response may be:

```text
404 Not Found
```

I would validate both the status code and error body.

---

# 34. 400 vs 404

### Q34. What is the difference between 400 and 404?

**Answer:**

`400 Bad Request` generally means the request itself is invalid.

Example:

```text
Invalid JSON
Missing required field
Invalid parameter format
```

`404 Not Found` generally means the requested resource cannot be found.

Example:

```text
GET /vehicles/VIN-DOES-NOT-EXIST
```

The exact behavior should always follow the API contract.

---

# 35. 401 vs 403

### Q35. What is the difference between 401 and 403?

**Answer:**

Generally:

```text
401 → Authentication is missing/invalid.
403 → Authentication may be valid, but access is forbidden.
```

Example:

A valid customer token attempting to access an admin-only endpoint could result in `403`.

---

# 36. Contract Testing

### Q36. What is API contract testing?

**Answer:**

Contract testing verifies that the API provider and consumer agree on the API contract.

It validates things such as:

* Endpoint
* HTTP method
* Request structure
* Response structure
* Field names
* Data types
* Required fields
* Status codes

It is especially useful in microservice architectures.

---

# 37. Microservices Scenario

### Q37. An appointment API depends on customer, vehicle, dealer, and scheduling services. How would you test it?

**Answer:**

I would test:

```text
Appointment API
       |
       +---- Customer Service
       |
       +---- Vehicle Service
       |
       +---- Dealer Service
       |
       +---- Scheduling Service
```

I would validate:

* Successful integration.
* Invalid customer.
* Invalid vehicle.
* Invalid dealer.
* Unavailable time slot.
* Dependency timeout.
* Dependency 500.
* Dependency unavailable.
* Retry behavior.
* Error propagation.
* Data consistency.

---

# 38. Dependency Failure

### Q38. The appointment API returns 500 because the dealer service is unavailable. Is that acceptable?

**Answer:**

I would first check the API contract and resilience requirements.

I would verify whether the expected behavior is:

* 500
* 502
* 503
* Business-specific error
* Graceful fallback

The important point is that the response should be intentional and consistent with the defined contract.

---

# 39. Timeout Testing

### Q39. How would you test API timeout behavior?

**Answer:**

I would simulate or identify a slow dependency and verify:

* Timeout threshold.
* Response status.
* Error message.
* Retry behavior.
* Number of retries.
* No duplicate transactions.
* Proper logging.
* Recovery after dependency becomes available.

---

# 40. Retry Scenario

### Q40. An API automatically retries a failed request. What risk would you test?

**Answer:**

The biggest concern is duplicate processing.

For example:

```text
POST payment
   ↓
Timeout
   ↓
Retry
   ↓
Payment processed twice
```

I would verify idempotency and transaction handling.

---

# 41. Rate Limiting

### Q41. How do you test API rate limiting?

**Answer:**

I would send requests above the documented threshold and verify:

* Rate limit is enforced.
* Expected status code such as `429`.
* Appropriate error response.
* Retry information if provided.
* Requests resume after the configured interval.
* Legitimate traffic is not permanently blocked.

---

# 42. Performance

### Q42. What API performance metrics do you monitor?

**Answer:**

Common metrics include:

* Response time
* Average latency
* Median latency
* 90th percentile
* 95th percentile
* 99th percentile
* Throughput
* Error rate
* Concurrent users
* Requests per second
* Timeout rate

Example requirement:

```text
95% of API requests should respond within 2 seconds.
```

I would validate this under the agreed workload.

---

# 43. Large Payload

### Q43. How would you test an API with a large request payload?

**Answer:**

I would test:

* Minimum payload.
* Normal payload.
* Maximum supported payload.
* Payload exceeding maximum.
* Large arrays.
* Large strings.
* Nested objects.
* Special characters.

I would verify that oversized requests are rejected gracefully and do not cause service instability.

---

# 44. Special Characters

### Q44. How do you test special characters in API input?

**Answer:**

I would test:

```text
@
#
$
%
&
'
"
<
>
>
Unicode characters
Emoji
```

I would verify:

* Correct acceptance/rejection.
* Encoding.
* Data persistence.
* Response handling.
* No unexpected HTML/script execution.
* No SQL injection vulnerability.

---

# 45. SQL Injection

### Q45. How would you perform basic SQL injection testing on an API?

**Answer:**

I would use authorized security-test inputs in parameters and verify that the API safely handles them.

I would look for:

* Unexpected database errors.
* Data leakage.
* Unauthorized records.
* Query manipulation.
* Stack traces.

I would coordinate with the security team where penetration testing is required.

---

# 46. Regression Testing

### Q46. A backend developer changes an API response field. What regression testing would you perform?

**Answer:**

I would identify all consumers of the API:

```text
Web
Mobile
Other APIs
Reports
Third-party integrations
Automation
```

Then verify:

* Existing functionality.
* Response contract.
* Required fields.
* Data types.
* Backward compatibility.
* Error scenarios.
* Consumer behavior.

---

# 47. Backward Compatibility

### Q47. An API adds a new response field. Is that automatically a breaking change?

**Answer:**

Not necessarily.

Adding an optional response field is often backward compatible, but it depends on the consumers and contract.

I would verify:

* Existing consumers continue working.
* Required fields were not removed.
* Data types did not change.
* Existing behavior remains unchanged.

---

# 48. API Versioning

### Q48. Why is API versioning important?

**Answer:**

Versioning allows an API to evolve while supporting existing consumers.

Examples:

```text
/api/v1/vehicles
/api/v2/vehicles
```

I would verify that:

* Existing v1 consumers continue working.
* v2 behavior follows the new contract.
* Deprecated versions are handled according to the retirement plan.

---

# 49. Environment Validation

### Q49. An API works in QA but fails in staging. How would you investigate?

**Answer:**

I would compare:

* API URL.
* Configuration.
* Database.
* Test data.
* Authentication.
* Environment variables.
* Certificates.
* Service dependencies.
* Network connectivity.
* Feature flags.
* API versions.
* Deployment versions.

I would determine whether the issue is environment-specific or code-related.

---

# 50. Test Data Management

### Q50. How do you manage API test data?

**Answer:**

I prefer controlled, reusable test data.

Examples:

```text
Valid customer
Invalid customer
Active vehicle
Inactive vehicle
Valid dealer
Unavailable dealer
Expired appointment
Future appointment
Unauthorized user
```

I would avoid relying on production data unless explicitly authorized and appropriately protected.

---

# 51. Postman Scenario

### Q51. How would you create an API regression suite in Postman?

**Answer:**

I would organize collections by business functionality:

```text
Customer
Vehicle
Dealer
Appointment
Authentication
```

Each request would include assertions for:

* Status code
* Response time
* Response body
* Required fields
* Business rules

I would use environment variables for:

```text
baseUrl
token
customerId
vehicleId
appointmentId
```

For chained APIs, I would capture IDs from previous responses and store them in variables.

---

# 52. Newman Scenario

### Q52. How can Postman tests be integrated into CI/CD?

**Answer:**

A Postman collection can be executed using Newman from a CI/CD pipeline.

Typical flow:

```text
Code Deployment
      ↓
Environment Setup
      ↓
Newman API Tests
      ↓
Assertions
      ↓
Test Report
      ↓
Pass / Fail Pipeline
```

The pipeline can fail when critical API assertions fail.

---

# 53. Rest Assured Scenario

### Q53. How would you automate API testing using Rest Assured?

**Answer:**

A typical Rest Assured test validates:

```java
given()
    .header("Authorization", token)
    .contentType(ContentType.JSON)
    .body(requestBody)
.when()
    .post("/appointments")
.then()
    .statusCode(201)
    .body("status", equalTo("CREATED"));
```

In a real framework, I would separate:

* Request models
* Response models
* API clients
* Test classes
* Configuration
* Test data
* Utilities
* Reporting

---

# 54. API Automation Framework

### Q54. How would you design a scalable API automation framework?

**Answer:**

A maintainable framework could contain:

```text
src
 ├── main
 │    ├── java
 │    │    ├── clients
 │    │    ├── models
 │    │    ├── utilities
 │    │    └── configuration
 │
 └── test
      ├── java
      │    ├── tests
      │    └── assertions
      └── resources
           ├── testdata
           └── schemas
```

I would also include:

* Environment configuration
* Logging
* Reporting
* Authentication handling
* Request/response logging
* Reusable API clients
* JSON schema validation
* Database utilities
* CI/CD integration

---

# 55. API Chaining in Automation

### Q55. How would you dynamically pass an ID from one API to another?

**Answer:**

Example:

```java
String customerId =
    given()
        .body(customerRequest)
    .when()
        .post("/customers")
    .then()
        .statusCode(201)
        .extract()
        .path("customerId");
```

Then:

```java
given()
    .pathParam("customerId", customerId)
.when()
    .get("/customers/{customerId}")
.then()
    .statusCode(200);
```

This avoids hardcoding dynamic IDs.

---

# 56. Authentication Reuse

### Q56. How would you avoid generating an authentication token for every API test?

**Answer:**

Depending on the application, I could:

* Generate a token once per test suite.
* Generate it per test class.
* Cache it until expiration.
* Refresh it when required.

I would avoid unnecessary authentication calls while ensuring tests remain independent enough for reliable execution.

---

# 57. Correlation ID

### Q57. Why is a correlation ID useful during API testing?

**Answer:**

A correlation ID helps trace one request across multiple services.

Example:

```text
Mobile App
    ↓
API Gateway
    ↓
Appointment Service
    ↓
Dealer Service
    ↓
Database
```

If the request contains:

```text
Correlation-ID: ABC123
```

logs across these services can potentially be searched using the same ID.

This is extremely useful when investigating production-like failures.

---

# 58. Production API Defect

### Q58. A production API intermittently returns 500. How would you investigate?

**Answer:**

I would collect:

* Endpoint
* HTTP method
* Request parameters
* Timestamp
* User/account context where appropriate
* Response
* Correlation ID
* Frequency
* Environment
* Application logs
* Dependency logs
* Database status
* Recent deployments

Then determine whether the issue is:

* Data-specific
* Load-related
* Dependency-related
* Configuration-related
* Code-related
* Intermittent infrastructure failure

---

# 59. Flaky API Test

### Q59. Your API automation test passes locally but fails intermittently in CI. What would you check?

**Answer:**

I would investigate:

* Test data conflicts.
* Parallel execution.
* Environment instability.
* Timing issues.
* Race conditions.
* Token expiration.
* Dependency availability.
* Database cleanup.
* Test ordering.
* Network latency.
* Shared variables.

I would reproduce the issue and avoid simply adding arbitrary waits.

---

# 60. API Test Dependency

### Q60. How do you decide which API tests should be automated first?

**Answer:**

I prioritize:

1. Business-critical APIs.
2. High-risk functionality.
3. Frequently executed regression tests.
4. Stable API contracts.
5. High-volume APIs.
6. APIs with complex business logic.
7. APIs difficult to validate through UI alone.

For example, customer creation, authentication, vehicle onboarding, payment, and appointment APIs may receive high priority depending on the product.

---

# 61. Real-Time Scenario – API Returns Wrong Dealer

### Q61. The user searches for a dealer, but the API returns a dealer from another region. How would you investigate?

**Answer:**

I would validate:

```text
User Region
    ↓
Request Parameters
    ↓
API Response
    ↓
Database
    ↓
UI
```

I would check:

* Region parameter.
* Dealer ID.
* Dealer status.
* Latitude/longitude if applicable.
* Database region mapping.
* API filtering logic.
* Cache.
* Default region behavior.

If the API itself returns the wrong region, I would raise a backend defect.

---

# 62. Real-Time Scenario – API and Mobile App

### Q62. The mobile app shows "No Dealers Found", but Postman returns dealers. What would you check?

**Answer:**

I would compare the mobile request with the Postman request.

Specifically:

* URL
* Query parameters
* Headers
* Authentication
* Region
* Language
* Request body
* API version
* Environment
* Device/network conditions

If the requests differ, I would identify the incorrect parameter or header.

If requests are identical, I would investigate mobile response parsing or UI logic.

---

# 63. Real-Time Scenario – Language

### Q63. The API returns English text even when the user selected Spanish. What would you validate?

**Answer:**

I would inspect the localization mechanism.

For example:

```http
Accept-Language: es
```

or an application-specific language parameter.

I would validate:

* Correct language request.
* Region.
* API response.
* Translation keys.
* Missing translations.
* Fallback behavior.

If the API returns English despite a valid Spanish request, it may be an API/localization defect.

---

# 64. Real-Time Scenario – Mobile Timeout

### Q64. The mobile application takes more than 30 seconds to load a page. How would you determine whether the API is responsible?

**Answer:**

I would capture the network request and measure:

```text
DNS
Connection
Request
Server processing
Response
```

Then compare the API response time directly.

If:

```text
API response = 2 seconds
UI loading = 30 seconds
```

the issue is probably not API server response time.

If:

```text
API response = 28 seconds
```

then I would investigate backend performance, database queries, downstream services, or infrastructure.

---

# 65. Real-Time Scenario – Data Not Saved

### Q65. POST API returns success, but a subsequent GET does not return the newly created record. What would you check?

**Answer:**

I would check:

1. POST response.
2. Generated ID.
3. Database record.
4. GET request parameters.
5. Read/write database separation.
6. Replication delay.
7. Cache.
8. Event/message processing.
9. Transaction commit.
10. Service consistency.

This could be an eventual-consistency issue rather than a simple API failure.

---

# 66. Real-Time Scenario – Partial Failure

### Q66. An API performs three database operations and the third operation fails. What should you verify?

**Answer:**

I would verify transaction behavior.

If the operation is expected to be atomic:

```text
Operation 1 → Success
Operation 2 → Success
Operation 3 → Failure
```

then the previous operations should be rolled back.

I would verify the database state after failure.

---

# 67. Transaction Validation

### Q67. How do you test transaction rollback through an API?

**Answer:**

I would:

1. Capture database state.
2. Execute API request that triggers multiple updates.
3. Force or reproduce a failure.
4. Query the database.
5. Verify whether partial data remains.

Expected behavior depends on the transaction requirements.

---

# 68. API Data Consistency

### Q68. What is data consistency testing in API testing?

**Answer:**

It verifies that the same business data remains consistent across systems.

Example:

```text
API
 ↓
Database
 ↓
Event Service
 ↓
Reporting System
```

If an appointment is created through the API, I may verify that the appointment status is correctly reflected across all required systems.

---

# 69. API Security Testing

### Q69. What security validations do you perform as a QA engineer?

**Answer:**

Depending on the scope and authorization, I validate:

* Authentication.
* Authorization.
* Access control.
* Sensitive data exposure.
* Token handling.
* Input validation.
* Error leakage.
* Session/token expiration.
* Rate limiting.
* CORS behavior where applicable.
* Injection risks.

Formal penetration testing should be performed by authorized security specialists when required.

---

# 70. API Test Pyramid

### Q70. Where does API testing fit in the test pyramid?

**Answer:**

API tests generally sit above unit tests and below UI tests.

```text
        UI Tests
       /        \
     API Tests
    /            \
 Unit Tests
```

API tests provide a good balance between:

* Execution speed
* Business coverage
* Reliability
* Maintenance

For many backend workflows, API tests can provide broader and faster regression coverage than UI-only tests.

---

# 71. Smoke Testing for APIs

### Q71. What would you include in an API smoke suite?

**Answer:**

I would include critical health/business flows such as:

```text
Authentication
Customer retrieval
Vehicle retrieval
Critical create operation
Critical update operation
Critical search operation
```

The objective is to quickly determine whether the environment and major API functionality are operational.

---

# 72. API Regression Suite

### Q72. What should an API regression suite contain?

**Answer:**

It should cover:

* Positive scenarios.
* Negative scenarios.
* Boundary conditions.
* Authentication.
* Authorization.
* CRUD operations.
* Business rules.
* Error handling.
* Integration scenarios.
* Database validation.
* Contract validation.
* Critical performance checks where appropriate.

---

# 73. API Test Prioritization

### Q73. If you have 1,000 API tests but only 30 minutes before release, how would you prioritize?

**Answer:**

I would use risk-based testing.

Priority:

```text
P0 → Critical business APIs
P1 → High-risk functionality
P2 → Important regression scenarios
P3 → Lower-risk edge cases
```

I would execute:

1. Smoke tests.
2. Critical business flows.
3. Recently changed APIs.
4. High-defect areas.
5. Integration tests.
6. Broader regression if time permits.

---

# 74. API Defect Report

### Q74. What information should be included when reporting an API defect?

**Answer:**

I would include:

```text
Title
Environment
Endpoint
HTTP Method
Request URL
Headers
Request Body
Expected Result
Actual Result
Status Code
Response Body
Timestamp
Correlation ID
Database evidence
Logs
Reproduction Steps
Severity
Priority
```

Sensitive credentials or tokens should never be exposed in defect reports.

---

# 75. Severity vs Priority

### Q75. An API returns incorrect customer information. How would you determine severity?

**Answer:**

I would consider:

* Business impact.
* Number of users affected.
* Data sensitivity.
* Security implications.
* Availability of workaround.
* Frequency.
* Production impact.

Incorrect customer data could be high severity, particularly if it exposes another customer's information.

---

# 76. API Test Coverage

### Q76. How do you measure API test coverage?

**Answer:**

I can measure coverage across:

* Endpoints.
* HTTP methods.
* Business scenarios.
* Positive/negative cases.
* Status codes.
* Error conditions.
* Authentication scenarios.
* Authorization scenarios.
* Data combinations.
* Boundary values.
* Integration paths.

Example:

```text
Total endpoints = 100
Automated endpoints = 85

Automation endpoint coverage = 85%
```

However, endpoint percentage alone does not represent meaningful business coverage.

---

# 77. API Testing in Agile

### Q77. When do you start API testing in a sprint?

**Answer:**

I prefer to start as soon as the API contract or implementation is sufficiently available.

The workflow can be:

```text
Requirement
   ↓
API Contract Review
   ↓
Test Scenario Design
   ↓
API Development
   ↓
API Testing
   ↓
UI Integration
   ↓
End-to-End Testing
```

This allows backend defects to be identified before UI testing begins.

---

# 78. API Contract Review

### Q78. What do you review before testing a new API?

**Answer:**

I review:

* Endpoint.
* HTTP method.
* Request schema.
* Response schema.
* Authentication.
* Headers.
* Parameters.
* Status codes.
* Error responses.
* Business rules.
* Data constraints.
* Pagination.
* Sorting.
* Versioning.
* Dependencies.

I also identify ambiguous requirements before test execution.

---

# 79. API Requirement Ambiguity

### Q79. The requirement says "API should return customer details" but does not define the expected fields. What would you do?

**Answer:**

I would clarify the contract before finalizing tests.

I would ask:

* Which fields?
* Which fields are mandatory?
* What happens when the customer does not exist?
* What authentication is required?
* What status codes are expected?
* What data format is expected?
* Are there privacy restrictions?

I would not make assumptions for critical business behavior.

---

# 80. Final Senior-Level Scenario

### Q80. A critical API works correctly in QA but intermittently fails in production. As a senior QA engineer, how would you handle it?

**Answer:**

I would approach it systematically.

### Step 1 – Confirm the issue

Reproduce using the same endpoint, request, and conditions where possible.

### Step 2 – Collect evidence

Capture:

* Timestamp
* Endpoint
* Request
* Response
* Status code
* Correlation ID
* Environment
* User context where appropriate

### Step 3 – Check dependencies

Investigate:

```text
API Gateway
   ↓
Service
   ↓
Database
   ↓
External Services
```

### Step 4 – Analyze patterns

Determine whether failures correlate with:

* Specific users.
* Specific regions.
* Specific data.
* High traffic.
* Specific API parameters.
* Specific servers.
* Recent deployments.

### Step 5 – Check logs and monitoring

Use available application and infrastructure monitoring to trace the request.

### Step 6 – Compare environments

Compare:

```text
QA
Staging
Production
```

for configuration, data, versions, dependencies, and infrastructure.

### Step 7 – Assess business impact

Determine:

* Number of users affected.
* Frequency.
* Business-criticality.
* Workaround availability.

### Step 8 – Collaborate

Work with:

* Developers
* DevOps
* Backend engineers
* Database team
* Product owner
* Security team when required

### Step 9 – Validate the fix

After the fix:

* Reproduce the original failure scenario.
* Run API regression.
* Run integration tests.
* Validate database consistency.
* Validate dependent applications.
* Monitor production behavior.

### Senior QA mindset

A senior QA engineer should not simply say:

> "The API returned 500, so I created a defect."

Instead, the goal is to **identify where the failure occurs, collect evidence, determine business impact, isolate the root cause, and verify the complete fix without introducing regression.**

---

# Quick API Testing Interview Checklist

Before an API interview, be comfortable explaining:

* [ ] GET
* [ ] POST
* [ ] PUT
* [ ] PATCH
* [ ] DELETE
* [ ] HTTP status codes
* [ ] Headers
* [ ] Query parameters
* [ ] Path parameters
* [ ] Request body
* [ ] JSON validation
* [ ] JSON schema
* [ ] Authentication
* [ ] Authorization
* [ ] OAuth/JWT concepts
* [ ] Negative testing
* [ ] Boundary testing
* [ ] Error handling
* [ ] API chaining
* [ ] Database validation
* [ ] API/UI validation
* [ ] API contract testing
* [ ] Microservice testing
* [ ] Dependency failures
* [ ] Timeout testing
* [ ] Retry behavior
* [ ] Idempotency
* [ ] Rate limiting
* [ ] Pagination
* [ ] Sorting
* [ ] Filtering
* [ ] Date/time validation
* [ ] Data consistency
* [ ] Security testing
* [ ] Performance testing
* [ ] Postman
* [ ] Newman
* [ ] Rest Assured
* [ ] API automation framework
* [ ] CI/CD integration
* [ ] Production troubleshooting
* [ ] API defect reporting
* [ ] Risk-based API testing
* [ ] Regression strategy

# Senior QA Interview Closing Answer

### Q81. What is your overall approach to API testing?

**Answer:**

My approach starts with understanding the API contract and business requirement. I validate the request, response, status codes, headers, authentication, authorization, business rules, negative scenarios, boundary conditions, and data consistency.

For critical APIs, I also validate the database and downstream integrations.

For automation, I use reusable API clients, parameterized test data, response assertions, schema validation, API chaining, reporting, and CI/CD integration.

When an API fails, I focus on isolating the failure across the complete flow:

```text
Client
  ↓
API Gateway
  ↓
Service
  ↓
Database
  ↓
Downstream Services
```

I collect request/response details, logs, correlation IDs, database evidence, and environment information before reporting the defect.

The main goal is not just to verify that an API returns `200`. The goal is to ensure that the API produces the **correct business outcome, correct data, correct security behavior, correct error handling, and reliable integration behavior** under both normal and exceptional conditions.
