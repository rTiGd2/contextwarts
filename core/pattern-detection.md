# Pattern Detection and Gap Analysis Framework

## Purpose
Automatically detect existing patterns in projects, identify gaps, and recommend pattern applications based on project analysis and context.

---

## Detection Engine Architecture

### Multi-Modal Detection Strategy
The detection engine uses multiple approaches to identify patterns:

#### 1. File Pattern Analysis
**Scans project files for pattern indicators**
```python
# Conceptual detection logic
class FilePatternDetector:
    def analyze_project(self, project_path: str) -> List[PatternMatch]:
        matches = []
        
        for pattern in self.pattern_registry:
            triggers = pattern.load_triggers()
            confidence = self.calculate_file_confidence(project_path, triggers)
            
            if confidence > 0.3:  # Threshold for potential match
                matches.append(PatternMatch(
                    pattern=pattern,
                    confidence=confidence,
                    evidence=self.collect_evidence(project_path, triggers),
                    completeness=self.assess_completeness(project_path, pattern)
                ))
        
        return matches
```

#### 2. Dependency Analysis
**Analyzes package.json, requirements.txt, etc.**
```yaml
# Package-based detection rules
dependency_patterns:
  "vite-plugin-pwa":
    pattern: "progressive-web-app"
    confidence: 0.9
    additional_checks:
      - "vite.config.ts contains VitePWA"
      - "manifest.json exists"
  
  "Fido2NetLib":
    pattern: "advanced-authentication"
    confidence: 0.8
    additional_checks:
      - "Controllers contain Passkey"
      - "Services contain FIDO2"
      
  "express-rate-limit":
    pattern: "api-rate-limiting"
    confidence: 0.7
```

#### 3. Configuration Analysis
**Examines configuration files**
```yaml
# Configuration-based detection
config_patterns:
  docker_compose:
    file_patterns: ["docker-compose.yml", "docker-compose.*.yml"]
    pattern_indicators:
      - services_count > 2: "container-orchestration"
      - has_reverse_proxy: "reverse-proxy-load-balancer"
      - has_database: "database-integration"
  
  nginx_config:
    file_patterns: ["nginx.conf", "*/nginx.conf"]
    pattern_indicators:
      - ssl_configuration: "https-security"
      - rate_limiting: "rate-limiting"
      - upstream_servers: "load-balancing"
```

#### 4. Code Structure Analysis
**Analyzes project architecture**
```python
# Structural analysis
class StructureAnalyzer:
    def analyze_architecture(self, project_path: str) -> ArchitecturePattern:
        structure = self.scan_project_structure(project_path)
        
        # Detect architecture patterns
        if self.is_monolith_structure(structure):
            return ArchitecturePattern("monolith-first", confidence=0.8)
        elif self.is_microservices_structure(structure):
            return ArchitecturePattern("microservices-ready", confidence=0.9)
        elif self.is_serverless_structure(structure):
            return ArchitecturePattern("serverless-native", confidence=0.7)
```

---

## Gap Analysis Engine

### Gap Detection Strategies

#### 1. Pattern Completeness Assessment
**Evaluates if detected patterns are fully implemented**
```python
class CompletenessAnalyzer:
    def assess_pattern_completeness(self, pattern: Pattern, project: Project) -> CompletenessResult:
        required_components = pattern.get_required_components()
        present_components = self.detect_components(project, required_components)
        
        completeness_score = len(present_components) / len(required_components)
        missing_components = set(required_components) - set(present_components)
        
        return CompletenessResult(
            score=completeness_score,
            missing=missing_components,
            recommendations=self.generate_completion_recommendations(missing_components)
        )
```

#### 2. Security Gap Analysis
**Identifies missing security patterns**
```yaml
# Security gap detection rules
security_gaps:
  authentication_missing:
    condition: "has_user_management AND NOT has_authentication"
    severity: "critical"
    pattern_recommendation: "advanced-authentication"
    
  https_missing:
    condition: "has_web_app AND NOT has_https"
    severity: "critical"
    pattern_recommendation: "https-security"
    
  rate_limiting_missing:
    condition: "has_public_api AND NOT has_rate_limiting"
    severity: "high"
    pattern_recommendation: "api-rate-limiting"
```

#### 3. Architecture Gap Analysis
**Identifies architectural improvements**
```yaml
# Architecture gap detection
architecture_gaps:
  scalability_concerns:
    condition: "monolith AND expected_scale > medium"
    recommendation: "microservices-readiness-assessment"
    
  deployment_gaps:
    condition: "has_app AND NOT has_deployment_automation"
    recommendation: "container-first-deployment"
    
  monitoring_gaps:
    condition: "production_app AND NOT has_monitoring"
    recommendation: "observability-patterns"
```

