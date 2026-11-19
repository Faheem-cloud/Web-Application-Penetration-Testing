🔐 Web Application Penetration Testing

A hands-on cybersecurity project focused on identifying and analysing web application vulnerabilities using OWASP Juice Shop, Burp Suite Community Edition, and Docker.

🎯 Project Objective

To perform practical web application security testing, identify potential vulnerabilities, analyse HTTP requests and responses, and document security findings with appropriate remediation recommendations.

🛠️ Tools & Technologies

* OWASP Juice Shop
* Burp Suite Community Edition
* Docker Desktop
* macOS (Apple Silicon)
* HTTP/HTTPS
* REST APIs
* JWT Authentication

🧪 Practical Implementation

1. Environment Setup

* Installed Docker Desktop.
* Deployed OWASP Juice Shop locally.
* Configured a controlled penetration testing environment.

2. HTTP Request Analysis

* Captured HTTP requests using Burp Suite.
* Analysed GET and POST methods.
* Inspected HTTP headers and status codes.
* Examined API endpoints and query parameters.

3. SQL Injection Investigation

* Tested the product search endpoint.
* Analysed special-character input handling.
* Observed SQLite syntax errors.
* Identified potential unsafe SQL query construction and database error disclosure.

4. Cross-Site Scripting (XSS)

* Performed controlled XSS testing.
* Demonstrated JavaScript execution through the search functionality.
* Studied client-side input handling and XSS prevention.

5. Authentication Security Testing

* Registered a test user.
* Captured login requests.
* Analysed authentication responses.
* Identified JWT-based authentication.
* Examined Bearer token usage.

6. Authentication Enforcement Testing

* Tested the /rest/user/whoami endpoint.
* Removed the Authorization header.
* Observed an HTTP 400 Bad Request response.
* Recorded the result for further investigation.

📸 Project Evidence

OWASP Juice Shop

Burp Suite HTTP History

Search API Analysis

API Response

Burp Suite Repeater

SQL Injection Investigation

Cross-Site Scripting

User Registration

Login Authentication

JWT Authentication

📚 Key Learning Outcomes

* Web application penetration testing fundamentals.
* HTTP request and response analysis.
* REST API security testing.
* SQL injection investigation.
* Cross-Site Scripting testing.
* Authentication and JWT analysis.
* Burp Suite Proxy and Repeater.
* Vulnerability documentation and remediation.

🔒 Security Recommendations

* Use parameterized SQL queries.
* Implement proper input validation.
* Apply context-aware output encoding.
* Implement secure authentication mechanisms.
* Protect authentication tokens and session cookies.
* Avoid exposing detailed database errors.
* Enforce authorization on protected API endpoints.

📂 Project Structure

Web-Application-Penetration-Testing/
│
├── README.md
│
├── assets/
│   ├── assessment-workflow.png
│   ├── http-request-flow.png
│   └── lab-architecture.png
│
├── screenshots/
│   ├── 01-juice-shop-running.png
│   ├── 02-burp-initial-http-history.png
│   ├── 03-search-request-empty-parameter.png
│   ├── 04-search-request-apple.png
│   ├── 05-search-api-json-response.png
│   ├── 06-repeater-banana-test.png
│   ├── 07-sql-error-observation.png
│   ├── 08-xss-alert-proof.png
│   ├── 09-registration-response-redacted.png
│   ├── 10-login-request-response.png
│   └── 11-whoami-request-redacted.png
│
└── reports/
    └── vulnerability-assessment-report.md

⚠️ Disclaimer

This project was conducted exclusively in a local OWASP Juice Shop testing environment for educational purposes. No unauthorized systems were accessed.

Potential vulnerabilities are documented as observations until independently validated.
