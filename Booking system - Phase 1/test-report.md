# Booking System - Phase 1 Test Report

## Overview
This report documents the security vulnerabilities identified in the Booking System during Phase 1 testing and provides the corresponding resolutions.

## Tools Used
- **Checkmarx**: Static Application Security Testing (SAST)
- **OWASP ZAP**: Dynamic Application Security Testing (DAST)

## Identified Security Issues and Resolutions

### 1. Cross-Site Scripting (XSS)
**Description**: The username field previously accepted script input, allowing malicious scripts to execute in users' browsers.  
**Impact**: Potential session hijacking, phishing, or data theft.  

**Recommendation**:
- Implement input validation to reject script input.
- Apply output encoding to neutralize harmful scripts.
- Use Content Security Policy (CSP) to restrict script execution.

**Fix**:  
- Input validation has been applied to reject any script input in the username field.
- Output encoding has been implemented to neutralize harmful scripts.
- Content Security Policy (CSP) headers have been configured to restrict script execution.

### 2. SQL Injection
**Description**: A high-risk SQL Injection vulnerability was identified using OWASP ZAP.  
**Steps to Reproduce**:
1. Opened the registration page in Firefox and accessed developer tools.
2. Registered a new user and saved a HAR file.
3. Imported the HAR file into ZAP and performed an attack.
4. Discovered SQL Injection vulnerability in the username parameter.  
**Impact**: An attacker could modify usernames by injecting SQL queries and potentially access sensitive database information.

**Recommendation**:
- Use prepared statements and parameterized queries.
- Implement input validation and sanitization.
- Restrict database error messages to avoid information disclosure.

**Fix**:
- Prepared statements and parameterized queries have been implemented to prevent SQL injection attacks.
- Input validation and sanitization have been applied to all user inputs.
- Database error messages are now restricted to prevent leakage of sensitive information.

### 3. Weak Password Policy
**Description**: The application previously accepted extremely weak passwords, including single-character usernames and passwords. Errors were only triggered if the username was already in use or fields were left empty.  
**Impact**: Weak password policies increase the risk of brute-force and credential-stuffing attacks, making it easier for attackers to gain unauthorized access.

**Recommendation**:
- Enforce strong password requirements (minimum length, complexity, disallow common passwords).
- Implement password validation functions in the registration and authentication processes.

**Fix**:
- A strong password policy has been enforced, including minimum length, complexity requirements, and restriction of common passwords.
- Password validation functions have been integrated into the registration and authentication processes.

### 4. Unprotected Admin Functionality
**Description**: Admin features were accessible without proper authentication and authorization checks, allowing anyone to modify user accounts, site settings, or delete critical data.  
**Impact**: Unauthorized users could take full control of the system, leading to data breaches, loss of integrity, and service disruption.

**Recommendation**:
- Implement strong access control mechanisms like Role-Based Access Control (RBAC).
- Validate user permissions before granting access to sensitive admin features.
- Require multi-factor authentication (MFA) for admin accounts.

**Fix**:
- Strong access control mechanisms (RBAC) have been implemented to restrict admin access based on roles.
- User permissions are validated before granting access to sensitive admin features.
- Multi-factor authentication (MFA) has been required for admin accounts to enhance security.

## Conclusion
All identified security vulnerabilities in the Booking System have been addressed and fixed. The system is now more secure and ready to move to the next development phase.


