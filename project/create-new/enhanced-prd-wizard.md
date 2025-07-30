# Enhanced PRD Creation Wizard

## Overview
This wizard creates Product Requirements Documents with intelligent section recommendations based on your project context. It builds on proven PRD methodology with smart suggestions for additional depth when beneficial.

## Initialization
**Q&A Session Setup**: Before starting, ask user about capturing outputs:
- "Would you like me to save our Q&A session details to `.aiwizard/project.create-new.qa-capture.md` for future reference?"
- "Should I save any research I conduct during this process to `.aiwizard/research/` for your project records?"

## Phase 1: Core Questions (Non-Skippable)

### Essential Context for Minimum Viable PRD

**Question 1: Project Description**
"Describe your project in a few sentences. What will it do and how will users interact with it?"

**Question 2: Primary Goal**
"What is the main goal you want to achieve with this project?"

**Question 3: Target User**
"Who is the primary user of this project? (Even if it's just yourself for a POC, that's perfectly valid.)"

**Question 4: Core Functionality**
"What are the key actions a user should be able to perform? Keep it to the essential 3-5 things."

**Question 5: Success Criteria**
"How will you know when this project is working successfully? What does 'done' look like?"

## Phase 2: Intelligent Section Analysis

### Trigger Detection System
**Analyse Core responses for section recommendation triggers:**

**Technical Deep-dive Triggers:**
- API, integration, third-party, existing systems, database
- performance, real-time, high-volume, scaling
- mobile, desktop, web application, platform
- complex data, workflows, business logic

**Security Requirements Triggers:**
- user accounts, login, authentication, personal data
- payment, financial, healthcare, sensitive information
- public, internet facing, external users, privacy
- compliance, regulatory, enterprise, business data

**Growth Planning Triggers:**
- multiple users, hundreds of users, public facing
- startup, business, revenue, customers, monetisation
- team growth, hiring, expanding, scaling
- investment, funding, market opportunity

**Market Analysis Triggers:**
- competitors, existing solutions, market, competitive advantage
- unique, different, better than, alternative to
- business model, sell, commercial, industry
- positioning, differentiation, value proposition

### Smart Recommendations Presentation

```
"Based on your responses, here's my plan:

✅ INCLUDING [Section Name]
   → [Specific trigger detected and why it's relevant]

⚠️ SKIPPING [Section Name]  
   → [Reason for skipping based on their context]

❌ SKIPPING [Section Name]
   → [Clear reason why this doesn't apply]

If you'd rather I didn't skip any of these sections, let me know. If you aren't certain about any of them, ask me about them.

Otherwise, shall we proceed with the PRD creation?"
```

## Phase 3: Enhanced Q&A Session

### Core PRD Questions (Always Asked)
**Based on original create-prd.md proven methodology:**

**Problem/Goal Deep-dive:**
"What specific problem does this solve for your users? What pain point are you addressing?"

**User Stories:**
"Can you provide 2-3 user stories? Format: As a [type of user], I want to [perform an action] so that [benefit]."

**Acceptance Criteria:**
"What are the key success criteria? How will we know each feature is working correctly?"

**Scope Boundaries:**
"What should this project NOT do? Any specific boundaries or limitations to set?"

### Conditional Sections (Based on Recommendations)

#### Technical Deep-dive Section (If Recommended)
- **Data Requirements**: "What kind of data does this handle? Storage, processing, integration needs?"
- **Performance Requirements**: "Any speed, capacity, or performance expectations?"
- **Integration Needs**: "Does this need to connect with existing systems or third-party services?"
- **Technical Constraints**: "Any technical limitations, compliance requirements, or architectural preferences?"

#### Security Requirements Section (If Recommended)
- **Authentication Needs**: "How will users access the system? Registration, login, permissions?"
- **Data Sensitivity**: "What types of data will you handle? Any privacy or compliance considerations?"
- **Access Control**: "Who should have access to what? Any role-based permissions needed?"
- **Security Considerations**: "Any specific security requirements or regulatory compliance needs?"

#### Growth Planning Section (If Recommended)
- **Scale Expectations**: "How many users do you expect initially vs. if successful?"
- **Performance Scaling**: "Any expectations for handling increased load or data volume?"
- **Team Growth**: "Will the development team grow? Any multi-developer considerations?"
- **Feature Evolution**: "How might this project evolve? Any features you'd add later?"

#### Market Analysis Section (If Recommended)
- **Competitive Landscape**: "Are there existing solutions? How will yours be different?"
- **Value Proposition**: "What makes your approach unique or better?"
- **Market Positioning**: "How would you position this in the market?"
- **Business Context**: "Any business model, revenue, or commercial considerations?"

## Phase 4: Enhanced PRD Generation

### PRD Structure with Dynamic Sections

**Standard Sections (Always Included):**
1. **Introduction/Overview**: Project description and problem solved
2. **Goals**: Specific, measurable objectives  
3. **User Stories**: Detailed user narratives
4. **Functional Requirements**: Numbered, specific functionalities
5. **Non-Goals (Out of Scope)**: Clear boundaries
6. **Success Metrics**: Measurable success criteria
7. **Open Questions**: Remaining clarifications needed

**Dynamic Sections (Added Based on Recommendations):**
8. **Technical Considerations**: Architecture, performance, integration requirements
9. **Security Requirements**: Authentication, data protection, compliance needs
10. **Scalability Planning**: Growth expectations, performance scaling, team considerations
11. **Market Positioning**: Competitive analysis, differentiation, business context
12. **Design Considerations**: UI/UX requirements, mockups, style guidelines

### Enhanced Output Quality

**Context-Aware Content:**
- **Technical sections** reference specific technologies/patterns mentioned
- **Security sections** address specific compliance or data sensitivity mentioned  
- **Growth sections** scale appropriately to mentioned expectations
- **Market sections** reflect competitive context provided

**Junior Developer Focus Maintained:**
- Requirements remain explicit and unambiguous
- Technical jargon explained when necessary
- Clear, actionable specifications
- Sufficient detail for implementation planning

## Phase 5: PRD Delivery and Follow-up

### File Generation
- **Save PRD**: `prd-[project-name].md` in `/tasks` directory
- **Save Q&A Context**: `.aiwizard/project.create-new.qa-capture.md` (if requested)
- **Save Research**: `.aiwizard/research/[topic]/` (if research conducted and requested)

### Integration Points
- **Task Generation**: Enhanced PRD provides better context for generate-tasks.md
- **Project Analysis**: Rich PRD enables better analysis by analyse-existing wizard
- **Architecture Planning**: Technical sections inform architecture decisions

### Follow-up Options
"Your enhanced PRD is complete! Next steps you might consider:
- Generate implementation tasks from this PRD
- Set up project structure with appropriate technology templates  
- Run security or architecture planning based on your requirements
- Create additional feature PRDs as your project evolves"

## Meta-Documentation

This enhanced PRD wizard combines:
- **Proven methodology** from original create-prd.md
- **Intelligent recommendations** based on project context analysis
- **Conversational overrides** for user control and customisation
- **Research integration** from project initiation best practices
- **Context preservation** for downstream wizard integration

**Key Innovation**: Smart section recommendations with transparent decision-making, maintaining conversational flow while providing enterprise-level PRD depth when beneficial.