#### 4. Modern Practice Gaps
**Identifies opportunities for modernization**
```yaml
# Modernization opportunities
modernization_gaps:
  pwa_opportunity:
    condition: "web_app AND mobile_users > 30%"
    pattern_recommendation: "progressive-web-app"
    
  auth_modernization:
    condition: "basic_password_auth AND security_requirements > basic"
    pattern_recommendation: "advanced-authentication"
    
  deployment_modernization:
    condition: "manual_deployment OR legacy_deployment"
    pattern_recommendation: "modern-deployment-patterns"
```

---

## Context-Aware Pattern Recommendations

### Context Integration with Detection

#### Project Context Analysis
```python
class ContextAnalyzer:
    def analyze_project_context(self, project: Project) -> ProjectContext:
        context = ProjectContext()
        
        # Analyze project scale
        context.scale = self.determine_scale(project)
        
        # Analyze team context
        context.team_size = self.infer_team_size(project)
        
        # Analyze technology maturity
        context.tech_maturity = self.assess_technology_choices(project)
        
        # Analyze security posture
        context.security_level = self.assess_security_implementation(project)
        
        return context
```

#### Context-Based Recommendations
```yaml
# Context-aware pattern suggestions
context_recommendations:
  small_team_context:
    prefer_patterns:
      - "simple-deployment"
      - "monolith-first"
      - "basic-security"
    avoid_patterns:
      - "complex-microservices"
      - "advanced-orchestration"
  
  enterprise_context:
    prefer_patterns:
      - "advanced-authentication"
      - "enterprise-security"
      - "compliance-patterns"
    require_patterns:
      - "audit-logging"
      - "security-monitoring"
  
  high_traffic_context:
    require_patterns:
      - "reverse-proxy-load-balancer"
      - "caching-strategies"
      - "performance-monitoring"
```

---

## Interactive Gap Analysis

### User-Guided Analysis
```markdown
# Interactive Gap Analysis Flow

## Phase 1: Automated Detection (30 seconds)
1. **File System Scan**: Identify obvious patterns and technologies
2. **Configuration Analysis**: Parse config files for infrastructure patterns
3. **Dependency Analysis**: Analyze package dependencies
4. **Initial Assessment**: Generate preliminary pattern detection report

## Phase 2: Context Gathering (2-3 minutes)
1. **Project Overview Questions**:
   - "What type of application is this?"
   - "What's the main business purpose?"
   - "Who are the primary users?"

2. **Technical Context Questions**:
   - "What are your scalability requirements?"
   - "What security level do you need?"
   - "Any compliance requirements?"

## Phase 3: Targeted Analysis (1-2 minutes)
1. **Pattern-Specific Questions**:
   - Based on detected patterns, ask specific clarifying questions
   - Validate assumptions from automated detection
   - Gather missing context for recommendations

## Phase 4: Gap Analysis Report (Immediate)
1. **Pattern Summary**: What patterns are currently implemented
2. **Gap Identification**: What's missing or incomplete
3. **Priority Recommendations**: Most important patterns to implement
4. **Implementation Roadmap**: Suggested order of pattern application
```

### Example Interactive Flow
```markdown
# Interactive Gap Analysis Example

AI: "I've analyzed your React application and detected the following patterns:
✅ Modern Web Stack (React + TypeScript + Vite)
✅ Basic HTTPS (development setup)
⚠️  Basic Authentication (password-only, could be enhanced)
❌ No deployment automation detected
❌ No rate limiting on API endpoints

Quick questions to provide better recommendations:

1. How many users do you expect? (helps determine scaling needs)
2. What type of data does your app handle? (helps determine security needs)
3. Is this for internal use or public? (helps determine deployment needs)

Based on your answers, I can recommend specific patterns and implementation priorities."

User: "About 5000 users, handling customer payment data, public-facing"

AI: "Perfect! Based on that context:

🔴 CRITICAL GAPS (Security & Compliance):
- Advanced Authentication Pattern (PCI-DSS compliance for payments)
- Rate Limiting Pattern (prevent abuse)
- Audit Logging Pattern (compliance requirement)

🟡 IMPORTANT GAPS (Scale & Reliability):
- Container Deployment Pattern (handle 5K users reliably)
- Database Scaling Pattern (user growth preparation)

🟢 NICE TO HAVE:
- Progressive Web App Pattern (better mobile experience)
- Monitoring Pattern (operational visibility)

Would you like me to start with the critical security patterns first?"
```

---

## Pattern Relationship Analysis

