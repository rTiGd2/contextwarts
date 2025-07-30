# Pattern Application Engine

## Purpose
The Pattern Application Engine transforms project development from a one-time setup to continuous evolution through composable, context-aware patterns that can be applied at any stage of a project's lifecycle.

---

## Core Concepts

### Pattern Definition
A **Pattern** is a reusable implementation guide that can be applied to projects in multiple contexts:
- **Creation**: Applied during initial project setup
- **Enhancement**: Added to existing projects to introduce new capabilities
- **Gap Filling**: Applied to complete partial implementations
- **Upgrade**: Used to enhance existing patterns with advanced features

### Application Modes

#### 1. Creation Mode
**Purpose**: Bootstrap new projects with foundational patterns
**Context**: New project initialization
**Behavior**: Apply minimal viable patterns for project type
**Example**: "Create a startup web application" → Apply `modern-web-stack` + `basic-security` + `monolith-first` patterns

#### 2. Enhancement Mode  
**Purpose**: Add new capabilities to existing projects
**Context**: Feature expansion or technology adoption
**Behavior**: Apply specific patterns while respecting existing architecture
**Example**: "Add PWA capabilities to existing React app" → Apply `progressive-web-app` pattern with context awareness

#### 3. Gap Mode
**Purpose**: Fill missing or incomplete implementations
**Context**: Project analysis reveals missing patterns
**Behavior**: Detect gaps and apply patterns to complete functionality
**Example**: Analysis finds missing authentication → Apply `advanced-authentication` pattern

#### 4. Upgrade Mode
**Purpose**: Enhance existing patterns with advanced features
**Context**: Evolving requirements or security improvements
**Behavior**: Extend current patterns without breaking existing functionality
**Example**: Upgrade basic auth to include WebAuthn/passkeys

---

## Pattern Structure

### Core Pattern Components

```
patterns/
├── [category]/
│   ├── [pattern-name]/
│   │   ├── pattern.md              # Main implementation guide
│   │   ├── detection.triggers      # Automatic detection rules
│   │   ├── dependencies.yaml       # Pattern dependencies and conflicts
│   │   ├── application/
│   │   │   ├── creation.md         # Creation mode guidance
│   │   │   ├── enhancement.md      # Enhancement mode guidance
│   │   │   ├── gap-filling.md      # Gap mode guidance
│   │   │   └── upgrade.md          # Upgrade mode guidance
│   │   ├── context/
│   │   │   ├── questionnaire.md    # Context gathering questions
│   │   │   ├── analysis.md         # Project analysis criteria
│   │   │   └── customization.md    # Context-based customization
│   │   └── validation/
│   │       ├── completion.md       # Pattern completion criteria
│   │       ├── quality.md          # Quality assessment
│   │       └── integration.md      # Integration validation
```

### Pattern Metadata
```yaml
# dependencies.yaml
pattern:
  id: "advanced-authentication"
  version: "1.0"
  category: "security"
  
dependencies:
  required:
    - "basic-https"
    - "session-management"
  optional:
    - "database-integration"
  
conflicts:
    - pattern: "basic-authentication"
      resolution: "upgrade"
      message: "Advanced authentication replaces basic auth patterns"

application_modes:
  creation:
    complexity: "high"
    time_estimate: "2-4 weeks"
    prerequisites: ["https", "user-management"]
    
  enhancement:
    complexity: "medium"
    time_estimate: "1-2 weeks" 
    compatibility_check: true
    
  gap_filling:
    detection_confidence: 0.9
    auto_apply: false
    
  upgrade:
    from_patterns: ["basic-authentication", "simple-jwt"]
    breaking_changes: false

context_requirements:
  - user_base_size
  - security_requirements
  - compliance_needs
  - existing_auth_system
  - technical_expertise
```

---

## Pattern Application Workflow

### 1. Context Gathering Phase

#### Universal Context Collection
```markdown
# Core Project Context (Always Collected)
1. **Project Stage**: New | Existing | Legacy Migration
2. **Team Size**: Solo | Small (2-5) | Medium (5-15) | Large (15+)
3. **Technical Expertise**: Junior | Mixed | Senior | Expert
4. **Timeline**: Prototype | MVP | Production | Long-term
5. **Budget Constraints**: Minimal | Moderate | Flexible | Enterprise
6. **Deployment Target**: Local | Cloud | Hybrid | Edge
```

#### Pattern-Specific Context
Each pattern defines its own questionnaire for targeted context gathering:

```markdown
# Advanced Authentication Pattern Context
1. **User Base**: Internal team | Small user base (<1K) | Medium (1K-100K) | Large (100K+)
2. **Security Requirements**: Basic | Standard | High | Regulated
3. **Compliance Needs**: None | GDPR | HIPAA | PCI-DSS | Multiple
4. **Existing Authentication**: None | Basic password | JWT | SSO | Legacy system
5. **Authentication Preferences**: Simple | Modern (WebAuthn) | Enterprise SSO | Multiple options
6. **Risk Tolerance**: Low (maximum security) | Balanced | High (convenience focus)
```

### 2. Pattern Detection and Analysis

