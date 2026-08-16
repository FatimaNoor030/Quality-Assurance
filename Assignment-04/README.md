# Assignment 04 – API Testing

## Overview

For this assignment, I worked on API testing using Postman and basic performance testing using Apache JMeter.

The main objective was to understand how APIs work, test different HTTP methods, validate API responses, create automated tests in Postman, and perform a basic load test using JMeter.

For the API testing part, I used JSONPlaceholder, a public REST API commonly used for testing and learning.

## Tools Used

- Postman
- Apache JMeter
- Java
- Git and GitHub

## Part 1 – API Testing with Postman

I started by creating a Postman collection named:

`JSONPlaceholder API Testing`

I organized the API requests inside the collection according to the HTTP methods required in the assignment.

### GET – All Posts

I created a GET request to retrieve all posts:

`https://jsonplaceholder.typicode.com/posts`

I checked the response and validated the response structure and important fields such as:

- id
- title
- body
- userId

I also added automated validations for the status code, response time, response structure, and required response fields.

### GET – Single Post

I then tested a single post using:

`https://jsonplaceholder.typicode.com/posts/1`

This helped me verify how the API behaves when retrieving a specific resource rather than the complete collection.

I added validations for the response status, response time, JSON structure, and required fields.

### POST – Create New Post

For the POST request, I used:

`https://jsonplaceholder.typicode.com/posts`

I sent a JSON request body containing a title, body, and userId.

The request returned a successful `201 Created` response.

I created automated tests to verify:

- Status code
- Response time
- Response structure
- Required fields
- Submitted values

This helped me understand how data is sent to an API and how the response can be validated automatically.

### PUT – Update Post

Next, I tested the PUT method using:

`https://jsonplaceholder.typicode.com/posts/1`

I updated the title and body of an existing post.

The API returned a successful response containing the updated values.

I added automated validations for the status code, response time, response structure, required fields, and updated values.

During testing, I initially used a response-time limit of 1000 ms. One request took slightly longer than this limit, so I reviewed the result and changed the validation threshold to 2000 ms instead of repeatedly running the request just to obtain a passing result.

### DELETE – Delete Post

Finally, I tested the DELETE method using:

`https://jsonplaceholder.typicode.com/posts/1`

The request returned a successful `200` status code.

For this request, I validated the status code, response time, and successful completion of the delete operation.

## Automated Testing in Postman

After creating the individual requests, I added automated tests using Postman's post-response test scripts.

The validations covered:

- HTTP status codes
- Response time
- JSON response structure
- Required response fields
- Specific response values where applicable

I then ran the complete collection using the Postman Collection Runner.

All five API requests completed successfully and the automated tests passed.

## Part 2 – Performance Testing with Apache JMeter

After completing the API testing in Postman, I moved to the performance testing part of the assignment.

I created a JMeter Test Plan and added a Thread Group with the configuration specified in the assignment:

- Number of users: 10
- Ramp-up period: 5 seconds
- Loop count: 5

I then added an HTTP Request Sampler for:

`https://jsonplaceholder.typicode.com/posts`

The HTTP method used was GET.

To observe the test execution and results, I added:

- View Results Tree
- Summary Report

## JMeter Test Results

The test generated a total of 50 samples.

| Metric | Result |
|---|---:|
| Samples | 50 |
| Average Response Time | 730 ms |
| Minimum Response Time | 136 ms |
| Maximum Response Time | 5073 ms |
| Error Rate | 0% |
| Throughput | 4.4 requests/sec |

The 50 samples were expected because the test used 10 virtual users with 5 iterations each.

The test completed with a 0% error rate, meaning all requests were successfully processed during the test.

The average response time was 730 ms. The minimum response time was 136 ms, while the maximum response time reached 5073 ms. This showed that although the requests were successful overall, there was some variation in response time during the load test.

The recorded throughput was 4.4 requests per second under the configured test conditions.

## What I Learned

Through this assignment, I gained practical experience in API testing rather than only working with testing concepts theoretically.

I learned how to:

- Create and organize API requests in Postman
- Work with GET, POST, PUT, and DELETE methods
- Read and validate API responses
- Write automated Postman test scripts
- Validate status codes and response times
- Validate JSON response structures and fields
- Run a complete Postman collection
- Export a Postman collection in JSON format
- Create a basic performance test plan in JMeter
- Configure virtual users, ramp-up time, and iterations
- Analyze response time, throughput, and error rate
- Document and interpret testing results

## Assignment Deliverables

The Assignment 04 folder contains:

- Postman Collection
- JMeter Test Plan
- Postman testing screenshots
- JMeter testing screenshots
- JMeter Summary Report screenshot
- This README file

## Conclusion

This assignment helped me understand the difference between functional API validation and basic performance testing.

Using Postman, I focused on verifying whether the API requests and responses behaved as expected. With JMeter, I then tested how the API performed when multiple virtual users sent requests.

Overall, this was a practical step toward understanding API testing and performance testing as part of the QA process.
