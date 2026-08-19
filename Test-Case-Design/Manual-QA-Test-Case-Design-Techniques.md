# Manual QA – Test Case Design Techniques – Real-Time / Scenario-Based Interview Questions

## 1. What is Test Case Design?

Test Case Design is the process of identifying test conditions, test data, expected results, and test scenarios required to verify that an application behaves as expected.

A good test case should be:

- Clear
- Independent
- Reproducible
- Traceable to a requirement
- Easy to execute
- Easy to maintain
- Focused on one validation wherever practical

---

# 2. What are the major Test Case Design Techniques?

The most commonly used techniques are:

1. Equivalence Partitioning
2. Boundary Value Analysis
3. Decision Table Testing
4. State Transition Testing
5. Use Case Testing
6. Error Guessing
7. Pairwise Testing
8. Cause-and-Effect Graphing
9. Positive Testing
10. Negative Testing
11. Exploratory Testing

---

# 3. What is Equivalence Partitioning?

Equivalence Partitioning divides input data into groups where all values are expected to behave similarly.

Instead of testing every possible value, we select representative values from each partition.

### Example

Suppose an age field accepts:

```text
18 to 60
