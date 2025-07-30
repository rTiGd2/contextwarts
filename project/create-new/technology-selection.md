# Technology Selection Wizard

## Overview
Analyses PRD requirements and task briefs to recommend appropriate technology stack with constraints and implementation guidance. Creates technology decisions that enhance task briefs without over-specifying implementation details.

## Phase 1: Requirements Analysis

### PRD Technology Triggers Analysis
**Scan PRD and task briefs for technology indicators:**

**Platform Requirements:**
- "web application", "website" → Web development stack needed
- "mobile app", "iOS", "Android" → Mobile development decision required
- "desktop application" → Desktop framework selection needed
- "API", "service" → Backend/API technology selection

**Functionality Indicators:**
- "database", "data storage" → Database technology decision
- "real-time", "chat", "live updates" → Real-time technology considerations
- "authentication", "user accounts" → Authentication framework selection
- "payments", "e-commerce" → Payment processing technology needs
- "file upload", "images" → File handling technology requirements

**Scale and Performance Indicators:**
- "high performance", "fast" → Performance-optimised technology choices
- "many users", "scalable" → Scalability-focused selections
- "simple", "POC", "prototype" → Development speed prioritised choices

## Phase 2: Technology Category Analysis

### Core Technology Categories
Based on PRD analysis, determine which categories need decisions:

#### Frontend Technology (If Web/Mobile Interface Needed)
**Decision Required When:**
- User interface mentioned in PRD
- Web application or mobile app requirements
- User interaction workflows described

**Analysis Questions:**
- Complexity of UI requirements (simple forms vs complex interactions)
- Target audience technical sophistication
- Mobile responsiveness requirements
- Team expertise and preferences

#### Backend Technology (If Server-Side Logic Needed)
**Decision Required When:**
- Data processing mentioned
- User authentication required
- Business logic described
- API or service requirements identified

**Analysis Questions:**
- Data complexity and relationships
- Performance and scalability requirements
- Integration with existing systems
- Team language preferences and expertise

#### Database Technology (If Data Storage Needed)
**Decision Required When:**
- User data storage mentioned
- Business data management required
- Persistent information needs identified

**Analysis Questions:**
- Data structure complexity (relational vs document vs key-value)
- Consistency requirements (ACID vs eventual consistency)
- Query complexity and reporting needs
- Scalability and performance requirements

#### Infrastructure Technology (If Deployment Needed)
**Decision Required When:**
- Public access mentioned
- Hosting requirements identified
- Scalability considerations present

**Analysis Questions:**
- Expected user load and geographic distribution
- Budget constraints and preferences
- Team DevOps expertise
- Compliance and security requirements

## Phase 3: Smart Technology Recommendations

### Recommendation Logic Based on Context

#### For Personal/Learning Projects
**Prioritise:**
- Learning value and skill development
- Low operational complexity
- Free or low-cost options
- Good documentation and community support

**Example Recommendations:**
- Frontend: React + Vite (modern, widely used, great learning value)
- Backend: Node.js + Express (JavaScript continuity, simple deployment)
- Database: PostgreSQL (robust, free, excellent learning platform)
- Hosting: Vercel/Netlify + Railway/Heroku (simple deployment, free tiers)

#### For Startup/Business Projects
**Prioritise:**
- Rapid development and iteration capability
- Scalability potential without premature optimisation
- Team hiring and expertise availability
- Operational costs and maintenance

**Example Recommendations:**
- Frontend: React/Vue.js + TypeScript (team scalability, maintainability)
- Backend: Node.js/Python/Go (based on team expertise and performance needs)
- Database: PostgreSQL + Redis (proven scalability, comprehensive features)
- Infrastructure: AWS/GCP (comprehensive services, scaling potential)

#### For POC/Prototype Projects
**Prioritise:**
- Speed of development over optimisation
- Familiar technologies to reduce learning overhead
- Simple deployment and sharing
- Easy iteration and modification

**Example Recommendations:**
- Frontend: HTML/CSS/JavaScript or familiar framework
- Backend: Express.js/Flask/Rails (rapid development frameworks)
- Database: SQLite/PostgreSQL (simple setup, easy migration later)
- Hosting: GitHub Pages/Vercel (immediate deployment)

## Phase 4: Technology Decision Presentation

