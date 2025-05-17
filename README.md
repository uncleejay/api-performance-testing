# k6 API Performance Testing

A project for performance testing APIs using k6, an open-source load testing tool. This project demonstrates how to set up and run automated performance tests for RESTful APIs.

## Prerequisites

Before you can run these tests, you'll need to install k6:

### macOS
```bash
brew install k6
```

### Linux
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
echo "deb https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
sudo apt-get update
sudo apt-get install k6
```

### Windows
```bash
choco install k6
```

For other installation methods, refer to the [k6 installation documentation](https://k6.io/docs/getting-started/installation/).

## Project Structure

```
k6-api-performance-testing/
│
└── api-test.js - Basic API authentication test
```

## Usage Instructions

To run the basic API test:

```bash
k6 run api-test.js
```

You can specify the number of virtual users and test duration:

```bash
# Run with 10 virtual users for 30 seconds
k6 run --vus 10 --duration 30s api-test.js
```

## Test Description

### api-test.js

This test makes a POST request to a test authentication endpoint with the following characteristics:

- **Endpoint**: https://test-api.k6.io/auth/basic/login/
- **Method**: POST
- **Payload**: Username and password in JSON format
- **Validation**: Checks that the response code is 200

The test uses k6's check functionality to validate the response status and will report success or failure based on this check.

## Extending the Project

To add more API tests, create new JavaScript files following the structure in api-test.js. You can organize tests by functionality or endpoint for better maintainability.

For complex scenarios, consider using k6's built-in features:
- Test lifecycle hooks
- Thresholds for performance criteria
- Custom metrics
- Scenarios for advanced load testing patterns

## Reporting

k6 provides detailed reports after each test run. For more advanced reporting options:

```bash
# Output results to JSON file
k6 run --out json=results.json api-test.js

# Output results to CSV file
k6 run --out csv=results.csv api-test.js
```

For visual reports, consider integration with tools like Grafana or using the k6 cloud service.