#### Automatic Detection Engine
```python
# Pattern Detection Logic (Conceptual)
class PatternDetector:
    def analyze_project(self, project_path: str) -> PatternAnalysis:
        analysis = PatternAnalysis()
        
        # File-based detection
        for pattern in self.patterns:
            triggers = pattern.load_triggers()
            confidence = self.calculate_confidence(project_path, triggers)
            
            if confidence > 0.7:
                analysis.add_detected_pattern(pattern, confidence)
            elif confidence > 0.3:
                analysis.add_potential_pattern(pattern, confidence)
        
        # Gap analysis
        analysis.gaps = self.detect_gaps(analysis.detected_patterns)
        
        # Upgrade opportunities
        analysis.upgrades = self.detect_upgrades(analysis.detected_patterns)
        
        return analysis
```

#### Gap Detection Rules
```yaml
# Pattern gap detection
gaps:
  - condition: "has_user_management AND NOT has_authentication"
    missing_pattern: "advanced-authentication"
    confidence: 0.9
    
  - condition: "has_web_app AND NOT has_https"
    missing_pattern: "basic-https"
    confidence: 1.0
    
  - condition: "has_api AND NOT has_rate_limiting"
    missing_pattern: "api-rate-limiting"
    confidence: 0.7
```

### 3. Context-Aware Application

#### Intelligent Pattern Customization
```markdown
# Context-Based Pattern Adaptation

## High-Security Context Detected
- Enable all security features
- Require multi-factor authentication
- Implement comprehensive audit logging
- Add advanced threat protection

## Small Team Context Detected  
- Simplify configuration
- Provide sensible defaults
- Include setup automation
- Focus on maintenance efficiency

## Legacy Integration Context Detected
- Provide migration pathways
- Include backward compatibility
- Offer gradual rollout options
- Maintain existing functionality
```

---

## Pattern Categories and Application Modes

### Technology Patterns
**Examples**: `modern-web-stack`, `progressive-web-app`, `container-first-deployment`
- **Creation**: Choose technology stack for new projects
- **Enhancement**: Add new technologies to existing projects
- **Gap**: Fill missing technology implementations
- **Upgrade**: Modernize existing technology choices

### Architecture Patterns  
**Examples**: `monolith-first`, `microservices-ready`, `serverless-native`
- **Creation**: Define initial architecture approach
- **Enhancement**: Add architectural capabilities (e.g., add microservices readiness)
- **Gap**: Implement missing architectural components
- **Upgrade**: Evolve architecture (e.g., monolith to microservices)

### Security Patterns
**Examples**: `advanced-authentication`, `basic-security`, `pci-dss-compliance`
- **Creation**: Establish security foundation
- **Enhancement**: Add specific security features (2FA, WebAuthn)
- **Gap**: Address security vulnerabilities
- **Upgrade**: Strengthen existing security measures

### Infrastructure Patterns
**Examples**: `reverse-proxy-load-balancer`, `container-orchestration`
- **Creation**: Set up deployment infrastructure
- **Enhancement**: Add infrastructure capabilities
- **Gap**: Implement missing infrastructure components
- **Upgrade**: Improve infrastructure reliability and performance

### Project Patterns
**Examples**: `personal-project`, `startup-mvp`, `enterprise-application`
- **Creation**: Define project structure and approach
- **Enhancement**: Add project management capabilities
- **Gap**: Implement missing project components
- **Upgrade**: Scale project approach (e.g., personal to startup)

---

## Human-AI Collaboration Model

### Context Maximization Strategy
The pattern system is designed to help humans provide exactly the context AI needs for optimal results:

#### 1. Progressive Context Gathering
```markdown
# Start Broad, Get Specific
1. **Project Overview** (30 seconds)
   - What are you building?
   - Who is it for?
   - What's the main goal?

2. **Pattern-Specific Context** (2-3 minutes per pattern)
   - Targeted questions for each applicable pattern
   - Only ask relevant questions based on project type
   - Build context progressively

3. **Implementation Context** (As needed)
   - Technical constraints
   - Integration requirements
   - Customization needs
```

#### 2. Intelligent Context Inference
```markdown
# AI Context Building
- **Pattern Dependencies**: "Since you're adding authentication, you'll need HTTPS"
- **Context Implications**: "Enterprise users typically need SSO integration"
- **Experience-Based Suggestions**: "Teams your size usually prefer simpler deployment"
```

#### 3. Context Validation Loop
```markdown
# Continuous Context Refinement
1. **Initial Assessment**: AI proposes pattern application based on gathered context
2. **Human Feedback**: User confirms, adjusts, or provides additional context
3. **Refinement**: AI adjusts approach based on feedback
4. **Implementation**: Apply pattern with full context understanding
```

### Example Context Interaction

#### Pattern: Advanced Authentication Enhancement
```markdown
AI: "I've detected your React app currently uses basic username/password authentication. I can help you add modern authentication capabilities. Let me gather some context to provide the best solution.

**Quick Context (30 seconds):**
1. Who uses this application? (Internal team/External users/Both)
2. What's your primary concern? (Security/User Experience/Compliance/All)
3. Do you have existing infrastructure? (None/Basic/Enterprise)

**Based on your answers, I'll ask 3-5 more specific questions to design the perfect authentication upgrade for your situation.**"