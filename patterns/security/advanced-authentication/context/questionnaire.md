# Advanced Authentication Pattern - Context Questionnaire

## Purpose
This questionnaire gathers the specific context needed to apply the Advanced Authentication Pattern optimally for your project. Your answers help determine the best authentication methods, security features, and implementation approach.

---

## Quick Context Assessment (2 minutes)

### Project Overview
1. **What type of application are you building/enhancing?**
   - [ ] Web application (SPA/traditional)
   - [ ] Mobile application (native/hybrid)
   - [ ] API service
   - [ ] Desktop application
   - [ ] Multi-platform (web + mobile)

2. **What's your primary authentication goal?**
   - [ ] Replace basic password authentication
   - [ ] Add modern authentication to existing app
   - [ ] Implement enterprise-grade security
   - [ ] Meet compliance requirements
   - [ ] Improve user experience while maintaining security

3. **Current authentication state:**
   - [ ] No authentication (anonymous app)
   - [ ] Basic username/password
   - [ ] JWT tokens only
   - [ ] Existing SSO integration
   - [ ] Legacy authentication system

---

## Detailed Context (5-10 minutes)

### User Base and Requirements

**4. Expected user base size:**
   - [ ] Small team/internal (1-50 users)
   - [ ] Small business (50-1,000 users) 
   - [ ] Medium scale (1,000-100,000 users)
   - [ ] Large scale (100,000+ users)
   - [ ] Enterprise/multi-tenant (variable scale)

**5. User technical sophistication:**
   - [ ] Technical users (developers, IT professionals)
   - [ ] Business users (comfortable with technology)
   - [ ] General consumers (mixed technical ability)
   - [ ] Non-technical users (elderly, accessibility needs)
   - [ ] Mixed user base

**6. Primary user authentication preference:**
   - [ ] Simple and fast (prioritize convenience)
   - [ ] Modern and secure (WebAuthn/passkeys)
   - [ ] Enterprise integration (SSO required)
   - [ ] Multiple options (let users choose)
   - [ ] Maximum security (regardless of complexity)

### Security and Compliance Context

**7. Security requirements level:**
   - [ ] Basic (protect against common attacks)
   - [ ] Standard (industry best practices)
   - [ ] High (financial/healthcare level)
   - [ ] Maximum (government/defense level)
   - [ ] Regulated (specific compliance required)

**8. Compliance requirements:** (Select all that apply)
   - [ ] None specific
   - [ ] GDPR (EU data protection)
   - [ ] HIPAA (US healthcare)
   - [ ] PCI-DSS (payment processing)
   - [ ] SOX (financial reporting)
   - [ ] FedRAMP (US government)
   - [ ] ISO 27001 (information security)
   - [ ] Other: ________________

**9. Risk tolerance:**
   - [ ] Security-first (maximum protection, accept UX complexity)
   - [ ] Balanced (good security with reasonable UX)
   - [ ] UX-focused (prioritize ease of use over maximum security)
   - [ ] Context-dependent (different levels for different users)

### Technical Context

**10. Backend technology:**
   - [ ] .NET Core/Framework
   - [ ] Node.js (Express, Fastify, etc.)
   - [ ] Python (Django, FastAPI, Flask)
   - [ ] Java (Spring Boot, etc.)
   - [ ] PHP (Laravel, Symfony, etc.)
   - [ ] Ruby on Rails
   - [ ] Go
   - [ ] Other: ________________

**11. Frontend technology:**
   - [ ] React
   - [ ] Vue.js
   - [ ] Angular
   - [ ] Vanilla JavaScript
   - [ ] Server-side rendered (Razor, EJS, etc.)
   - [ ] Mobile native (iOS/Android)
   - [ ] Cross-platform mobile (React Native, Flutter)
   - [ ] Other: ________________

**12. Deployment environment:**
   - [ ] Cloud (AWS, Azure, GCP)
   - [ ] On-premise servers
   - [ ] Hybrid (cloud + on-premise)
   - [ ] Edge computing
   - [ ] Container-based (Docker, Kubernetes)
   - [ ] Serverless (Lambda, Azure Functions)

### Organizational Context

**13. Team size and expertise:**
   - [ ] Solo developer (need simple, well-documented solutions)
   - [ ] Small team 2-5 (prefer proven patterns)
   - [ ] Medium team 5-15 (can handle moderate complexity)
   - [ ] Large team 15+ (can implement complex solutions)
   - [ ] Multiple teams (need standardized approaches)

**14. Authentication/security expertise:**
   - [ ] Beginner (new to authentication patterns)
   - [ ] Some experience (implemented basic auth before)
   - [ ] Experienced (familiar with JWT, OAuth)
   - [ ] Expert (deep security knowledge)
   - [ ] Mixed expertise across team