### Decision Format with Reasoning
```
"Based on your PRD analysis, here are my technology recommendations:

🎯 FRONTEND: React + TypeScript + Vite
   Reasoning: Your PRD mentions complex user interactions and data management
   Constraints: Mobile-responsive design, UK accessibility standards
   Implementation Notes: Focus on component reusability, modern React patterns

🔧 BACKEND: Node.js + Express + TypeScript  
   Reasoning: API requirements and real-time features detected
   Constraints: Secure authentication, GDPR compliance for UK users
   Implementation Notes: RESTful API design, proper error handling

💾 DATABASE: PostgreSQL + Redis
   Reasoning: Complex data relationships and performance requirements
   Constraints: Data protection compliance, backup and recovery capability
   Implementation Notes: Proper indexing, connection pooling

☁️ INFRASTRUCTURE: Railway + Cloudflare
   Reasoning: Simple deployment with professional features
   Constraints: UK/EU data residency for GDPR compliance
   Implementation Notes: Environment variable management, monitoring setup

Alternative approaches considered:
- Next.js fullstack (simpler but less flexible for your API needs)
- Python/Django (excellent but team JavaScript expertise prioritised)
- MongoDB (document flexibility but relational data structure better fits your requirements)

Would you like to discuss any of these recommendations or explore alternatives?"
```

## Phase 5: Technology Constraint Integration

### Enhance Task Briefs with Technology Context
**Update existing task briefs with technology-specific constraints:**

**Original Task Brief:**
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Research Areas: UI framework selection, user experience patterns
```

**Enhanced with Technology Context:**
```
Task 1: Implement Core User Features
Goal: Enable users to perform primary actions identified in PRD
Constraints: UK English throughout, intuitive UX, mobile-responsive design
Technology Context: React + TypeScript, Material-UI component library
Research Areas: React component patterns, accessibility with Material-UI
Implementation Notes: Focus on reusable components, proper TypeScript typing
```

### Technology-Specific Research Areas
**Add to task briefs:**
- Specific framework patterns and best practices
- Security considerations for chosen technologies
- Performance optimisation approaches
- Testing strategies appropriate for tech stack
- Deployment and operational considerations

## Phase 6: Implementation Guidance Generation

### Technology Setup Instructions
**Create technology-specific setup guidance:**

#### Development Environment Setup
- Required development tools and versions
- Project initialisation commands
- Development server configuration
- Environment variable template

#### Project Structure Recommendations
- Directory organisation patterns for chosen stack
- Configuration file templates
- Development workflow recommendations
- Code organisation principles

#### Integration Guidelines
- How different technology components connect
- Data flow patterns between frontend/backend/database
- Authentication and authorisation implementation approaches
- Error handling and logging strategies

## Phase 7: Decision Documentation

### Technology Decisions Record
**Document all technology choices with reasoning:**

```markdown
# Technology Decisions

## Frontend Technology: React + TypeScript
**Decision Date:** [Current Date]
**Reasoning:** Complex UI requirements, team TypeScript expertise, component reusability needs
**Alternatives Considered:** Vue.js (less ecosystem), Svelte (smaller community), Plain JavaScript (maintenance concerns)
**Constraints:** Mobile responsiveness, UK accessibility compliance
**Review Trigger:** If performance becomes critical or team composition changes

## Backend Technology: Node.js + Express
**Decision Date:** [Current Date]  
**Reasoning:** JavaScript continuity, rapid development, excellent ecosystem
**Alternatives Considered:** Python/Flask (team preference for JS), Go (development speed priority)
**Constraints:** GDPR compliance, secure authentication requirements
**Review Trigger:** If performance requirements exceed Node.js capabilities

[Continue for all technology categories...]
```

### Technology Migration Considerations
**For each technology choice, document:**
- When to consider migrating to alternatives
- What indicators suggest current choice isn't working
- How to plan migration if needed
- Cost and complexity estimates for changes

## Integration with Master Task Analysis

### Task Brief Enhancement
- Add technology-specific constraints to existing task briefs
- Include implementation approach guidance
- Specify research areas with technology context
- Update dependencies based on technology architecture

### New Technology-Specific Task Briefs
**May generate additional task briefs:**
- Development environment setup and configuration
- Technology integration and architecture implementation
- Performance monitoring and optimisation setup
- Deployment pipeline and operational procedures

## Output Deliverables

1. **Technology Recommendations Document**: Comprehensive technology choices with reasoning
2. **Enhanced Task Briefs**: Updated with technology-specific context and constraints
3. **Setup Instructions**: Technology-specific development environment guidance
4. **Architecture Overview**: How chosen technologies integrate and communicate
5. **Migration Planning**: Future-proofing and technology evolution considerations

## Meta-Documentation

This Technology Selection wizard balances:
- **Informed recommendations** based on project requirements and current best practices
- **Flexibility for implementation** without over-specifying technical details
- **Context enhancement** of existing task briefs rather than replacement
- **Future adaptability** through decision documentation and migration planning

The key innovation is technology choice integration with existing planning documents rather than creating separate technical specifications that might conflict with project evolution.