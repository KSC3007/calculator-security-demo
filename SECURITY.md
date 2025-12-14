# Security Scanning

## Overview
This repository uses three types of security scanning:

### SAST (Static Analysis with CodeQL)
- Scans source code for vulnerabilities
- Runs on push to main branch
- Checks for: Code injection vulnerabilities, Hardcoded secrets and sensitive data, Insecure configurations, Insecure data flow patterns
- Artifacts: See GitHub Security tab

### SCA (Dependency Check)
- Scans Python packages for known CVEs
- Runs on push to main branch
- Checks for: Outdated packages with CVEs, Known vulnerable packages, License compliance issues
- Artifacts: sca-reports

### DAST (Live Application with ZAP)
- Tests running application for vulnerabilities
- Runs on push to main branch
- Checks for: SQL injection, Cross-site scripting (XSS), Security misconfigurations, Broken authentication
- Artifacts: zap-baseline-reports, zap-fullscan-reports

## Understanding Results
- [Complete Security Scanning Guide for Beginners: Interpreting DAST Scan Results](https://github.com/Lowkh/Practice_SAST_SCA_DAST/blob/main/README.md#part-10-interpreting-dast)

## Reporting Vulnerabilities
Please email S10243956@connect.np.edu.sg or kohshanchun@gmail.com