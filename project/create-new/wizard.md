# Project Creation Wizard

## Overview
This wizard guides you through creating a new software project with appropriate context tracks for your specific needs. It uses dynamic context loading based on your responses to ensure you get relevant guidance without information overload.

## Initialization
**Context Loading**: Load all `.triggers` files from tracks directory at startup to enable fast keyword matching during Q&A.

**State Management**: Create `.aiwizard/project.create-new.state.md` and `.aiwizard/project.create-new.additionalcontext.md` for session persistence.

## Phase 1: Project Foundation

### Step 1.1: Basic Project Understanding
**Q&A Required**: Understanding project context before loading specific tracks

**Question 1**: What type of project are you creating?

A) Personal project (learning, portfolio, experimentation)
B) Proof of concept (market validation, technical feasibility)  
C) Startup venture (business validation, funding, scaling)
D) Enterprise/client project (stakeholder management, compliance)
E) Open source/community project

**Trigger Processing**: Based on response, load appropriate project track and scan response for additional trigger keywords.

### Step 1.2: Project Scope and Goals
**Question 2**: What are your primary goals for this project?

Provide multiple-choice options based on project type selected, plus free-form input for specific goals.

**Keyword Scanning**: Process response for trigger words that might indicate need for additional context tracks.

## Phase 2: Dynamic Context Loading

### Step 2.1: Technology Context Discovery
**Question 3**: Describe your project in a few sentences. What will it do and how will users interact with it?

**Trigger Analysis**: Scan response for technology-related keywords:
- Web application, API, mobile app, desktop application
- Specific technologies: Python, .NET, Node.js, React, etc.
- Integration needs: databases, third-party APIs, cloud services

**Context Loading**: Based on triggers found, ask user to confirm loading relevant technology tracks.

### Step 2.2: Security Context Discovery
**Question 4**: Does your project involve any of the following?

Present checklist based on security triggers found in previous responses:
- [ ] User authentication and personal data
- [ ] Payment processing or financial transactions
- [ ] Healthcare or sensitive personal information
- [ ] Enterprise or corporate data
- [ ] Public-facing with high security requirements

**Context Loading**: Load appropriate security tracks based on selections.

### Step 2.3: Architecture Context Discovery
**Question 5**: What are your expectations for project scale and team size?

A) Individual or small team (2-3 people), simple deployment
B) Small team (4-8 people), moderate complexity
C) Growing team (8-15 people), need for scalability
D) Large team (15+ people), distributed development
E) High-scale requirements from the start

**Context Loading**: Load appropriate architecture tracks based on response.

## Phase 3: Enhanced PRD Creation

### Step 3.1: Context-Aware PRD Generation
With all relevant tracks loaded, generate comprehensive PRD that includes:

**From Project Track**:
- Project goals and success metrics
- Resource constraints and timeline
- Risk factors and mitigation strategies

**From Technology Track**:
- Technology stack recommendations
- Integration requirements
- Performance considerations

**From Security Track**:
- Security requirements and compliance needs
- Data protection requirements
- Authentication and authorisation needs

**From Architecture Track**:
- Architectural pattern recommendations
- Scalability considerations
- Development process suggestions

### Step 3.2: Enhanced Q&A Session
Use the standard create-prd.md Q&A process, but with context from loaded tracks to:
- Ask more specific, relevant questions
- Provide better multiple-choice options
- Suggest considerations user might not have thought of
- Validate requirements against loaded track recommendations

## Phase 4: Implementation Planning

### Step 4.1: Technology Stack Selection
Based on loaded technology tracks and project requirements:
- Recommend specific technologies and frameworks
- Identify potential integration challenges
- Suggest development tools and platforms
- Consider deployment and hosting options

### Step 4.2: Security Implementation Planning
Based on loaded security tracks:
- Define specific security requirements
- Identify compliance requirements
- Plan authentication and authorisation approach
- Consider data protection and privacy requirements

### Step 4.3: Architecture Planning
Based on loaded architecture tracks:
- Recommend initial architecture pattern
- Plan for future scalability needs
- Define development process and team structure
- Consider operational requirements

## Phase 5: Task Generation and Project Setup

### Step 5.1: Enhanced Task Generation
Use enhanced version of generate-tasks.md that incorporates:
- Context from all loaded tracks
- Technology-specific implementation patterns
- Security implementation requirements
- Architecture-specific development tasks

### Step 5.2: Project Template Creation
Generate project structure based on selected technology stack:
- Create basic directory structure
- Configure development tools and build systems
- Set up version control and CI/CD pipeline
- Implement basic security measures

### Step 5.3: Documentation Generation
Create comprehensive project documentation:
- Enhanced README with context from all tracks
- Development setup instructions
- Architecture decision records
- Security considerations and compliance notes

## Output Deliverables

1. **Enhanced PRD**: `prd-[project-name].md` with context from all relevant tracks
2. **Task List**: `tasks-[project-name].md` with technology and security-specific tasks
3. **Project Structure**: Generated directory structure and configuration files
4. **Documentation**: Comprehensive README and development guides
5. **Context Record**: Documentation of all loaded tracks and decisions made

## Session Management

**Resume Capability**: Check for existing `.aiwizard/project.create-new.state.md` at startup:
- If partial: Offer to resume from last completed step
- If complete: Offer to update/refresh project setup
- Load previous context decisions to avoid re-asking questions

**Context Persistence**: Store all loaded tracks and user decisions in state files for future reference and updates.

**Integration**: This wizard creates foundation for other project wizards (analyse-existing, improve-gaps) to build upon.

## Meta-Documentation

This wizard was created using the enhanced project creation methodology that emerged from combining:
- Original create-prd.md feature-level planning
- Research-based project success factors
- Modular track system for contextual expertise
- Dynamic context loading for efficiency
- Session persistence for resume capability

The key innovation is the hybrid required/optional context loading system that provides comprehensive guidance without overwhelming users with irrelevant information.