# Database Testing – Scenario-Based Interview Questions

## 1. What is Database Testing?

Database Testing is the process of validating the data layer of an application to ensure that data is correctly stored, updated, retrieved, deleted, and maintained according to business requirements.

A QA engineer typically validates:

* Data accuracy
* Data integrity
* Data consistency
* CRUD operations
* Database constraints
* Stored procedures
* Triggers
* Views
* Data relationships
* Transactions
* Data migration
* Backend/API-to-database consistency

---

## 2. What are the main areas you validate during database testing?

I generally validate:

1. Data correctness
2. Data completeness
3. Data integrity
4. Primary and foreign key relationships
5. NULL handling
6. Duplicate records
7. Constraints
8. CRUD operations
9. Stored procedures
10. Triggers
11. Views
12. Transaction behavior
13. Data migration
14. API/UI-to-database consistency
15. Boundary and negative scenarios

---

## 3. Scenario: A user creates an account through the UI. How would you verify the database?

I would:

1. Create the user through the UI.
2. Capture the unique user/customer ID.
3. Query the corresponding database table.
4. Verify that the record was created.
5. Validate each important field.
6. Check default values.
7. Verify timestamps.
8. Verify generated IDs.
9. Check that sensitive data is stored according to requirements.
10. Verify relationships with related tables.

Example:

```sql
SELECT *
FROM customer
WHERE customer_id = 'C12345';
```

I would compare the database values against the expected values from the UI and requirements.

---

## 4. Scenario: UI shows customer information, but the database contains different information. What would you do?

I would first determine whether the UI is reading directly from the database or through an API/service layer.

I would:

1. Capture the UI response.
2. Capture the API response.
3. Query the database.
4. Compare UI → API → DB.
5. Check whether caching is involved.
6. Check whether there is eventual consistency.
7. Check timestamps and transaction status.
8. Review application logs.

I would then identify which layer introduced the discrepancy before logging the defect.

---

## 5. Scenario: A record is inserted successfully, but some columns contain NULL values unexpectedly. How would you investigate?

I would:

1. Identify which columns contain NULL.
2. Check the business requirement.
3. Determine whether NULL is allowed.
4. Check the database schema.
5. Review API payloads.
6. Review application logs.
7. Check default constraints.
8. Verify whether the application omitted the field.
9. Check whether a trigger or stored procedure modified the value.

If NULL is not expected, I would report it with the complete evidence.

---

## 6. Scenario: How do you verify data integrity between two related tables?

Suppose we have:

```text
Customer
---------
customer_id
customer_name

Order
---------
order_id
customer_id
order_amount
```

I would verify that every `Order.customer_id` corresponds to a valid `Customer.customer_id`.

Example:

```sql
SELECT o.order_id, o.customer_id
FROM orders o
LEFT JOIN customer c
    ON o.customer_id = c.customer_id
WHERE c.customer_id IS NULL;
```

If this query returns records, there may be orphaned order records.

---

## 7. Scenario: How do you test primary key constraints?

I would attempt to insert duplicate values into the primary-key column.

Example:

```sql
INSERT INTO customer(customer_id, customer_name)
VALUES ('C1001', 'John');
```

If `C1001` already exists, another insert using the same ID should fail.

I would verify that the database prevents duplicate primary-key values.

---

## 8. Scenario: How do you test foreign key constraints?

I would attempt to insert a child record with a nonexistent parent ID.

Example:

```sql
INSERT INTO orders(order_id, customer_id)
VALUES ('O1001', 'INVALID_CUSTOMER');
```

If the foreign key is correctly configured, the database should reject the operation.

I would also test update and delete behavior.

---

## 9. Scenario: How would you test CRUD operations?

CRUD means:

* **Create**
* **Read**
* **Update**
* **Delete**

For example, for a customer:

### Create

```sql
INSERT INTO customer(customer_id, customer_name)
VALUES ('C1001', 'John');
```

### Read

```sql
SELECT *
FROM customer
WHERE customer_id = 'C1001';
```

### Update

```sql
UPDATE customer
SET customer_name = 'John Smith'
WHERE customer_id = 'C1001';
```

### Delete

```sql
DELETE FROM customer
WHERE customer_id = 'C1001';
```

I would validate both successful and negative scenarios.

---

## 10. Scenario: UI says "Order Created Successfully," but no database record exists. What would you check?

I would investigate the complete transaction flow:

```text
UI
 ↓
API
 ↓
Service Layer
 ↓
Database
```

I would check:

* API response
* Request payload
* Application logs
* Database connection
* Transaction status
* Commit/rollback behavior
* Stored procedures
* Queue processing
* Asynchronous processing
* Database replication delay

I would not immediately conclude that the database is defective.

---

## 11. Scenario: The application creates duplicate records. How would you investigate?

I would check:

1. UI request.
2. API request.
3. Request IDs/correlation IDs.
4. Database records.
5. Unique constraints.
6. Retry mechanisms.
7. Message queues.
8. Stored procedures.
9. Application logs.
10. Whether the user clicked the submit button multiple times.

I would determine whether duplication originated from the UI, API, backend processing, or database layer.

---

## 12. Scenario: How do you test NULL and NOT NULL constraints?

I would identify mandatory fields and attempt to insert NULL values.

Example:

```sql
INSERT INTO customer(customer_id, customer_name)
VALUES ('C1002', NULL);
```

If `customer_name` is defined as `NOT NULL`, the database should reject the operation.

I would also verify that optional fields correctly accept NULL.

---

## 13. Scenario: How would you validate default values?

Suppose `status` should default to `ACTIVE`.

I would create a record without specifying the status:

```sql
INSERT INTO customer(customer_id, customer_name)
VALUES ('C1003', 'David');
```

Then:

```sql
SELECT status
FROM customer
WHERE customer_id = 'C1003';
```

Expected:

```text
ACTIVE
```

---

## 14. Scenario: How do you test database transactions?

I would verify:

* Commit
* Rollback
* Partial failure
* Atomicity
* Data consistency

For example, if an order creation updates multiple tables and the second operation fails, the first operation should also be rolled back if the business transaction requires atomicity.

---

## 15. Scenario: An order is created, but payment fails. What database validations would you perform?

I would verify:

* Order status
* Payment status
* Transaction record
* Inventory reservation
* Audit information
* Rollback behavior

For example:

```text
Order → PAYMENT_FAILED
Payment → FAILED
Inventory → RELEASED
```

The exact expected state would depend on the business requirement.

---

## 16. Scenario: How would you test a database migration?

I would compare the source and target databases.

I would validate:

* Record counts
* Column mappings
* Data types
* Mandatory fields
* NULL values
* Duplicate records
* Referential integrity
* Transformation rules
* Boundary values
* Special characters
* Date/time conversions

Example:

```sql
SELECT COUNT(*)
FROM source_customer;
```

Compare with:

```sql
SELECT COUNT(*)
FROM target_customer;
```

Count comparison alone is not sufficient; I would also validate actual data and transformation rules.

---

## 17. Scenario: Source database contains 1 million records. How would you validate migration efficiently?

I would avoid manually validating every record.

I would use:

* Record counts
* Aggregations
* Sampling
* Hash/checksum comparisons where appropriate
* Key-based comparisons
* Boundary records
* Random samples
* Duplicate checks
* NULL checks
* Referential-integrity queries

For example:

```sql
SELECT COUNT(*), SUM(order_amount)
FROM orders;
```

I could compare aggregate results between source and target.

---

## 18. Scenario: How would you identify duplicate records?

Example:

```sql
SELECT email, COUNT(*)
FROM customer
GROUP BY email
HAVING COUNT(*) > 1;
```

This identifies duplicate email values.

I would determine whether duplicates are actually defects or are permitted by the business rules.

---

## 19. Scenario: How would you test date and timestamp fields?

I would validate:

* Correct date
* Correct time
* Time zone
* Daylight-saving behavior where applicable
* Date format
* Boundary dates
* Future dates
* Past dates
* NULL behavior

For distributed systems, I would also verify whether timestamps are stored in UTC and converted correctly for display.

---

## 20. Scenario: How would you test database performance?

I would identify important queries and measure:

* Execution time
* Response time
* Query plans
* Index usage
* Large-data behavior
* Concurrent access
* Locking
* Deadlocks

I would compare results against the application's performance requirements.

---

## 21. Scenario: A query works with 100 records but becomes extremely slow with millions of records. What would you investigate?

I would investigate:

* Indexes
* Query execution plan
* Full table scans
* Joins
* Sorting
* Filtering
* Database statistics
* Missing indexes
* Large result sets
* Inefficient stored procedures

I would work with the DBA/development team rather than simply reporting "database is slow."

