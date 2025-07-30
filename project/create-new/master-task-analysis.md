# Master Task Analysis Wizard

## Overview
Analyses your PRD to create high-level task mini-briefs with goals and constraints, determining what additional capture sessions are needed for detailed implementation.

## Purpose
Create **Goal + Constraints** task structure that provides enough context for effective implementation without locking in premature technical decisions.

## Phase 1: PRD Analysis

### Automatic PRD Scanning
**Analyse PRD for capability requirements:**

**Core Functionality Triggers:**
- User interface needs → UI/UX task brief
- Data storage requirements → Data management task brief
- User authentication → Security implementation task brief
- External integrations → Integration task brief
- Business logic → Core functionality task brief

**Technical Context Triggers:**
- Performance requirements → Performance optimization considerations
- Scalability mentions → Architecture planning needs
- Security requirements → Security capture session needed
- Compliance mentions → Regulatory constraint analysis needed
- Integration needs → Technology selection capture needed

## Phase 2: Master Task Brief Creation

### Task Brief Structure
```
Task [N]: [Goal Statement]
Goal: [What we're trying to achieve - the outcome]
Constraints: [Boundary conditions, standards, limitations]
Context: [Relevant PRD sections, stakeholder needs]
Research Areas: [What needs investigation before implementation]
Success Criteria: [How we'll know it's working]
Dependencies: [What other tasks this relies on]
```

### Example Task Briefs

#### Core Functionality Task
```
Task 1: Implement Core User Features
Goal: Enable users to perform the primary actions identified in the PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Context: PRD functional requirements sections 3.1-3.4
Research Areas: UI framework selection, user experience patterns
Success Criteria: All core user stories can be completed successfully
Dependencies: User authentication (if required), data storage setup
```

#### Security Implementation Task
```
Task 2: Establish User Security
Goal: Protect user data and control access to application features
Constraints: UK GDPR compliance, modern security standards, user-friendly experience
Context: PRD mentioned user accounts and personal data handling
Research Areas: Authentication patterns, data protection best practices
Success Criteria: Secure user registration, login, and data protection
Dependencies: Technology stack selection, database setup
```

#### Integration Task
```
Task 3: Enable External Connectivity
Goal: Connect with third-party services as specified in PRD
Constraints: Reliable error handling, secure API communication, maintainable code
Context: PRD sections mentioning external services and data sources
Research Areas: API patterns, error handling strategies, authentication methods
Success Criteria: Reliable data exchange with external systems
Dependencies: Core application framework, security implementation
```

## Phase 3: Capture Session Recommendations

### Intelligent Session Planning
Based on task briefs created, recommend additional capture sessions:

```
"Based on your PRD analysis, I've created [N] high-level task briefs. 

To provide you with the best implementation guidance, I recommend these additional capture sessions:

🔍 REQUIRED: Technology Selection Session
   → Multiple technical decisions needed across task briefs
   → Will research current best practices for your specific needs

🔍 REQUIRED: Security Planning Session  
   → User data and authentication requirements identified
   → Will ensure compliance and modern security practices

⚠️ RECOMMENDED: Architecture Planning Session
   → Integration and scalability considerations present
   → Will help structure application for maintainability

❌ SKIPPING: Mobile-Specific Planning
   → No mobile-specific requirements detected in PRD

Would you like to run these capture sessions now, or proceed with the current task briefs and enhance them later?"
```

## Phase 4: Flexible Task Enhancement

### Iterative Refinement Capability
- **Task briefs can be enhanced** as capture sessions provide more context
- **Research areas get populated** with specific findings
- **Constraints get refined** based on technical discoveries
- **Dependencies get clarified** as architecture emerges

### Enhancement Example
```
ORIGINAL TASK BRIEF:
Task 1: Implement Core User Features
Research Areas: UI framework selection, user experience patterns

ENHANCED AFTER TECHNOLOGY CAPTURE:
Task 1: Implement Core User Features  
Research Areas: React component patterns, Material-UI best practices
Technology Context: React + TypeScript, Material-UI component library
Implementation Notes: Focus on reusable components, accessibility compliance
```

## Phase 5: Task Brief Delivery

### Output Structure
1. **Master Task List**: High-level briefs with goals and constraints
2. **Capture Recommendations**: Which additional sessions would enhance implementation
3. **Research Agenda**: Key areas to investigate during implementation
4. **Dependency Map**: Task interdependencies and suggested order
5. **Enhancement Path**: How task briefs will evolve with additional context

### Integration Points
- **Captures enhance task briefs**: Technology/Architecture/Security sessions add context
- **Task briefs guide captures**: Research areas inform what to investigate
- **Flexible refinement**: Task briefs evolve as understanding improves
- **Implementation freedom**: Enough guidance without premature technical lock-in

## Key Benefits

### For Implementation
- **Clear intent** without premature technical decisions
- **Research guidance** for current best practices
- **Constraint awareness** for compliance and quality
- **Flexibility** to adapt as understanding improves

### For Context Management
- **Minimal bloat**: High-level guidance, not detailed specifications  
- **Focused research**: Specific areas to investigate when needed
- **Adaptive structure**: Can incorporate new information without rebuilding
- **Clear boundaries**: Constraints provide guardrails without over-specification

## Meta-Documentation

This Master Task Analysis approach solves the classic project management tension between:
- **Enough guidance** to ensure quality and compliance
- **Sufficient flexibility** to adapt to discoveries and current best practices
- **Context efficiency** to avoid overwhelming detail and premature optimization
- **Research integration** to leverage current knowledge when implementing

The task brief structure provides mini-briefs that give context for effective research and implementation while maintaining adaptability as project understanding evolves.