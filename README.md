# REST API Testing Portfolio — Postman

## Project Overview

This project demonstrates my practical skills in **REST API testing using Postman and JavaScript**. I created an independent API testing project using [JSONPlaceholder](https://jsonplaceholder.typicode.com/), a public REST API for testing and development.

The project covers functional testing, response validation, data-type verification, negative testing, POST requests, and basic response-time checks.

**Tools:** Postman, JavaScript, REST API
**API Under Test:** JSONPlaceholder
**Project Type:** Independent QA Portfolio Project

## Testing Objectives

* Validate HTTP status codes and API responses.
* Verify JSON response structures and required fields.
* Validate data types and response content.
* Test resource retrieval using IDs and query parameters.
* Verify API behavior when resources do not exist.
* Test POST requests and validate returned data.
* Investigate unsupported routes and incomplete requests.
* Measure response times against a defined threshold.
* Create reusable test scripts and document test results.

## Test Scenarios

| Test ID | Scenario                                  | Method | Endpoint                 |
| ------- | ----------------------------------------- | ------ | ------------------------ |
| API-001 | Retrieve all posts                        | GET    | `/posts`                 |
| API-002 | Retrieve a post by ID                     | GET    | `/posts/1`               |
| API-003 | Retrieve a nonexistent post               | GET    | `/posts/9999`            |
| API-004 | Create a new post                         | POST   | `/posts`                 |
| API-005 | Retrieve posts for user 1                 | GET    | `/posts?userId=1`        |
| API-006 | Retrieve comments for post 1              | GET    | `/posts/1/comments`      |
| API-007 | Request an unsupported route              | GET    | `/unsupported-route-123` |
| API-008 | Submit a POST request with missing fields | POST   | `/posts`                 |
| API-009 | Validate JSON response structure          | GET    | `/posts/1`               |
| API-010 | Check API response time                   | GET    | `/posts`                 |

## Detailed Test Coverage

### API-001: Retrieve All Posts

**Request:** `GET /posts`

**Validations:**

* Verify the response status is `200 OK`.
* Confirm the response is a JSON array.
* Verify that each post contains `userId`, `id`, `title`, and `body`.
* Validate that IDs and user IDs are numeric.

**Objective:** Verify that the API successfully returns a collection of posts with the expected structure.

### API-002: Retrieve a Post by ID

**Request:** `GET /posts/1`

**Validations:**

* Verify the response status is `200 OK`.
* Confirm the response is a JSON object.
* Validate the presence of `userId`, `id`, `title`, and `body`.
* Verify the data types of the required fields.
* Confirm that the returned post ID matches the requested ID.

**Objective:** Ensure that individual resource retrieval returns the correct post and expected data structure.

### API-003: Retrieve a Nonexistent Post

**Request:** `GET /posts/9999`

**Validations:**

* Record the actual HTTP status code.
* Inspect the response body.
* Compare the observed behavior with the API's documented requirements.

**Objective:** Investigate how the API handles requests for resources that do not exist.

**Note:** JSONPlaceholder may return an empty JSON object with a successful status for a nonexistent post. Record the actual response rather than assuming the API must return `404 Not Found`.

### API-004: Create a New Post

**Request:** `POST /posts`

**Example request body:**

```json
{
  "title": "API testing portfolio",
  "body": "Testing POST requests with Postman",
  "userId": 1
}
```

**Validations:**

* Verify the response status is `201 Created`.
* Confirm that the response contains the submitted title, body, and user ID.
* Verify that a generated post ID is returned.
* Validate the data types of the response fields.

**Objective:** Verify the API's simulated resource-creation behavior and validate the returned data.

**Note:** JSONPlaceholder simulates POST operations. A successful response does not mean that the new post has been permanently stored.

### API-005: Retrieve Posts for User 1

**Request:** `GET /posts?userId=1`

**Validations:**

* Verify the response status is `200 OK`.
* Confirm the response is an array.
* Verify that every returned post has `userId = 1`.
* Confirm that each post contains the required fields.

**Objective:** Validate query-parameter filtering and ensure the returned records match the requested user.

### API-006: Retrieve Comments for Post 1

**Request:** `GET /posts/1/comments`

**Validations:**

* Verify the response status is `200 OK`.
* Confirm the response is a non-empty array.
* Verify that every comment contains `postId`, `id`, `name`, `email`, and `body`.
* Validate the expected data types.
* Confirm that each comment belongs to post 1.

**Objective:** Validate the structure and relationships of comments associated with a particular post.

### API-007: Request an Unsupported Route

**Request:** `GET /unsupported-route-123`

**Validations:**

* Capture the actual HTTP status code.
* Inspect the response body.
* Record whether the response is appropriate for an unsupported route.
* Compare the observed behavior with the documented API contract.

**Objective:** Investigate how the API responds to unsupported endpoints.

**Note:** Do not assume that the response must be `404 Not Found`. Record the actual result and evaluate it against the expected behavior.

### API-008: Submit a POST Request with Missing Fields

**Request:** `POST /posts`

**Example request body:**

```json
{
  "title": "API testing portfolio"
}
```

The request intentionally omits the `body` and `userId` fields.

**Validations:**

* Record the actual HTTP status code.
* Inspect the response body.
* Determine whether the API accepts the incomplete request.
* Record the fields returned by the API.
* Compare the observed behavior with expected validation requirements.

**Objective:** Investigate how the API handles incomplete request data.

**Note:** JSONPlaceholder may accept this request because it is a demonstration API. Acceptance should not automatically be considered correct behavior for a production API.

### API-009: Validate JSON Response Structure

**Request:** `GET /posts/1`

**Validations:**

* Verify the response status is `200 OK`.
* Confirm the response content type indicates JSON.
* Verify the required fields are present.
* Validate data types.
* Confirm the returned post ID matches the requested ID.
* Ensure the title and body are not empty.

**Objective:** Validate response structure, data consistency, and required field constraints.

### API-010: Check API Response Time

**Request:** `GET /posts`

**Validations:**

* Measure the response time.
* Verify the response status is `200 OK`.
* Compare the response time against a configurable threshold of 1,000 milliseconds.
* Record the actual response time.

**Objective:** Perform a basic response-time check against a defined target.

**Note:** The 1,000 ms threshold is an example portfolio target, not a universal performance standard. A single request does not constitute a load test or establish performance under concurrent traffic.

## Testing Techniques Demonstrated

### Functional Testing

* Successful resource retrieval
* Query-parameter filtering
* Resource creation
* Resource relationship validation

### Negative Testing

* Requests for nonexistent resources
* Unsupported routes
* Requests with missing fields

### Data Validation

* Required field verification
* JSON structure validation
* Data-type assertions
* Response consistency checks

### Basic Performance Testing

* Response-time measurement
* Threshold-based assertions
* Recording actual performance observations

## Project Structure

```text
REST-API-Testing-Portfolio/
├── postman/
│   └── API_Testing_Postman_Collection.json
├── reports/
│   ├── API_Test_Cases_and_Results.md
│   ├── API_Test_Scenarios.csv
│   └── Defect_Report_Template.md
├── screenshots/
└── README.md
```

## Tools and Technologies

| Tool / Technology | Purpose                                    |
| ----------------- | ------------------------------------------ |
| Postman           | API request execution and test automation  |
| JavaScript        | Writing reusable Postman test scripts      |
| REST API          | Testing resource retrieval and creation    |
| JSON              | Validating request and response data       |
| GitHub            | Version control and portfolio presentation |
| Markdown          | Test documentation and reporting           |

## How to Run the Tests

### Prerequisites

* Install [Postman](https://www.postman.com/downloads/).
* Ensure you have an internet connection.

### Execution Steps

1. Clone or download this repository.
2. Open Postman.
3. Click **Import**.
4. Import `postman/API_Testing_Postman_Collection.json`.
5. Verify that the `baseUrl` variable is set to `https://jsonplaceholder.typicode.com`.
6. Execute each request individually and review its response.
7. Run the full collection to execute the available automated assertions.
8. Review the Postman test results and console output.
9. Record actual outcomes in `reports/API_Test_Cases_and_Results.md`.
10. Capture screenshots of the requests, responses, and test results.

**Important:** Ensure that all ten scenarios are implemented in your collection before claiming that the complete suite is covered.

## Test Configuration

| Variable                  | Default Value                          | Purpose                                         |
| ------------------------- | -------------------------------------- | ----------------------------------------------- |
| `baseUrl`                 | `https://jsonplaceholder.typicode.com` | Base URL for API requests                       |
| `responseTimeThresholdMs` | `1000`                                 | Example response-time threshold in milliseconds |

## Test Reporting

The `reports/` directory contains templates for documenting test execution and potential defects.

For each test scenario, record:

* Test ID and scenario description
* Request method and endpoint
* Expected result
* Actual result
* HTTP status code
* Pass/fail status or observation
* Execution date
* Supporting evidence
* Defect details, if a confirmed requirement violation is identified

Do not mark a scenario as passed until you have executed it and verified the result.

## Limitations

JSONPlaceholder is a public demonstration service rather than a production business API.

* POST requests simulate resource creation.
* Unsupported routes and nonexistent resources may behave differently from production APIs.
* Response times depend on network conditions and service availability.
* The project does not include authentication testing, authorization testing, security testing, or load testing.

These limitations must be considered when interpreting the test results.

## Conclusion

This project demonstrates my approach to structured API testing using Postman, including functional testing, response validation, negative testing, JSON data-type checks, and basic response-time assertions.

My focus is on developing maintainable test scripts, investigating actual API behavior, documenting results clearly, and providing actionable information that helps development teams improve software quality.

**Project disclosure:** This is an independent QA portfolio project using a public demo API. Actual test results should be documented after execution.
