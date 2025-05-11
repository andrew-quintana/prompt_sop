# Security Module Integration Guide

This guide explains how to integrate the security modules into your broader prompt system for coding agents.

## Module Overview

The security module system consists of three components:

1. **Security Best Practices** (`security_guidelines.md`) - Comprehensive reference for secure coding practices
2. **Security Agent Prompt** (`security_agent_prompt.md`) - Directive instructions for the coding agent
3. **Security Checklist** (`security_checklist.md`) - Practical implementation checklists for different scenarios

## Integration Methods

### Method 1: Full Security-First Integration

For applications where security is paramount (financial, healthcare, enterprise), include the full security agent prompt at the top level of your instructions:

```
[General Agent Instructions]

# Security-First Directive
{include: security_agent_prompt.md}

[Remaining Instructions]
```

### Method 2: Contextual Security Integration

For general applications, integrate security directives as a specific section:

```
[General Agent Instructions]

# Task-Specific Guidelines
...

# Security Guidelines
When implementing the solution, follow these security practices:
{include: sections_from_security_agent_prompt.md}

[Remaining Instructions]
```

### Method 3: Referenced Security Knowledge

For situations where space is limited, reference the security knowledge and include only key points:

```
[General Agent Instructions]

You have knowledge of secure coding practices as defined in the security guidelines.
The most important principles to follow are:

1. Never hardcode sensitive data
2. Use environment variables for configuration
3. Implement proper input validation
4. Use parameterized queries for database operations
5. Encrypt sensitive data at rest and in transit

[Remaining Instructions]
```

## Domain-Specific Security Integration

### Web Application Development

```
When developing web applications:

1. Ensure all user inputs are validated and sanitized
2. Implement CSRF protection on all forms 
3. Use Content-Security-Policy headers
4. Set proper cookie flags (secure, httpOnly, SameSite)
5. Never store sensitive data in client-side storage

{include: relevant_sections_from_security_checklist.md#frontend-security}
```

### API Development

```
When developing APIs:

1. Implement proper authentication and authorization
2. Validate all inputs
3. Use rate limiting to prevent abuse
4. Return appropriate error codes without leaking information
5. Implement proper CORS configuration

{include: relevant_sections_from_security_checklist.md#api-development}
```

### Data-Handling Applications

```
When handling sensitive data:

1. Follow data minimization principles
2. Implement appropriate encryption at rest
3. Use secure channels for data transmission
4. Apply proper access controls
5. Follow relevant regulatory requirements (GDPR, HIPAA, etc.)

{include: relevant_sections_from_security_checklist.md#sensitive-data-handling}
```

## Contextual Triggers

Include these directives to activate security checks based on specific code contexts:

```
When you detect any of the following in a user request:
- Authentication implementation
- Database operations
- API endpoints 
- File operations
- User input handling
- Configuration management

Automatically apply the relevant security checklist from {security_checklist.md}
```

## Example: Complete Integration

```
You are a helpful coding assistant that helps users write high-quality, secure code.

{include: security_agent_prompt.md}

When implementing solutions:
1. Focus on readability and maintainability
2. Follow language-specific best practices
3. Apply security measures appropriate to the context

For specific security scenarios, refer to these guidelines:
{include: security_checklist.md#authentication-systems}
{include: security_checklist.md#api-development}
{include: security_checklist.md#database-operations}

Remember to verify your solution against security best practices before providing it to the user.
```

## Security Override Prevention

To prevent users from inadvertently requesting insecure implementations, include:

```
If a user explicitly requests code that would violate security best practices:
1. Acknowledge their request
2. Explain the security concerns
3. Offer a secure alternative 
4. Only proceed with the secure implementation

Never implement insecure patterns even if specifically requested.
``` 