**15. Maintenance capacity:**
   - [ ] Minimal (want set-and-forget solutions)
   - [ ] Standard (regular updates and monitoring)
   - [ ] Comprehensive (dedicated security team)

**16. Third-party service preference:**
   - [ ] Self-hosted only (no external dependencies)
   - [ ] Open to managed services (Auth0, Azure AD)
   - [ ] Prefer managed services (reduce operational overhead)
   - [ ] Hybrid approach okay

---

## Feature-Specific Context (3-5 minutes)

### Authentication Methods

**17. Which authentication methods do you want to support?** (Select all desired)
   - [ ] Traditional passwords (with strong requirements)
   - [ ] WebAuthn/Passkeys (modern passwordless)
   - [ ] Biometric authentication (fingerprint, face, etc.)
   - [ ] Multi-factor authentication (SMS, TOTP, push)
   - [ ] Social login (Google, Microsoft, GitHub)
   - [ ] Enterprise SSO (SAML, OpenID Connect)
   - [ ] Magic links (email-based passwordless)
   - [ ] Hardware security keys (YubiKey, etc.)

**18. Multi-factor authentication requirements:**
   - [ ] Not required (optional for users)
   - [ ] Required for admin users only
   - [ ] Required for all users
   - [ ] Risk-based (adaptive MFA)
   - [ ] Configurable by organization/tenant

**19. Single Sign-On (SSO) needs:**
   - [ ] Not needed
   - [ ] Internal SSO (across your applications)
   - [ ] External SSO (integrate with customer identity providers)
   - [ ] Both internal and external SSO
   - [ ] Social login providers only

### Advanced Features

**20. Advanced security features needed:** (Select all desired)
   - [ ] Risk-based authentication (unusual location/device detection)
   - [ ] Device trust management
   - [ ] Session management (concurrent session limits)
   - [ ] Account lockout policies
   - [ ] Password history and rotation
   - [ ] Audit logging and monitoring
   - [ ] Threat detection and response
   - [ ] Zero-trust architecture support

**21. User experience features:** (Select all desired)
   - [ ] Remember device/trusted devices
   - [ ] Progressive authentication (step-up when needed)
   - [ ] Self-service account recovery
   - [ ] User profile management
   - [ ] Privacy controls and consent management
   - [ ] Account linking (multiple providers)
   - [ ] Guest/anonymous access options

---

## Implementation Context (2-3 minutes)

### Timeline and Constraints

**22. Implementation timeline:**
   - [ ] Urgent (need basic auth ASAP, enhance later)
   - [ ] Standard (2-4 weeks for full implementation)
   - [ ] Comprehensive (6-8 weeks for advanced features)
   - [ ] Phased (implement core first, add features incrementally)

**23. Budget/resource constraints:**
   - [ ] Minimal budget (prefer open-source solutions)
   - [ ] Standard budget (can use some paid services)
   - [ ] Flexible budget (best solution regardless of cost)
   - [ ] Enterprise budget (premium solutions acceptable)

**24. Existing infrastructure integration needs:**
   - [ ] Must integrate with existing user database
   - [ ] Must work with current API architecture
   - [ ] Must support existing mobile apps
   - [ ] Must integrate with current monitoring/logging
   - [ ] Green field (no existing constraints)

### Success Criteria

**25. Primary success metrics:** (Select top 3)
   - [ ] Security (no authentication-related breaches)
   - [ ] User experience (reduced authentication friction)
   - [ ] Compliance (meet regulatory requirements)
   - [ ] Performance (fast authentication response)
   - [ ] Scalability (handle user growth)
   - [ ] Maintainability (easy to operate and update)
   - [ ] Cost effectiveness (reasonable operational costs)

---

## Additional Context

**26. Any specific requirements, constraints, or concerns not covered above?**
```
[Free text field for additional context]
```

**27. Are there any existing authentication systems or patterns you want to avoid or specifically emulate?**
```
[Free text field for positive/negative examples]
```

---

## Context Summary

Based on your responses, I'll provide:

1. **Recommended Authentication Architecture** - Specific authentication methods and security features for your context
2. **Implementation Plan** - Step-by-step approach considering your timeline and constraints
3. **Technology Recommendations** - Specific libraries, services, and patterns for your tech stack
4. **Security Configuration** - Security settings and policies appropriate for your risk level
5. **Integration Strategy** - How to integrate with your existing systems and infrastructure

**Estimated Time to Complete Questionnaire: 10-15 minutes**
**Context Processing Time: 2-3 minutes**
**Detailed Recommendations Delivery: 5-10 minutes**