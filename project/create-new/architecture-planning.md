# Architecture Planning Wizard

## Overview
Analyses PRD requirements, technology selections, and security planning to recommend appropriate software architecture patterns. Enhances task briefs with architectural constraints and generates architecture-specific implementation guidance.

## Phase 1: Architecture Requirements Analysis

### PRD Architecture Trigger Detection
**Scan PRD, task briefs, and technology selections for architectural indicators:**

**Complexity Indicators:**
- "multiple features", "various functions" → Modular architecture needed
- "different user types", "roles" → Separation of concerns important
- "integrations", "third-party services" → Integration layer architecture
- "reporting", "analytics" → Data access layer considerations

**Scale Indicators:**
- "many users", "thousands", "public" → Scalability architecture patterns
- "real-time", "live updates" → Event-driven or real-time architecture
- "high performance", "fast response" → Performance-optimised patterns
- "global", "multi-region" → Distributed systems considerations

**Team Indicators:**
- Single developer or small team → Monolith-first approach
- Growing team mentioned → Modular monolith preparation
- Large team or distributed team → Microservices consideration
- Multiple specialties → Domain-driven design patterns

**Business Indicators:**
- "startup", "MVP" → Simple, evolvable architecture
- "enterprise", "business-critical" → Robust, maintainable patterns
- "prototype", "POC" → Quick development, simple deployment
- "long-term", "scalable business" → Future-proofing considerations

## Phase 2: Architecture Pattern Recommendation

### Pattern Selection Logic

#### Monolith-First Architecture
**Recommended When:**
- Single developer or team of 2-5 people
- Simple to moderate complexity requirements
- Fast development and deployment priority
- Uncertain requirements that may evolve

**Architecture Characteristics:**
```
Architecture Pattern: Modular Monolith
Reasoning: Team size and requirements uncertainty favour simple deployment with clear module boundaries
Implementation Approach:
- Single deployment unit with modular internal structure
- Clear separation between presentation, business logic, and data layers
- Module boundaries aligned with business domains
- Database-per-module pattern within single database instance

Technology Integration: [Based on chosen stack]
- Frontend and backend in same deployment
- Shared database with logical separation
- Simple CI/CD pipeline
- Environment-based configuration
```

#### Microservices-Ready Architecture
**Recommended When:**
- Team size 8+ people or growing rapidly
- Complex domain with distinct business areas
- High scalability requirements
- Strong DevOps capabilities present

**Architecture Characteristics:**
```
Architecture Pattern: Domain-Driven Microservices
Reasoning: Team size and domain complexity benefit from service boundaries aligned with business capabilities
Implementation Approach:
- Services organised around business capabilities
- Database-per-service pattern
- API-first design with clear service contracts
- Event-driven communication where appropriate

Technology Integration: [Based on chosen stack]
- Containerised service deployment
- API gateway for external communication
- Service mesh for internal communication
- Distributed monitoring and logging
```

#### Event-Driven Architecture
**Recommended When:**
- Real-time features or live updates required
- Complex business processes with multiple steps
- High throughput or performance requirements
- Asynchronous processing needs identified

**Architecture Characteristics:**
```
Architecture Pattern: Event-Driven with Command Query Responsibility Segregation (CQRS)
Reasoning: Real-time requirements and complex data flows benefit from event-based communication
Implementation Approach:
- Event sourcing for critical business events
- Separate read and write models for performance
- Message queues for asynchronous processing
- Event store for audit trail and replay capability

Technology Integration: [Based on chosen stack]
- Message broker integration (Redis, RabbitMQ, or cloud equivalent)
- Event store implementation
- CQRS pattern with read/write separation
- Real-time communication layer (WebSockets, Server-Sent Events)
```

#### Serverless Architecture
**Recommended When:**
- Variable or unpredictable load patterns
- Cost optimisation important
- Minimal operational overhead preferred
- Event-driven or API-centric functionality

**Architecture Characteristics:**
```
Architecture Pattern: Serverless with Backend-as-a-Service (BaaS)
Reasoning: Variable load and operational simplicity favour serverless approach
Implementation Approach:
- Function-based backend implementation
- Managed database and authentication services
- Static frontend with API integration
- Event-driven function orchestration

Technology Integration: [Based on chosen stack]
- Cloud function deployment (AWS Lambda, Vercel Functions, etc.)
- Managed services for database, authentication, file storage
- CDN for static asset delivery
- Serverless framework for deployment automation
```

## Phase 3: Architecture Decision Presentation

