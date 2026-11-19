# Screenshot Evidence

These are screenshots captured during the user's local OWASP Juice Shop exercises. Sensitive values visible in the original captures have been redacted in the copies included here.

| File | Evidence |
|---|---|
| `01-juice-shop-running.png` | Local Juice Shop homepage |
| `02-burp-initial-http-history.png` | Burp Suite HTTP history |
| `03-search-request-empty-parameter.png` | Search endpoint with empty query |
| `04-search-request-apple.png` | Captured product-search request |
| `05-search-api-json-response.png` | JSON response for an `apple` search |
| `06-repeater-banana-test.png` | Repeater test using `banana` |
| `07-sql-error-observation.png` | SQLite syntax error and query detail exposure |
| `08-xss-alert-proof.png` | JavaScript alert observed in local search flow |
| `09-registration-response-redacted.png` | Registration response; email redacted |
| `10-login-request-response.png` | Login exchange; token area redacted |
| `11-whoami-request-redacted.png` | Authenticated whoami request; Bearer token redacted |

The screenshots are evidence of the observed exercises, not proof that every suspected vulnerability is exploitable. The authentication test returned HTTP 400 and remains inconclusive.


# Web Application Penetration Testing

A practical web-application security assessment using **OWASP Juice Shop**, **Docker Desktop**, and **Burp Suite Community Edition** in a controlled local lab.

> **Scope:** All testing was performed against the locally hosted OWASP Juice Shop at `http://localhost:3000`. Only test systems you own or are explicitly authorized to assess.

## Lab Architecture

![Local lab architecture](assets/lab-architecture.png)

## Objectives

- Set up a repeatable local web-security lab.
- Inspect HTTP requests, responses, headers, and JSON API data.
- Use Burp Suite Proxy and Repeater for controlled request analysis.
- Investigate SQL error disclosure and potential unsafe query construction.
- Demonstrate client-side JavaScript execution in the local application.
- Review login, Bearer-token authentication, and authentication enforcement.

## Tools

- OWASP Juice Shop
- Docker Desktop
- Burp Suite Community Edition
- Burp Browser
- macOS (Apple Silicon)

## Practical Work and Evidence

### 1. Local target setup

OWASP Juice Shop was deployed locally using Docker.

![OWASP Juice Shop running](screenshots/01-juice-shop-running.png)

### 2. HTTP request and API analysis

Captured application traffic in Burp Suite and inspected the product-search endpoint, query parameters, status codes, and JSON responses.

![Burp HTTP history](screenshots/02-burp-initial-http-history.png)

![Search request](screenshots/04-search-request-apple.png)

![Search API JSON response](screenshots/05-search-api-json-response.png)

### 3. Burp Repeater

Modified a harmless search parameter and compared the server response.

![Repeater banana test](screenshots/06-repeater-banana-test.png)

### 4. SQL error investigation

A search input containing an encoded apostrophe produced an HTTP 500 response with SQLite syntax details and part of the SQL query.

**Assessment:** This is evidence of database error disclosure and a potential unsafe SQL construction issue. It is not sufficient on its own to confirm exploitable SQL injection.

![SQL error observation](screenshots/07-sql-error-observation.png)

**Recommended remediation:** Use parameterized SQL queries, validate input, and return generic client-facing errors while keeping diagnostics in protected server logs.

### 5. Cross-Site Scripting investigation

A controlled proof-of-execution input in the local search flow caused a JavaScript alert to appear.

**Assessment:** Client-side JavaScript execution was demonstrated in the tested context. Confirm the exact source-to-sink flow before assigning a specific XSS subtype or severity.

![XSS alert proof](screenshots/08-xss-alert-proof.png)

**Recommended remediation:** Use context-aware output encoding, safe DOM APIs such as `textContent`, sanitize HTML where necessary, and apply a restrictive Content Security Policy as defence in depth.

### 6. Registration and login analysis

Registered a test user and captured the registration and login exchanges. Sensitive email and token values have been redacted from the published evidence.

![Registration response](screenshots/09-registration-response-redacted.png)

![Login response](screenshots/10-login-request-response.png)

### 7. JWT and authenticated endpoint review

Observed a Bearer token being sent with a request to `/rest/user/whoami`. The published screenshot has the token redacted.

![Whoami request redacted](screenshots/11-whoami-request-redacted.png)

An authentication-enforcement test without the Authorization header returned **HTTP 400 Bad Request**. This result is **inconclusive**; the response body and a clean unauthenticated control request must be reviewed before drawing a security conclusion.

## Assessment Workflow

![Assessment workflow](assets/assessment-workflow.png)

## Key Learning Outcomes

- HTTP request and response analysis
- REST API endpoint discovery
- Burp Suite Proxy and Repeater
- SQL error disclosure investigation
- XSS proof-of-execution testing
- Login and JWT/Bearer-token review
- Evidence handling and remediation documentation

## Repository Structure

```text
.
├── README.md
├── assets/
│   ├── assessment-workflow.png
│   ├── http-request-flow.png
│   └── lab-architecture.png
├── reports/
│   └── vulnerability-assessment-report.md
└── screenshots/
    ├── README.md
    └── [redacted practical evidence]
```

## Report

See [`reports/vulnerability-assessment-report.md`](reports/vulnerability-assessment-report.md) for the detailed observations, limitations, and remediation recommendations.

## Disclaimer

This is an educational project conducted in an isolated local lab. Do not test systems without explicit authorization. Screenshots have been reviewed for visible credentials, but review them again before public publication.
