# Scanner Comparison

## Only CodeQL (SAST) Found
- Flask app is run in debug mode

## Only ZAP (DAST) Found
- Content Security Policy (CSP) Header Not Set
- Insufficient Site Isolation Against Spectre Vulnerability
- Permissions Policy Header Not Set
- Server Leaks Version Information via "Server" HTTP Response Header Field
- X-Content-Type-Options Header Missing

## Only Dependency-Check (SCA) Found
- No vulnerabilities found

## All Three Tools
- Unlikely - they focus on different layers