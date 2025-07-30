# Security Planning Wizard

## Overview
Analyses PRD requirements and technology selections to create appropriate security implementation guidance. Enhances task briefs with security constraints and generates security-specific implementation requirements.

## Phase 1: Security Requirements Analysis

### PRD Security Trigger Detection
**Scan PRD and existing task briefs for security indicators:**

**Authentication Requirements:**
- "user accounts", "login", "registration" → User authentication needed
- "admin", "roles", "permissions" → Authorisation and role management
- "personal data", "user information" → Data protection requirements
- "password", "secure access" → Credential management needs

**Data Protection Requirements:**
- "personal information", "user data" → Privacy and GDPR considerations
- "payment", "financial", "credit card" → PCI-DSS compliance potential
- "healthcare", "medical" → Additional regulatory requirements
- "business data", "confidential" → Enterprise security considerations

**External Access Requirements:**
- "public", "internet", "website" → Public-facing security concerns
- "API", "integration" → API security and authentication
- "mobile", "app" → Mobile-specific security considerations
- "third-party", "external service" → Integration security requirements

## Phase 2: Security Level Determination

### Intelligent Security Level Assessment
**Based on PRD analysis and project type, determine appropriate security level:**

#### Basic Security Level
**Triggered by:**
- Personal projects with minimal sensitive data
- Simple authentication needs
- No regulatory compliance mentioned
- POC or prototype projects

**Security Focus:**
- Secure authentication patterns
- Basic data protection
- Input validation and sanitisation
- HTTPS enforcement

#### Enhanced Security Level  
**Triggered by:**
- Business or startup projects
- User personal data handling
- Public-facing applications
- API endpoints with sensitive operations

**Security Focus:**
- Comprehensive authentication and authorisation
- Data encryption at rest and in transit
- Security headers and middleware
- Audit logging and monitoring

#### Compliance-Focused Security Level
**Triggered by:**
- GDPR, PCI-DSS, or other compliance mentions
- Healthcare, financial, or regulated industry data
- Enterprise or client projects
- High-value or sensitive business data

**Security Focus:**
- Regulatory compliance implementation
- Comprehensive audit trails
- Data sovereignty and retention policies
- Security testing and validation procedures

## Phase 3: Security Implementation Planning

### Authentication and Authorisation Strategy

#### For Basic Security Level
```
Authentication Approach: Simple user accounts with secure practices
Implementation Constraints:
- Secure password hashing (bcrypt with appropriate rounds)
- Session management with reasonable timeouts
- Basic rate limiting on authentication endpoints
- Secure password reset functionality

Research Areas:
- Current authentication patterns for [chosen technology stack]
- Session security best practices
- Password policy recommendations
```

#### For Enhanced Security Level
```
Authentication Approach: Comprehensive user management with role-based access
Implementation Constraints:
- Multi-factor authentication capability
- JWT or session-based authentication with refresh tokens
- Role-based permission system
- Account lockout and security monitoring

Research Areas:
- OAuth 2.0 implementation patterns
- JWT security best practices
- Role-based access control (RBAC) patterns
- Security monitoring and alerting
```

#### For Compliance-Focused Security Level
```
Authentication Approach: Enterprise-grade authentication with audit compliance
Implementation Constraints:
- Comprehensive audit trail for all authentication events
- Strong password policies with complexity requirements
- Multi-factor authentication mandatory for sensitive operations
- Integration with compliance frameworks (GDPR, PCI-DSS, etc.)

Research Areas:
- Compliance-specific authentication requirements
- Audit trail implementation patterns
- Data protection impact assessment (DPIA) requirements
- Security incident response procedures
```

### Data Protection Strategy

#### Data Classification and Handling
```
Data Protection Approach: [Level-appropriate data handling]
Implementation Constraints:
- Encryption for data at rest (database encryption)
- HTTPS/TLS for all data transmission
- Input validation and sanitisation for all user inputs
- Secure data deletion and retention policies

Research Areas:
- Database encryption options for [chosen database]
- Data validation libraries and patterns
- GDPR compliance for UK users (if applicable)
- Secure file upload and storage practices
```

### API and Integration Security

#### For Projects with API Requirements
```
API Security Approach: Secure API design and implementation
Implementation Constraints:
- API authentication (API keys, JWT, or OAuth)
- Rate limiting and abuse prevention
- Input validation and output sanitisation
- CORS configuration for web applications

Research Areas:
- RESTful API security best practices
- API rate limiting patterns
- CORS configuration for [chosen frontend technology]
- API documentation and security considerations
```

## Phase 4: Security Task Brief Enhancement

### Enhanced Task Briefs with Security Context

**Original Task Brief:**
```
Task 2: Establish User Security
Goal: Protect user data and control access to application features
Constraints: UK GDPR compliance, modern security standards, user-friendly experience
Research Areas: Authentication patterns, data protection best practices
```

