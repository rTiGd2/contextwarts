# Project Orchestrator Wizard

## Overview
Final orchestration wizard that coordinates all project creation components, generates comprehensive implementation prompts, and creates a self-contained project ready for development.

## Phase 1: Project Creation Workflow

### Complete Workflow Orchestration
```
Project Creation Sequence:
1. Enhanced PRD Creation → Comprehensive project requirements
2. Master Task Analysis → High-level task briefs with goals and constraints
3. Conditional Capture Sessions:
   - Technology Selection (if technical decisions needed)
   - Security Planning (if security requirements detected)
   - Architecture Planning (if architectural decisions needed)
4. Final Task Brief Enhancement → Context-rich implementation guidance
5. Implementation Prompt Generation → Self-contained project ready for development
```

### Intelligent Workflow Management
**Based on PRD analysis, determine required capture sessions:**

```
"Project creation workflow planned:

✅ COMPLETED: Enhanced PRD Creation
   → Comprehensive requirements with intelligent section recommendations

✅ COMPLETED: Master Task Analysis  
   → [N] high-level task briefs created with goals and constraints

🔍 REQUIRED: Technology Selection Session
   → Technical decisions needed for [specific requirements from PRD]

🔍 REQUIRED: Security Planning Session
   → Security requirements detected: [specific triggers]

⚠️ RECOMMENDED: Architecture Planning Session
   → [reasoning based on complexity/team size/requirements]

Total estimated time: [X] hours for complete project setup
Shall we proceed with the required sessions?"
```

## Phase 2: Context Integration and Enhancement

### Progressive Task Brief Enhancement
**Track how task briefs evolve through each capture session:**

#### Initial Task Brief (From Master Task Analysis)
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Research Areas: UI framework selection, user experience patterns
Dependencies: User authentication, data storage setup
```

#### After Technology Selection
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Technology Context: React + TypeScript, Material-UI component library
Research Areas: React component patterns, Material-UI accessibility practices
Implementation Notes: Focus on reusable components, proper TypeScript typing
```

#### After Security Planning
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design, GDPR compliance
Technology Context: React + TypeScript, Material-UI component library
Security Context: JWT authentication integration, secure API communication
Research Areas: React component patterns, Material-UI accessibility, secure authentication flows
Implementation Notes: Focus on reusable components, secure state management, audit trail integration
```

#### After Architecture Planning
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design, GDPR compliance
Technology Context: React + TypeScript, Material-UI component library
Security Context: JWT authentication integration, secure API communication
Architecture Context: Modular Monolith - Core Business Module
Module Boundaries: Clear separation between UI components and business logic
Implementation Notes: Feature-based organisation, API client layer, state management aligned with module structure
Research Areas: React modular patterns, JWT integration, Material-UI theming, component testing strategies
Dependencies: User Management Module (authentication), Integration Module (external data)
```

### Context Synthesis
**Create comprehensive implementation context from all capture sessions:**

#### Technology Context Summary
- Complete technology stack with reasoning
- Integration patterns and communication strategies
- Development tools and build configuration
- Deployment and hosting approach

#### Security Context Summary
- Security level and compliance requirements
- Authentication and authorisation approach
- Data protection and privacy measures
- Security testing and validation procedures

#### Architecture Context Summary
- Chosen architecture pattern with trade-offs
- Module organisation and boundaries
- Data architecture and access patterns
- Evolution planning and future considerations

## Phase 3: Final Implementation Prompt Generation

### Comprehensive Implementation Prompts
**Generate self-contained prompts for each enhanced task brief:**