---

## 22. Scenario: How do you validate an index?

I would first understand why the index exists and which query should benefit from it.

Then I would:

1. Execute the query.
2. Review the execution plan.
3. Determine whether the index is being used.
4. Compare query performance.
5. Verify that indexes do not negatively affect required write operations.

---

## 23. Scenario: What is a stored procedure and how would you test it?

A stored procedure is a reusable set of SQL statements stored in the database.

I would test:

* Input parameters
* Output parameters
* Valid inputs
* Invalid inputs
* NULL values
* Boundary values
* Data modifications
* Error handling
* Transaction behavior
* Performance

Example:

```sql
EXEC GetCustomerDetails @CustomerId = 'C1001';
```

I would validate both the returned data and any database changes.

---

## 24. Scenario: How would you test a database trigger?

I would identify the event that activates the trigger.

For example:

```text
INSERT customer
      ↓
Trigger executes
      ↓
Audit table updated
```

I would perform the triggering operation and verify the expected side effect.

I would also test:

* INSERT
* UPDATE
* DELETE
* Multiple affected rows
* Failure scenarios
* Transaction rollback

---

## 25. Scenario: How would you test an audit table?

I would perform an operation such as updating a customer's address.

Then verify:

```text
Customer Table
       ↓
Updated record

Audit Table
       ↓
Old value
New value
User
Timestamp
Operation
```

I would verify that audit information is accurate and complete.

---

## 26. Scenario: API returns HTTP 200, but database update failed. Is this a defect?

Potentially yes.

I would first verify the API contract and expected transaction behavior.

If HTTP 200 indicates successful processing, but the required database update did not occur, that is likely a defect.

I would provide:

* API request
* API response
* Database query/result
* Timestamp
* Correlation/request ID
* Logs

---

## 27. Scenario: How do you validate API-to-database data?

I use the following flow:

```text
API Request
     ↓
API Response
     ↓
Database Query
     ↓
Compare
```

I validate:

* IDs
* Names
* Status
* Dates
* Amounts
* Flags
* Nested data
* Relationships

I also verify transformations where API and database representations differ.

---

## 28. Scenario: What SQL queries should a QA engineer know?

At minimum:

```sql
SELECT
INSERT
UPDATE
DELETE
WHERE
ORDER BY
GROUP BY
HAVING
DISTINCT
JOIN
LEFT JOIN
RIGHT JOIN
INNER JOIN
COUNT
SUM
AVG
MIN
MAX
LIKE
IN
BETWEEN
EXISTS
CASE
```

A senior QA engineer should also understand subqueries, CTEs, window functions, transactions, and execution plans at a practical level.

---

## 29. Scenario: What is the difference between INNER JOIN and LEFT JOIN?

### INNER JOIN

Returns matching records from both tables.

```sql
SELECT *
FROM customer c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

### LEFT JOIN

Returns all records from the left table and matching records from the right table.

```sql
SELECT *
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

LEFT JOIN is especially useful when looking for missing relationships.

---

## 30. Scenario: How would you find customers who have never placed an order?

```sql
SELECT c.customer_id, c.customer_name
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.customer_id IS NULL;
```

This is a common real-world QA database validation scenario.

---

## 31. Scenario: How would you validate deletion?

I would determine whether the requirement expects:

* Hard delete
* Soft delete

For hard delete:

```sql
SELECT *
FROM customer
WHERE customer_id = 'C1001';
```

After deletion, the record should no longer exist.

For soft delete, I would verify something such as:

```text
is_deleted = true
```

or:

```text
status = INACTIVE
```

I would also verify the impact on related records.

---

## 32. Scenario: A developer says "The database is correct," but you believe the data is wrong. How do you handle it?

I would avoid arguing based on assumptions.

I would provide reproducible evidence:

1. Requirement
2. Test data
3. API/UI action
4. SQL query
5. Actual result
6. Expected result
7. Logs if necessary

This makes the discussion objective and helps identify whether the issue is in the application, database, or requirement.

---

## 33. Scenario: What would you include in a database defect?

I would include:

* Environment
* Database/schema
* Table name
* Test data
* Steps to reproduce
* SQL query
* Expected result
* Actual result
* API/UI evidence
* Timestamp
* Correlation ID if available
* Logs
* Screenshots where useful

---

## 34. Scenario: How do you safely test UPDATE and DELETE queries?