**Enhanced with Security Planning:**
```
Task 2: Establish User Security
Goal: Protect user data and control access to application features
Constraints: UK GDPR compliance, modern security standards, user-friendly experience
Security Level: Enhanced Security (business application with personal data)
Technology Context: Node.js + Express authentication middleware
Implementation Approach:
- JWT-based authentication with refresh token rotation
- bcrypt password hashing with minimum 12 rounds
- Rate limiting on authentication endpoints (5 attempts per 15 minutes)
- Secure session management with httpOnly cookies
Research Areas:
- Express.js JWT implementation patterns
- Passport.js integration strategies
- GDPR-compliant user data handling
- Security middleware configuration
Success Criteria:
- Secure user registration and login functionality
- Protection against common authentication vulnerabilities
- GDPR-compliant user data management
- Security audit trail for authentication events
```

### Additional Security-Specific Task Briefs

#### Security Infrastructure Setup
```
Task: Implement Security Infrastructure
Goal: Establish foundational security measures across the application
Constraints: Industry-standard security practices, minimal performance impact
Technology Context: [Based on chosen stack]
Implementation Approach:
- Security headers middleware (helmet.js for Node.js, equivalent for other stacks)
- Input validation library integration
- Environment variable management for secrets
- HTTPS configuration and certificate management
Research Areas:
- Security header configuration for [chosen technology]
- Environment variable security best practices
- HTTPS setup for [chosen hosting platform]
- Security testing tools and practices
```

#### Data Protection Implementation
```
Task: Implement Data Protection Measures
Goal: Ensure user data is properly protected and GDPR-compliant
Constraints: UK GDPR compliance, user privacy rights, secure data handling
Implementation Approach:
- Database encryption configuration
- Data retention and deletion policies
- User consent management (if required)
- Privacy policy and terms of service integration
Research Areas:
- [Chosen database] encryption options
- GDPR compliance implementation patterns
- User consent management libraries
- Privacy policy legal requirements for UK
```

## Phase 5: Security Testing and Validation Planning

### Security Testing Requirements
**Based on security level, define testing approaches:**

#### Basic Security Testing
- Automated dependency vulnerability scanning
- Basic penetration testing tools (OWASP ZAP)
- Input validation testing
- Authentication flow testing

#### Enhanced Security Testing
- Comprehensive security testing suite
- Regular dependency updates and monitoring
- Security code review processes
- Performance impact assessment of security measures

#### Compliance Security Testing
- Formal security assessment procedures
- Compliance audit preparation
- Penetration testing by qualified assessors
- Security incident response testing

## Phase 6: Security Documentation and Implementation Guidance

### Security Implementation Guide
**Generate technology-specific security implementation guidance:**

#### Development Security Practices
- Secure coding guidelines for chosen technology stack
- Security review checklist for code changes
- Common vulnerability prevention (OWASP Top 10)
- Security testing integration into development workflow

#### Deployment Security Configuration
- Production environment security hardening
- Secret management and environment configuration  
- Security monitoring and logging setup
- Incident response and security breach procedures

### Security Decision Documentation
```markdown
# Security Implementation Decisions

## Security Level: Enhanced Security
**Decision Date:** [Current Date]
**Reasoning:** Business application handling personal user data, public-facing
**Compliance Requirements:** UK GDPR compliance for EU users
**Technology Integration:** Node.js + Express security middleware stack

## Authentication Strategy: JWT with Refresh Tokens
**Decision Date:** [Current Date]
**Reasoning:** Stateless authentication suitable for API architecture, good security practices
**Implementation:** JWT access tokens (15 min) + refresh tokens (7 days)
**Security Measures:** Token rotation, secure storage, rate limiting

## Data Protection Approach: Database Encryption + HTTPS
**Decision Date:** [Current Date]
**Reasoning:** Personal data protection, GDPR compliance requirements
**Implementation:** PostgreSQL transparent data encryption, Let's Encrypt HTTPS
**Backup Strategy:** Encrypted backups, secure key management

[Continue for all security decisions...]
```

## Phase 7: Integration with Project Planning

### Security-Enhanced Project Structure
**Update project planning with security considerations:**
- Security-specific environment variables and configuration
- Security testing integration into task workflow
- Security review processes for code changes
- Compliance documentation and audit preparation

### Security Monitoring and Maintenance Planning
**Long-term security considerations:**
- Regular security update procedures
- Security monitoring and alerting setup
- Incident response procedures and contact information
- Security review and assessment schedule

## Output Deliverables

1. **Security Implementation Plan**: Comprehensive security approach with technology-specific guidance
2. **Enhanced Security Task Briefs**: Updated task briefs with detailed security context and constraints
3. **Security Configuration Guide**: Technology-specific security setup instructions
4. **Compliance Documentation**: GDPR, PCI-DSS, or other regulatory compliance guidance
5. **Security Testing Framework**: Testing approaches and tools appropriate for security level
6. **Security Operations Guide**: Ongoing security maintenance and monitoring procedures

## Meta-Documentation

This Security Planning wizard provides:
- **Risk-appropriate security measures** based on project requirements and context
- **Technology-integrated guidance** that works with chosen development stack
- **Compliance-aware recommendations** for regulatory requirements
- **Implementation-focused planning** that enhances rather than replaces existing task briefs

The key innovation is adaptive security planning that scales from basic protection for simple projects to comprehensive compliance for enterprise applications, while maintaining integration with existing project planning documents.