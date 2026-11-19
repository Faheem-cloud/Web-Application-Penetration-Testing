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