#### Example Implementation Prompt
```markdown
# Implementation Prompt: Core User Features

## Context Loading Instructions
Load the following context before beginning implementation:
- Project PRD: `/prd-[project-name].md`
- Technology Decisions: `/.aiwizard/technology-decisions.md`
- Security Requirements: `/.aiwizard/security-requirements.md`
- Architecture Guidelines: `/.aiwizard/architecture-decisions.md`

## Task Overview
**Goal:** Enable users to perform primary actions identified in PRD
**Module:** Core Business Module (Modular Monolith Architecture)
**Technology Stack:** React + TypeScript + Material-UI + Node.js + Express + PostgreSQL

## Implementation Requirements

### Functional Requirements
[Derived from PRD functional requirements with task-specific focus]
1. User story implementation with specific acceptance criteria
2. Component structure aligned with module boundaries
3. API integration patterns for backend communication
4. State management following architectural guidelines

### Technical Constraints
- **Language/Framework:** React 18+ with TypeScript, Material-UI v5+
- **Code Quality:** ESLint + Prettier configuration, 80%+ test coverage
- **Performance:** Component lazy loading, memo optimization where appropriate
- **Accessibility:** WCAG 2.1 AA compliance, keyboard navigation support

### Security Constraints
- **Authentication:** JWT token integration with automatic renewal
- **Data Validation:** Client-side validation with server-side verification
- **API Security:** Secure HTTP client with error handling and retry logic
- **Privacy:** GDPR-compliant user data handling, audit trail integration

### Architecture Constraints
- **Module Structure:** /src/modules/core-business/components structure
- **Component Organisation:** Feature-based folders aligned with business capabilities
- **State Management:** Context API for module state, React Query for server state
- **API Layer:** Abstracted API client with consistent error handling

## Research Areas
Before implementation, research current best practices for:
1. **React Patterns:** Modern component patterns, custom hooks for business logic
2. **Material-UI Integration:** Theme customisation, component overrides
3. **TypeScript Patterns:** Proper typing for React components and API responses
4. **Testing Strategies:** Component testing with React Testing Library
5. **Performance Optimisation:** Bundle splitting, component optimisation

## Implementation Approach
1. **Setup Module Structure:** Create directory structure aligned with architecture
2. **Implement Core Components:** Build reusable components following design system
3. **Integrate Authentication:** Connect with User Management Module authentication
4. **API Integration:** Implement API client with error handling and loading states
5. **State Management:** Setup Context API for component state management
6. **Testing Implementation:** Unit and integration tests for all components
7. **Performance Optimisation:** Implement lazy loading and optimisation patterns

## Success Criteria
- [ ] All user stories from PRD are implementable with created components
- [ ] Authentication integration works seamlessly with User Management Module
- [ ] API communication follows security and error handling requirements
- [ ] Component structure supports future service extraction (architecture evolution)
- [ ] Test coverage meets quality requirements (80%+)
- [ ] Performance metrics meet requirements (< 2s initial load, < 500ms interactions)
- [ ] Accessibility compliance verified with automated and manual testing

## Dependencies
- **User Management Module:** Authentication state and user context
- **Integration Module:** External data requirements and API specifications
- **Shared Infrastructure Module:** Logging, error handling, configuration utilities

## Architecture Evolution Notes
Component structure and API design prepared for future service extraction:
- Clear module boundaries with well-defined interfaces
- API client abstraction supporting service-based communication
- State management patterns compatible with distributed state management
- Component organisation aligned with potential service boundaries

## Files to be Created/Modified
Based on technology and architecture decisions:
- `/src/modules/core-business/components/` - React component implementation
- `/src/modules/core-business/hooks/` - Custom hooks for business logic
- `/src/modules/core-business/api/` - API client and data fetching logic
- `/src/modules/core-business/types/` - TypeScript interfaces and types
- `/src/modules/core-business/tests/` - Component and integration tests
- `/src/modules/core-business/index.ts` - Module public interface

## Next Steps After Implementation
1. Integration testing with User Management Module
2. End-to-end testing for complete user workflows
3. Performance testing and optimisation
4. Security testing and vulnerability assessment
5. Accessibility audit and remediation
```

### Project Setup Prompts
**Create comprehensive project initialisation prompts:**

#### Development Environment Setup
```markdown
# Development Environment Setup Prompt

## Technology Stack Installation
Based on your technology decisions, set up the following development environment:

### Required Tools
- Node.js 18+ (LTS version recommended)
- npm 8+ or yarn 1.22+
- Git 2.34+
- VS Code (recommended) with extensions:
  - TypeScript and JavaScript Language Features
  - ESLint
  - Prettier
  - Material-UI Snippets

### Project Initialisation
```bash
# Create project structure
npx create-react-app [project-name] --template typescript
cd [project-name]

# Install additional dependencies based on technology decisions
npm install @mui/material @emotion/react @emotion/styled
npm install @mui/icons-material
npm install axios react-query
npm install --save-dev @testing-library/jest-dom

# Setup project structure aligned with modular architecture
mkdir -p src/modules/{user-management,core-business,integrations,shared-infrastructure}
mkdir -p src/api src/config src/types
```

### Configuration Files
[Generate specific configuration files based on technology stack]
- TypeScript configuration
- ESLint and Prettier setup
- Package.json scripts
- Environment variable templates
- Docker configuration (if chosen)
```

### Deployment Setup Prompts
**Create deployment-ready configuration:**

