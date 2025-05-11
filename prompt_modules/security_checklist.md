# Security Implementation Checklist

This checklist provides practical security implementation guidance for common coding scenarios.

## Authentication Systems

- [ ] Passwords are properly hashed (bcrypt/Argon2) with appropriate cost factors
- [ ] Multi-factor authentication is implemented or recommended
- [ ] Account lockout policies are in place for failed attempts
- [ ] Password requirements follow NIST guidelines
- [ ] Sessions are properly managed (rotation, timeouts, secure flags)
- [ ] Forgot password flows are secure
- [ ] Account enumeration is prevented
- [ ] User input is properly validated and sanitized

## API Development

- [ ] Authentication is required for all non-public endpoints
- [ ] Authorization checks are implemented
- [ ] Rate limiting is in place
- [ ] Input validation is thorough
- [ ] Error responses don't leak sensitive information
- [ ] Proper HTTP methods are used
- [ ] HTTPS is enforced
- [ ] CORS is properly configured
- [ ] API keys are properly handled (not in code)
- [ ] Logging doesn't capture sensitive data

## Database Operations

- [ ] Parameterized queries or ORM are used (no string concatenation)
- [ ] Least privilege principle is applied to database users
- [ ] Sensitive data is encrypted at rest
- [ ] Connections are secured (TLS)
- [ ] Credentials are loaded from secure sources
- [ ] Database error messages are not exposed to users
- [ ] Input validation before database operations
- [ ] Transactions are used appropriately
- [ ] Pagination is implemented for large datasets

## File Operations

- [ ] Path traversal attacks are prevented
- [ ] File uploads are properly validated (type, size, content)
- [ ] Uploaded files are stored outside webroot
- [ ] File permissions are properly set
- [ ] Temporary files are securely handled
- [ ] File downloads are properly secured
- [ ] User-supplied filenames are sanitized

## Frontend Security

- [ ] XSS prevention is implemented
- [ ] CSRF protection is in place
- [ ] Content Security Policy is configured
- [ ] Sensitive data is not stored in localStorage/sessionStorage
- [ ] Third-party libraries are from trusted sources
- [ ] Subresource Integrity is used where appropriate
- [ ] Cookies have appropriate security flags
- [ ] Sensitive data is not exposed in URLs

## Mobile App Security

- [ ] Certificate pinning is implemented
- [ ] App permissions follow least privilege
- [ ] Sensitive data is not stored in plain text
- [ ] Secure communication channels are used
- [ ] Authentication tokens are securely stored
- [ ] Biometric authentication is properly implemented
- [ ] App data is encrypted when at rest
- [ ] Clipboard data is protected for sensitive fields

## Deployment & Infrastructure

- [ ] Production credentials are not in version control
- [ ] Environment variables are used for configuration
- [ ] CI/CD pipeline is secured
- [ ] Dependency scanning is implemented
- [ ] Vulnerability scanning is in place
- [ ] Proper network segmentation is recommended
- [ ] HTTPS is properly configured
- [ ] Security headers are implemented

## Sensitive Data Handling

- [ ] Data minimization is practiced
- [ ] Data is encrypted in transit
- [ ] Sensitive data is encrypted at rest
- [ ] Data masking is used in logs and displays
- [ ] PII is properly protected
- [ ] Financial data follows PCI-DSS guidelines
- [ ] Healthcare data follows relevant regulations (HIPAA, etc.)
- [ ] Data retention policies are implemented

## Third-Party Integrations

- [ ] OAuth flows are correctly implemented
- [ ] API secrets are properly stored
- [ ] Webhook endpoints are secured
- [ ] Callbacks validate authenticity
- [ ] Data shared with third parties is minimized
- [ ] Third-party libraries are kept updated
- [ ] Fallbacks exist for third-party failures

## Security Testing Recommendations

- [ ] Static Application Security Testing (SAST)
- [ ] Dynamic Application Security Testing (DAST)
- [ ] Regular dependency scanning
- [ ] Security code reviews
- [ ] Penetration testing
- [ ] Threat modeling
- [ ] Security logging and monitoring
- [ ] Regular security training for developers 