I avoid executing destructive queries directly against shared environments unless authorized.

I would:

1. Confirm the environment.
2. Identify the exact records.
3. Run a SELECT first.
4. Verify the records.
5. Execute the operation only when authorized.
6. Validate the result.
7. Roll back where appropriate.

Example:

```sql
SELECT *
FROM customer
WHERE customer_id = 'C1001';
```

Only after confirming the target record would I proceed with an UPDATE or DELETE in an appropriate test environment.

---

## 35. Senior-Level Scenario: UI, API, and DB all show different values. How do you debug it?

I would create a data-flow comparison:

```text
UI
 ↓
API Request
 ↓
Backend Service
 ↓
Database
 ↓
API Response
 ↓
UI
```

Then compare the same business field at every layer.

For example:

```text
UI        → ACTIVE
API       → ACTIVE
Database  → INACTIVE
```

This immediately narrows the investigation to the backend/database interaction or caching/replication layer.

I would then check:

* API request
* API response
* Database state
* Logs
* Cache
* Transactions
* Replication
* Timing
* Stored procedures/triggers

---

# Real-Time DB Testing Interview Scenarios

## Scenario 1 – Customer Creation

**Interviewer:** A customer registers successfully, but the customer does not appear in the database. What do you do?

**Answer approach:**

I would verify the API response first, then check application logs and database transaction status. I would determine whether the operation was committed, rolled back, queued for asynchronous processing, or written to another database/schema.

---

## Scenario 2 – Incorrect Order Status

**Interviewer:** UI shows `Completed`, but database shows `Pending`. How do you investigate?

**Answer approach:**

I would compare:

```text
UI → API Response → Backend Logs → DB
```

I would check whether the UI has stale cached data, whether the API is reading from a replica, and whether the database transaction updating the status completed successfully.

---

## Scenario 3 – Missing Child Record

**Interviewer:** Customer exists, but the corresponding order record is missing.

**Answer approach:**

I would verify the order creation request, transaction boundaries, foreign-key relationships, backend logs, and whether the order operation was rolled back.

---

## Scenario 4 – Duplicate Customer

**Interviewer:** The same customer appears twice in the database.

**Answer approach:**

I would check whether duplicate creation requests were sent, whether the application has retry logic, whether unique constraints exist, and whether concurrent requests can create duplicate records.

---

## Scenario 5 – Data Migration

**Interviewer:** Your team migrated 10 million customer records. How would you test it?

**Answer approach:**

I would validate:

```text
Record counts
↓
Primary keys
↓
Mandatory fields
↓
Data mappings
↓
Transformation rules
↓
Duplicates
↓
NULL values
↓
Relationships
↓
Random samples
↓
Boundary records
```

I would automate large-volume comparisons rather than manually checking records.

---

# Important SQL Examples for QA Interviews

### Find duplicates

```sql
SELECT email, COUNT(*)
FROM customer
GROUP BY email
HAVING COUNT(*) > 1;
```

### Find NULL values

```sql
SELECT *
FROM customer
WHERE email IS NULL;
```

### Count records

```sql
SELECT COUNT(*)
FROM customer;
```

### Find records created today

```sql
SELECT *
FROM customer
WHERE CAST(created_date AS DATE) = CURRENT_DATE;
```

*The exact date syntax varies by database.*

### Find orphan records

```sql
SELECT o.*
FROM orders o
LEFT JOIN customer c
    ON o.customer_id = c.customer_id
WHERE c.customer_id IS NULL;
```

### Group records

```sql
SELECT status, COUNT(*)
FROM orders
GROUP BY status;
```

### Find records within a range

```sql
SELECT *
FROM orders
WHERE order_amount BETWEEN 100 AND 500;
```

---

# Key Database Testing Interview Topics to Prepare

* Database fundamentals
* SQL for QA
* CRUD testing
* Primary keys
* Foreign keys
* Constraints
* Joins
* Subqueries
* Aggregations
* NULL handling
* Duplicate detection
* Stored procedures
* Triggers
* Views
* Transactions
* Commit and rollback
* Data integrity
* Referential integrity
* Data migration
* ETL testing
* API-to-database validation
* UI-to-database validation
* Database performance
* Indexes
* Query execution plans
* Concurrency
* Deadlocks
* Audit tables
* Data reconciliation
* Production database validation
* Large-volume data testing
* Negative database testing
* Real-time troubleshooting