### Decision Presentation with Trade-offs
```
"Based on your PRD analysis, technology selections, and team context, here's my architecture recommendation:

🏗️ RECOMMENDED: Modular Monolith Architecture
   Reasoning: Team size (2-3 people), moderate complexity, rapid development needs
   Benefits: Simple deployment, fast development, easy debugging and testing
   Trade-offs: Scaling requires more planning, technology stack lock-in initially
   
   Implementation Approach:
   - Clear module boundaries (User Management, Core Features, External Integrations)
   - Layered architecture (Presentation → Business Logic → Data Access)
   - Single database with logical separation
   - Simple CI/CD with single deployment artifact

Alternative architectures considered:
   
⚡ Microservices: Excellent for scaling teams, but operational overhead too high for current team size
💫 Event-Driven: Perfect for real-time features, but adds complexity not justified by current requirements
☁️ Serverless: Great for cost optimisation, but vendor lock-in concerns for business-critical application

Evolution Path:
Your chosen architecture can evolve as requirements change:
- Module boundaries prepare for future service extraction
- Database design allows for service-per-database migration
- API design enables frontend/backend separation when needed

Would you like to discuss this recommendation or explore alternative approaches?"
```

## Phase 4: Architecture Implementation Planning

### Detailed Architecture Guidelines

#### Module Structure Definition
```
Architecture Implementation: Modular Monolith Structure
Application Modules:
- User Management Module: Authentication, authorisation, user profiles
- Core Business Module: Primary application functionality
- Integration Module: External service connections and data exchange
- Shared Infrastructure Module: Logging, configuration, utilities

Module Communication:
- Direct method calls within modules
- Well-defined interfaces between modules
- Shared data access through repository patterns
- Event notifications for cross-module communication when needed
```

#### Data Architecture Strategy
```
Data Architecture: Single Database with Logical Separation
Database Design:
- Schema-per-module approach within single PostgreSQL instance
- Foreign key relationships only within module boundaries
- Shared reference data in common schema
- Migration strategy supporting module-based changes

Data Access Patterns:
- Repository pattern for data access abstraction
- Unit of Work pattern for transaction management
- Query objects for complex read operations
- Event publishing for data change notifications
```

#### API Design Strategy
```
API Architecture: RESTful with GraphQL Consideration
API Design Principles:
- Resource-based REST endpoints aligned with business capabilities
- Consistent error handling and response formats
- API versioning strategy for future evolution
- Authentication and authorisation middleware

Future Evolution Support:
- API design supports service extraction
- Backend-for-Frontend pattern if multiple client types develop
- GraphQL consideration for complex query requirements
- Rate limiting and abuse prevention built-in
```

## Phase 5: Architecture Task Brief Enhancement

### Enhanced Task Briefs with Architecture Context

**Original Task Brief:**
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Technology Context: React + TypeScript, Material-UI component library
Research Areas: React component patterns, accessibility with Material-UI
```

**Enhanced with Architecture Planning:**
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Technology Context: React + TypeScript, Material-UI component library
Architecture Context: Modular Monolith - Core Business Module
Module Boundaries:
- Clear separation between UI components and business logic
- API client layer for backend communication
- State management aligned with module structure
- Component organisation supporting future service extraction

Implementation Approach:
- Feature-based component organisation aligned with business capabilities
- Custom hooks for business logic abstraction
- API client with consistent error handling
- State management patterns supporting module evolution

Research Areas:
- React component patterns for modular architecture
- State management patterns (Context API vs Redux vs Zustand)
- API client patterns and error handling
- Component testing strategies for modular design

Architecture Dependencies:
- User Management Module (authentication state)
- Integration Module (external data requirements)
- Shared Infrastructure Module (logging, error handling)
```

### Architecture-Specific Task Briefs

#### Application Structure Setup
```
Task: Establish Application Architecture Structure
Goal: Create foundational architecture structure supporting modular development
Constraints: Clear module boundaries, future evolution support, maintainable code organisation
Architecture Pattern: Modular Monolith
Implementation Approach:
- Directory structure aligned with module boundaries
- Dependency injection setup for module communication
- Configuration management supporting multiple environments
- Development workflow supporting modular development

Module Structure:
/src
  /modules
    /user-management
    /core-business
    /integrations
    /shared-infrastructure
  /api
  /config
  /tests

Research Areas:
- Module organisation patterns for [chosen technology stack]
- Dependency injection implementation
- Configuration management best practices
- Development tooling for modular architecture
```

#### Data Layer Architecture
```
Task: Implement Data Access Architecture
Goal: Create data access layer supporting module boundaries and future evolution
Constraints: Performance, maintainability, module separation, transaction consistency
Architecture Pattern: Repository + Unit of Work
Implementation Approach:
- Repository pattern for each module's data access
- Unit of Work for transaction management across modules
- Migration strategy supporting module-based changes
- Query optimisation aligned with access patterns

Database Organisation:
- Schema per module within single database
- Foreign keys only within module boundaries
- Shared reference data in common schema
- Audit trail support for compliance requirements

Research Areas:
- Repository pattern implementation for [chosen database]
- Transaction management across module boundaries
- Database migration strategies
- Query optimisation and performance monitoring
```

