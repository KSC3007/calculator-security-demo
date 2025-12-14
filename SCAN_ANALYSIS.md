# Security Scan Analysis - [December 14, 2025]

## DAST Results (ZAP Baseline)
- Total URLs scanned: 3
- PASS: Information not available
- WARN-NEW: 9 warnings (3 medium, 6 low alerts)
- FAIL-NEW: 0 failures

### Warning Summary
10038: Content Security Policy (CSP) Header Not Set (Medium)
10106: HTTP Only Site (Medium)
10020: Missing Anti-clickjacking Header (Medium)
90004: Insufficient Site Isolation Against Spectre Vulnerability (Low)
10037: Permissions Policy Header Not Set (Low)
10021: Server Leaks Version Information via "Server" HTTP Response Header Field (Low)
10035: Strict-Transport-Security Header Not Set (Low)
10034: X-Content-Type-Options Header Missing (Low)

## SCA Results (Dependency Check)
- High severity: 0
- Medium severity: 0
- Low severity: 0

### Vulnerable Packages
No vulnerabilities detected

## SAST Results (CodeQL)
- Total issues: 1
- By type: Flask app is run in debug mode (High)

## Recommendations
Based on the DAST findings, the following recommendations are prioritised:

1. Critical Header Implementation (Medium Risk):
- Implement a Content-Security-Policy (CSP) header to mitigate Cross-Site Scripting (XSS) and other injection attacks.
- Implement an Anti-clickjacking Header to prevent clickjacking attacks
- Enforce HTTPS by configuring the site to be served under HTTPS instead of HTTP only.

2. Mitigate Client-Side Issues (Low Risk):
- Set the 'X-Content-Type-Options: nosniff' header to prevent browsers from MIME-sniffing the content type.
- Address Insufficient Site Isolation by implementing the 'Cross-Origin-Resource-Policy' header (e.g., set to 'same-origin') to help counter side-channel attacks like Spectre.
- Review and implement appropriate 'Cache-Control' headers (e.g., no-cache, no-store, must-revalidate, private) for responses that may contain sensitive data, addressing the 'Storable and Cacheable Content' finding.

3. Information Disclosure (Low Risk):
- Configure the web server to suppress or remove version information exposed via the "Server" HTTP response header field.

## Summary table
| Code | Issue | Risk | Affected | Why It Matters |
| :-- | :-- | :-- | :-- | :-- |
| 10038 | Content Security Policy (CSP) Header Not Set | Medium | http://localhost:5000<br>http://localhost:5000/<br>http://localhost:5000/favicon.ico<br>http://localhost:5000/robots.txt<br>http://localhost:5000/sitemap.xml | Detects and mitigates certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks |
| 10106 | HTTP Only Site | Medium | http://localhost:5000 | Encrypts data sent, making HTTPS more secure than HTTP |
| 10020 | Missing Anti-clickjacking Header | Medium | http://localhost:5000<br>http://localhost:5000/ | Prevents Clickjacking attacks |
| 90004 | Insufficient Site Isolation Against Spectre Vulnerability | Low | localhost:5000<br>http://localhost:5000/ | Prevents side-channels attacks like Spectre |
| 10037 | Permissions Policy Header Not Set | Low | http://localhost:5000<br>http://localhost:5000/<br>http://localhost:5000/favicon.ico<br>http://localhost:5000/robots.txt<br>http://localhost:5000/sitemap.xml | Resctricts unauthorized access or usage of browser/client features by web resources |
| 10021 | Server Leaks Version Information via "Server" HTTP Response Header Field | Low | http://localhost:5000<br>http://localhost:5000/<br>http://localhost:5000/favicon.ico<br>http://localhost:5000/robots.txt<br>http://localhost:5000/sitemap.xml | Prevents version information from being leaked, preventing attackers from identifying vulnerabilities |
| 10035 | Strict-Transport-Security Header Not Set | Low | https://firefox-settings-attachments.cdn.mozilla.net/main-workspace/tracking-protection-lists/5654b845-5c86-4315-9c04-c38b6962fa88 | Declares that complying user agents (such as a web browser) are to interact with it using only secure HTTPS connections (i.e. HTTP layered over TLS/SSL) |
| 10034 | X-Content-Type-Options Header Missing | Low | http://localhost:5000 | Allows older versions of Internet Explorer and Chrome to perform MIME-sniffing on the response body, potentially causing the response body to be interpreted and displayed as a content type other than the declared content type | 