### Dependency Chain Detection
```python
class PatternRelationshipAnalyzer:
    def analyze_pattern_dependencies(self, detected_patterns: List[Pattern], 
                                   recommended_patterns: List[Pattern]) -> DependencyGraph:
        graph = DependencyGraph()
        
        # Build dependency relationships
        for pattern in detected_patterns + recommended_patterns:
            dependencies = pattern.get_dependencies()
            for dep in dependencies:
                graph.add_edge(pattern, dep)
        
        # Detect circular dependencies
        cycles = graph.detect_cycles()
        if cycles:
            self.resolve_circular_dependencies(cycles)
        
        # Order patterns by dependency hierarchy
        ordered_patterns = graph.topological_sort()
        
        return DependencyGraph(
            patterns=ordered_patterns,
            relationships=graph.edges,
            application_order=ordered_patterns
        )
```

### Conflict Detection
```python
class ConflictDetector:
    def detect_conflicts(self, patterns: List[Pattern]) -> List[Conflict]:
        conflicts = []
        
        for i, pattern_a in enumerate(patterns):
            for pattern_b in patterns[i+1:]:
                conflict = self.check_pattern_conflict(pattern_a, pattern_b)
                if conflict:
                    conflicts.append(conflict)
        
        return conflicts
    
    def suggest_conflict_resolution(self, conflict: Conflict) -> Resolution:
        # Analyze conflict type and suggest resolution
        if conflict.type == ConflictType.DIRECT:
            return self.suggest_replacement_resolution(conflict)
        elif conflict.type == ConflictType.VERSION:
            return self.suggest_upgrade_resolution(conflict)
        else:
            return self.suggest_configuration_resolution(conflict)
```

---

## Continuous Pattern Monitoring

### Pattern Drift Detection
```python
class PatternDriftMonitor:
    def monitor_pattern_compliance(self, project: Project, applied_patterns: List[Pattern]):
        for pattern in applied_patterns:
            current_state = self.assess_current_implementation(project, pattern)
            expected_state = pattern.get_expected_state()
            
            drift = self.calculate_drift(current_state, expected_state)
            
            if drift.severity > DriftSeverity.MINOR:
                self.alert_pattern_drift(pattern, drift)
                self.suggest_corrective_actions(pattern, drift)
```

### Evolution Recommendations
```python
class PatternEvolutionAdvisor:
    def suggest_pattern_evolution(self, project: Project) -> List[EvolutionRecommendation]:
        recommendations = []
        
        # Analyze project growth
        current_scale = self.assess_current_scale(project)
        projected_scale = self.project_future_scale(project)
        
        if projected_scale.requires_architecture_evolution(current_scale):
            recommendations.append(EvolutionRecommendation(
                pattern="microservices-readiness",
                reason="Projected scale requires architecture evolution",
                timeline="6-12 months",
                priority="medium"
            ))
        
        return recommendations
```

---

## Report Generation

### Gap Analysis Report Structure
```markdown
# Pattern Analysis Report Template

## Executive Summary
- **Project Type**: [Detected project type]
- **Current Maturity**: [Assessment of current implementation maturity]
- **Critical Gaps**: [Number of critical gaps found]
- **Recommended Actions**: [Top 3 priority actions]

## Current Pattern Implementation
### ✅ Implemented Patterns
- Pattern Name (Completeness: X%, Quality: Y/10)
  - Implementation details
  - Areas for improvement

### ⚠️ Partially Implemented Patterns  
- Pattern Name (Completeness: X%)
  - What's missing
  - Impact of incompleteness
  - Completion recommendations

## Gap Analysis
### 🔴 Critical Gaps (Security/Compliance)
- Gap description
- Business impact
- Implementation complexity
- Timeline estimate

### 🟡 Important Gaps (Performance/Scalability)
- Gap description  
- Growth impact
- Implementation approach

### 🟢 Enhancement Opportunities
- Potential improvements
- User experience impact
- ROI assessment

## Implementation Roadmap
### Phase 1: Critical (Weeks 1-2)
- Critical security/compliance gaps

### Phase 2: Important (Weeks 3-6)  
- Performance and scalability improvements

### Phase 3: Enhancement (Weeks 7-12)
- User experience and operational improvements

## Pattern Dependencies
- Dependency graph visualization
- Application order recommendations
- Conflict resolutions required

## Resource Requirements
- Development time estimates
- Infrastructure requirements
- Third-party service needs
- Ongoing maintenance considerations
```

This detection and gap analysis framework enables the pattern system to intelligently analyze projects and provide contextual recommendations for pattern application, making the wizard truly adaptive to any project's current state and future needs.