## Phase 6: Architecture Evolution Planning

### Future Architecture Considerations

#### Evolution Triggers and Pathways
```
Architecture Evolution Planning:
Current State: Modular Monolith
Evolution Triggers:
- Team growth beyond 8-10 developers → Consider service extraction
- Performance bottlenecks in specific modules → Micro-frontend or service extraction
- Different scaling requirements per module → Selective service deployment
- Technology diversity needs → Service-based technology choices

Evolution Pathways:
1. Module to Microservice: Extract specific modules as independent services
2. Database Separation: Migrate to database-per-service as modules become services
3. API Gateway: Introduce API gateway as service count increases
4. Event-Driven: Add event-driven communication for complex workflows

Preparation for Evolution:
- Module boundaries align with potential service boundaries
- API design supports service extraction
- Database schema design supports service separation
- Monitoring and logging support distributed system needs
```

### Architecture Testing Strategy
```
Architecture Testing Approach:
Testing Strategy: Module-Aware Testing Pyramid
Implementation:
- Unit tests within module boundaries
- Integration tests for module communication
- Contract tests for API boundaries
- End-to-end tests for critical user journeys

Architecture-Specific Testing:
- Module boundary enforcement tests
- API contract validation
- Database constraint testing
- Performance testing for module interaction patterns

Research Areas:
- Testing patterns for modular architecture
- Contract testing implementation
- Performance testing tools and practices
- Architecture fitness function implementation
```

## Phase 7: Architecture Documentation and Guidelines

### Architecture Decision Records (ADRs)
```markdown
# Architecture Decision Record: ADR-001 - Application Architecture Pattern

## Status: Accepted
**Date:** [Current Date]
**Decision Makers:** [Team/Stakeholder Names]

## Context
We need to choose an application architecture pattern that supports:
- Team size of 2-3 developers with potential for growth
- Moderate complexity requirements with integration needs
- Rapid development and deployment requirements
- Future evolution as requirements and team grow

## Decision
We will implement a Modular Monolith architecture pattern.

## Rationale
- Team size favours simple deployment and debugging
- Module boundaries prepare for future service extraction
- Technology stack choice supports this pattern well
- Development speed prioritised over distributed system benefits

## Consequences
**Positive:**
- Faster initial development and deployment
- Easier debugging and testing
- Simple operational model
- Clear module boundaries support code organisation

**Negative:**
- Scaling requires more planning than microservices
- Technology stack changes affect entire application
- Module discipline required to maintain boundaries

## Evolution Strategy
Module boundaries designed to support future service extraction when team size and requirements justify distributed architecture.
```

### Architecture Implementation Guide
**Generate architecture-specific implementation guidance:**
- Module organisation and communication patterns
- Data access patterns and database organisation
- API design principles and evolution support
- Testing strategies for modular architecture
- Deployment and operational considerations
- Architecture evolution triggers and pathways

## Output Deliverables

1. **Architecture Design Document**: Comprehensive architecture pattern with implementation guidance
2. **Enhanced Architecture Task Briefs**: Updated task briefs with architectural context and constraints
3. **Architecture Decision Records**: Documented decisions with reasoning and evolution planning
4. **Implementation Guidelines**: Architecture-specific development patterns and practices
5. **Evolution Planning**: Future architecture considerations and migration pathways
6. **Testing Strategy**: Architecture-aware testing approaches and tools

## Integration with Project Planning

### Architecture-Enhanced Project Structure
**Update project planning with architectural considerations:**
- Module-based task organisation and dependencies
- Architecture-specific development workflow
- Testing strategy aligned with architectural patterns
- Deployment procedures supporting chosen architecture
- Monitoring and operational considerations

### Long-term Architecture Considerations
**Architecture maintenance and evolution:**
- Regular architecture review and fitness function evaluation
- Architecture evolution triggers and decision criteria
- Team structure alignment with architectural boundaries
- Technology evolution and architecture adaptation planning

## Meta-Documentation

This Architecture Planning wizard provides:
- **Context-appropriate architecture patterns** based on team size, complexity, and requirements
- **Evolution-aware recommendations** that support future growth and change
- **Technology-integrated guidance** that works seamlessly with chosen development stack
- **Implementation-focused planning** that enhances existing task briefs with architectural context

The key innovation is adaptive architecture planning that scales from simple monoliths for small teams to complex distributed systems for large organisations, while maintaining clear evolution pathways and integration with existing project planning.