#### Production Deployment Guide
```markdown
# Production Deployment Setup

## Infrastructure Requirements
Based on your technology and architecture decisions:

### Hosting Configuration
- **Frontend:** [Chosen hosting platform] configuration
- **Backend:** [Chosen hosting platform] configuration  
- **Database:** [Chosen database] setup and configuration
- **Environment Variables:** Secure configuration management

### Security Configuration
- HTTPS certificate setup
- Security headers configuration
- Database encryption setup
- Authentication service configuration

### Monitoring and Logging
- Application performance monitoring
- Error tracking and alerting
- Security monitoring and audit logging
- Business metrics and analytics tracking
```

## Phase 4: Project Package Creation

### Self-Contained Project Structure
**Generate complete project package:**

```
/[project-name]/
├── README.md                           # Project overview and setup instructions
├── prd-[project-name].md              # Complete PRD with all sections
├── .aiwizard/
│   ├── qa-sessions/
│   │   ├── prd-creation.md
│   │   ├── technology-selection.md
│   │   ├── security-planning.md
│   │   └── architecture-planning.md
│   ├── decisions/
│   │   ├── technology-decisions.md
│   │   ├── security-decisions.md
│   │   └── architecture-decisions.md
│   ├── research/
│   │   └── [any research conducted during planning]
│   └── implementation-prompts/
│       ├── setup-instructions.md
│       ├── task-1-core-features.md
│       ├── task-2-user-security.md
│       ├── task-N-[task-name].md
│       ├── deployment-guide.md
│       └── testing-strategy.md
├── tasks/
│   └── master-task-list.md
└── docs/
    ├── technology-decisions.md
    ├── security-requirements.md
    ├── architecture-overview.md
    └── evolution-planning.md
```

### Project Portability Features
**Ensure project can be moved and used independently:**

#### Standalone Implementation Capability
- All implementation prompts are self-contained
- Context loading instructions reference local files
- No dependencies on wizard system for implementation
- Clear setup and deployment instructions

#### Version Control Ready
- `.gitignore` appropriate for chosen technology stack
- README with comprehensive setup instructions
- Contribution guidelines aligned with architecture decisions
- Issue templates for bug reports and feature requests

## Phase 5: Final Project Delivery

### Project Handoff Documentation
```markdown
# Project Creation Complete

## What Has Been Created
✅ **Comprehensive PRD:** [prd-[project-name].md]
✅ **Technology Stack:** Complete technology decisions with reasoning
✅ **Security Planning:** [Security level] with [compliance requirements]
✅ **Architecture Design:** [Architecture pattern] with evolution planning
✅ **Implementation Prompts:** [N] detailed task briefs ready for development

## Project Structure
Your project is now self-contained in `/[project-name]/` directory with:
- Complete requirements and planning documentation
- Technology-specific setup instructions  
- Detailed implementation prompts for each task
- Security and compliance guidelines
- Architecture documentation and evolution planning

## Next Steps
1. **Setup Development Environment:** Follow `/.aiwizard/implementation-prompts/setup-instructions.md`
2. **Begin Implementation:** Start with Task 1 using provided implementation prompts
3. **Follow Architecture Guidelines:** Maintain module boundaries and patterns
4. **Security Implementation:** Follow security requirements throughout development
5. **Testing Strategy:** Implement testing as specified in task briefs

## Implementation Support
Each task has a detailed implementation prompt in `/.aiwizard/implementation-prompts/` containing:
- Complete context and requirements
- Technology-specific guidance
- Security and architecture constraints
- Research areas for current best practices
- Success criteria and testing requirements

## Project Evolution
Your project is designed for evolution:
- Architecture supports future scaling and team growth
- Technology choices enable enhancement and integration
- Security implementation supports compliance and trust
- Documentation enables knowledge transfer and maintenance

The project is now ready for development with no dependencies on the wizard system.
```

### Success Metrics and Validation
**Define success criteria for project creation process:**

#### Process Quality Metrics
- Time from start to complete project setup
- Number of questions required for complete context
- Quality of generated implementation prompts
- Completeness of project documentation

#### Project Quality Metrics  
- PRD completeness and clarity
- Technology decision appropriateness
- Security requirement coverage
- Architecture pattern suitability
- Implementation prompt detail and clarity

## Meta-Documentation

This Project Orchestrator provides:
- **Complete workflow orchestration** from PRD through implementation-ready project
- **Progressive context enhancement** maintaining consistency across all planning phases
- **Self-contained project generation** with no ongoing wizard system dependencies
- **Portable project structure** enabling sharing, archiving, and independent development

The key innovation is creating a comprehensive project planning system that generates everything needed for implementation while maintaining clean separation between planning and execution phases.