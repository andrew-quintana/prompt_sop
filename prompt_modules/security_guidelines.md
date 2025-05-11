# Security Best Practices Module

## Purpose
This module provides guidelines for safely handling sensitive information and implementing secure coding practices to protect user data and systems.

## Sensitive Data Protection

### Never expose or handle in insecure ways:
- **Authentication Credentials**
  - API keys, tokens, and secrets
  - Passwords and password hashes
  - OAuth tokens and refresh tokens
  - Session identifiers

- **Personal Identifiable Information (PII)**
  - Full names 
  - Email addresses
  - Phone numbers
  - Physical addresses
  - Government-issued identification numbers
  - IP addresses
  - MAC addresses
  - Device identifiers

- **Access Information**
  - Database connection strings
  - Server hostnames and IP addresses
  - Usernames
  - SSH keys
  - Certificate private keys

- **Financial Data**
  - Credit card information
  - Bank account details
  - Cryptocurrency wallet addresses/keys
  - Payment processing credentials

- **Infrastructure Details**
  - Internal network layouts
  - Server configurations
  - Port mappings
  - Firewall rules

## Security Implementation Guidelines

### Environment Variables and Configuration
- Always use environment variables or secure configuration management for sensitive values
- Never hardcode sensitive data in source code
- Recommend using `.env` files (which must be in `.gitignore`)
- For configuration examples, use placeholder values like `YOUR_API_KEY_HERE`

### Secure Coding Practices
- Implement proper input validation and sanitization
- Use parameterized queries to prevent SQL injection
- Escape output to prevent XSS attacks
- Implement proper authentication and authorization checks
- Use secure, up-to-date encryption algorithms and hashing functions
- Follow the principle of least privilege

### Data Handling
- Minimize data collection to what's necessary
- Implement proper data encryption (at rest and in transit)
- Use secure deletion practices when disposing of sensitive data
- Implement timeouts for sensitive operations
- Add rate limiting for authentication attempts

### API Security
- Implement proper authentication for all API endpoints
- Use HTTPS/TLS for all communications
- Validate all incoming data
- Implement proper error handling that doesn't leak sensitive information
- Use appropriate HTTP status codes and headers

### Frontend Security
- Never store sensitive data in client-side storage (localStorage, sessionStorage)
- Implement proper CSRF protection
- Use Content Security Policy headers
- Sanitize user inputs to prevent DOM-based XSS

### Database Security
- Use prepared statements or ORM tools
- Implement proper access controls
- Encrypt sensitive data
- Regularly backup and test restore procedures

### Logging and Monitoring
- Never log sensitive information
- Implement proper log rotation and retention policies
- Develop procedures for security incident logging

## Implementation Guidance

When coding, always:
1. **Identify** potential sensitive data in the requirements
2. **Suggest** secure storage methods for sensitive data
3. **Implement** appropriate security controls based on data sensitivity
4. **Review** code for security vulnerabilities before finalizing
5. **Recommend** additional security measures when appropriate

## Example Implementations

### Example: Secure API Key Handling (Node.js)
```javascript
// CORRECT: Load API key from environment variable
const apiKey = process.env.API_KEY;
if (!apiKey) {
  throw new Error('API key is required');
}

// INCORRECT: Hardcoding API key
const apiKey = "YOUR_FAKE_API_KEY_EXAMPLE";
```

### Example: Secure Database Connection (Python)
```python
# CORRECT: Using environment variables for database credentials
import os
from sqlalchemy import create_engine

db_user = os.environ.get('DB_USER')
db_pass = os.environ.get('DB_PASS')
db_host = os.environ.get('DB_HOST')
db_name = os.environ.get('DB_NAME')

connection_string = f"postgresql://{db_user}:{db_pass}@{db_host}/{db_name}"
engine = create_engine(connection_string)

# INCORRECT: Hardcoding database credentials
connection_string = "postgresql://username:password@example-db.company.com/example_db"
```

### Example: Secure Password Handling
```javascript
// CORRECT: Using bcrypt for password hashing
const bcrypt = require('bcrypt');

async function storeUserPassword(password) {
  const saltRounds = 10;
  const hashedPassword = await bcrypt.hash(password, saltRounds);
  // Store hashedPassword in database
}

async function verifyPassword(password, hashedPassword) {
  return await bcrypt.compare(password, hashedPassword);
}

// INCORRECT: Storing plain text passwords
function storeUserPassword(password) {
  // Directly storing the password
  user.password = password;
  // Save user to database
}
```

## Check Yourself
When reviewing code for security issues, ask:
1. Is any sensitive data hardcoded?
2. Are we properly validating and sanitizing inputs?
3. Are we using secure, up-to-date libraries and dependencies?
4. Could this code inadvertently expose internal system details?
5. Are authentication and authorization mechanisms properly implemented?
6. Are we encrypting sensitive data appropriately?
7. Are we following security best practices for the specific frameworks and languages used? 