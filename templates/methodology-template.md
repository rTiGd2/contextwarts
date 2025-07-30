# Methodology Pattern Development Template

## Purpose
Template for creating custom development methodology patterns that integrate with the PatternForge wizard system.

---

## Methodology Pattern Structure

### Directory Template
```
[methodology-name]/
├── dependencies.yaml              # Methodology metadata and dependencies
├── methodology-guide.md           # Complete methodology implementation guide
├── selector-integration.md        # Integration with methodology selector
├── team-setup/                    # Team setup and training materials
│   ├── setup-guide.md            # Initial team setup
│   ├── training-materials.md     # Training and onboarding
│   └── role-definitions.md       # Role and responsibility definitions
├── process/                       # Process workflows and ceremonies
│   ├── workflow-definition.md     # Core workflow processes
│   ├── ceremonies.md             # Meetings and ceremonies
│   └── decision-frameworks.md    # Decision-making frameworks
├── tools/                         # Tool integration and setup
│   ├── recommended-tools.md       # Tool recommendations
│   ├── integrations.md           # Third-party integrations
│   └── automation.md             # Process automation
├── quality/                       # Quality gates and standards
│   ├── quality-gates.md          # Quality checkpoints
│   ├── standards.md              # Coding and process standards
│   └── metrics.md                # Success metrics and KPIs
├── templates/                     # Templates and artifacts
│   ├── user-story.template.md    # User story template
│   ├── task-breakdown.template.md # Task breakdown template
│   └── retrospective.template.md  # Retrospective template
└── examples/                      # Implementation examples
    ├── small-team-example.md
    ├── enterprise-example.md
    └── hybrid-approach-example.md
```

---

## Template Files

### 1. dependencies.yaml Template
```yaml
pattern:
  id: "[methodology-id]"
  version: "1.0"
  category: "methodology"
  name: "[Methodology Name]"
  description: "[Brief methodology description focusing on key principles and approach]"
  author: "[Your Name]"
  created: "[YYYY-MM-DD]"
  methodology_type: "pure|hybrid|framework"

dependencies:
  required:
    - pattern: "[required-pattern-1]"
      reason: "[Why this pattern is essential for the methodology]"
      auto_apply: true
      alternatives: ["[alternative-1]", "[alternative-2]"]
      
    - pattern: "[required-pattern-2]"
      reason: "[Why this pattern is essential]"
      auto_apply: true

  optional:
    - pattern: "[complementary-pattern-1]"
      reason: "[How this pattern enhances the methodology]"
      benefit: "[Specific benefit description]"
      compatibility: "high"
      
    - pattern: "[complementary-pattern-2]"
      reason: "[How this pattern enhances the methodology]"
      benefit: "[Specific benefit description]"
      applies_when: "[condition_when_recommended]"

  contextual:
    - condition: "[team_size_condition] OR [complexity_condition]"
      pattern: "[contextual-pattern-1]"
      reason: "[Why needed in this context]"
      auto_apply: false
      
    - condition: "[organizational_condition]"
      pattern: "[contextual-pattern-2]"
      reason: "[Why needed in this context]"
      auto_apply: true

conflicts:
  direct:
    - pattern: "[conflicting-methodology]"
      resolution: "replace"
      message: "[Explanation of methodology conflict]"
      migration_path: "application/enhancement.md"
      breaking_change: false
      
  soft:
    - pattern: "[soft-conflicting-approach]"
      resolution: "adapt"
      message: "[Explanation of how to adapt conflicting approach]"
      adjustment: "[What adjustment is needed]"
      compatibility: true

application_modes:
  creation:
    complexity: "medium|high"
    time_estimate: "[implementation time estimate]"
    prerequisites: ["[prerequisite-1]", "[prerequisite-2]"]
    suitable_for: ["[project-type-1]", "[project-type-2]"]
    team_expertise_required: "[required expertise level]"
    
  enhancement:
    complexity: "medium|high|very-high"
    time_estimate: "[transition time estimate]"
    compatibility_check: true
    suitable_for: ["[existing-methodology-1]", "[existing-methodology-2]"]
    cultural_change_required: true
    
  gap_filling:
    detection_confidence: 0.6-0.8
    auto_apply: false
    validation_required: true
    suitable_for: ["[gap-scenario-1]", "[gap-scenario-2]"]
    
  upgrade:
    from_patterns: ["[upgradeable-methodology-1]", "[basic-approach-2]"]
    breaking_changes: false
    process_change: true
    enhanced_features: ["[feature-1]", "[feature-2]"]

context_requirements:
  essential:
    - team_size: "[Question about team size and structure]"
    - project_complexity: "[Question about project complexity]"
    - stakeholder_involvement: "[Question about stakeholder engagement]"
    - timeline_constraints: "[Question about timeline and delivery pressure]"
    
  methodology_specific:
    - collaboration_preference: "[Methodology-specific collaboration question]"
    - quality_focus: "[Quality requirements and priorities]"
    - change_tolerance: "[Change management and adaptation preferences]"
    - documentation_needs: "[Documentation requirements and culture]"
    
  technical:
    - technical_complexity: "[Technical complexity assessment]"
    - integration_requirements: "[Integration and dependency complexity]"
    - performance_requirements: "[Performance and scalability needs]"
    - technology_constraints: "[Technology stack and constraint considerations]"
    
  organizational:
    - organizational_culture: "[Culture and change readiness assessment]"
    - decision_making_style: "[Decision-making preferences and authority]"
    - communication_patterns: "[Communication styles and preferences]"
    - success_metrics: "[How success is measured and evaluated]"

comparison_framework:
  vs_traditional_waterfall:
    methodology_advantages:
      - "[Advantage 1 over waterfall]"
      - "[Advantage 2 over waterfall]"
      - "[Advantage 3 over waterfall]"
    waterfall_advantages:
      - "[Where waterfall might be better]"
      - "[Waterfall strength 2]"
    when_to_choose_methodology:
      - "[Scenario 1 where methodology is preferred]"
      - "[Scenario 2 where methodology is preferred]"
  
  vs_agile_scrum:
    methodology_advantages:
      - "[Advantage 1 over Scrum]"
      - "[Advantage 2 over Scrum]"
    scrum_advantages:
      - "[Where Scrum might be better]"
      - "[Scrum strength 2]"
    when_to_choose_methodology:
      - "[Scenario 1 where methodology is preferred]"
      - "[Scenario 2 where methodology is preferred]"

  vs_[other_methodology]:
    methodology_advantages:
      - "[Comparative advantage 1]"
      - "[Comparative advantage 2]"
    other_advantages:
      - "[Other methodology strength 1]"
      - "[Other methodology strength 2]"
    when_to_choose_methodology:
      - "[Scenario 1]"
      - "[Scenario 2]"

customization_points:
  team_structure:
    - role_definitions: "[How roles can be customized]"
    - responsibility_matrix: "[Responsibility customization options]"
    - communication_patterns: "[Communication customization]"
    - decision_authority: "[Decision-making customization]"
    
  process_workflows:
    - ceremony_frequency: "[How ceremonies can be adjusted]"
    - workflow_stages: "[Workflow customization options]"
    - feedback_loops: "[Feedback mechanism customization]"
    - quality_gates: "[Quality gate customization]"
    
  tool_integration:
    - project_management_tools: "[PM tool integration options]"
    - development_tools: "[Development tool integration]"
    - communication_tools: "[Communication tool integration]"
    - measurement_tools: "[Metrics and measurement tool integration]"
    
  adaptation_strategies:
    - team_size_scaling: "[How methodology scales with team size]"
    - complexity_adaptation: "[Adaptation for different complexity levels]"
    - domain_customization: "[Domain-specific customizations]"
    - cultural_adaptation: "[Cultural and organizational adaptation]"

validation_criteria:
  process_adoption:
    - methodology_understanding: "[How to validate team understanding]"
    - process_adherence: "[How to measure process following]"
    - tool_utilization: "[Tool usage and effectiveness metrics]"
    - ceremony_effectiveness: "[Meeting and ceremony effectiveness]"
    
  quality_impact:
    - delivery_quality: "[Quality improvement measurements]"
    - defect_reduction: "[Defect tracking and reduction]"
    - customer_satisfaction: "[Customer satisfaction metrics]"
    - technical_debt: "[Technical debt management metrics]"
    
  team_effectiveness:
    - collaboration_improvement: "[Team collaboration metrics]"
    - knowledge_sharing: "[Knowledge sharing effectiveness]"
    - decision_speed: "[Decision-making speed and quality]"
    - conflict_resolution: "[Conflict resolution effectiveness]"
    
  business_impact:
    - delivery_speed: "[Delivery velocity and predictability]"
    - requirement_stability: "[Requirement change management]"
    - stakeholder_engagement: "[Stakeholder satisfaction and engagement]"
    - business_value_delivery: "[Business value realization metrics]"
```

### 2. methodology-guide.md Template
```markdown
# [Methodology Name] Implementation Guide

## Overview
[Comprehensive overview of the methodology, its origins, and core principles]

## Core Principles
1. **[Principle 1]**: [Detailed explanation]
2. **[Principle 2]**: [Detailed explanation]
3. **[Principle 3]**: [Detailed explanation]

## When to Use This Methodology

### Ideal Scenarios
- ✅ **[Scenario 1]**: [Why it's ideal]
- ✅ **[Scenario 2]**: [Why it's ideal]
- ✅ **[Scenario 3]**: [Why it's ideal]

### Situations to Avoid
- ❌ **[Anti-scenario 1]**: [Why to avoid]
- ❌ **[Anti-scenario 2]**: [Why to avoid]

## Implementation Roadmap

### Phase 1: Foundation (Weeks 1-2)
**Objectives**: [Phase objectives]

**Activities**:
1. [Activity 1 with timeline]
2. [Activity 2 with timeline]
3. [Activity 3 with timeline]

**Deliverables**:
- [Deliverable 1]
- [Deliverable 2]

### Phase 2: Process Implementation (Weeks 3-6)
**Objectives**: [Phase objectives]

**Activities**:
1. [Activity 1 with timeline]
2. [Activity 2 with timeline]
3. [Activity 3 with timeline]

**Deliverables**:
- [Deliverable 1]
- [Deliverable 2]

### Phase 3: Optimization (Weeks 7-12)
**Objectives**: [Phase objectives]

**Activities**:
1. [Activity 1 with timeline]
2. [Activity 2 with timeline]
3. [Activity 3 with timeline]

**Deliverables**:
- [Deliverable 1]
- [Deliverable 2]

## Core Workflows

### [Primary Workflow Name]
[Detailed workflow description with steps, inputs, outputs, and responsibilities]

**Process Steps**:
1. [Step 1] - [Responsible role] - [Duration]
2. [Step 2] - [Responsible role] - [Duration]
3. [Step 3] - [Responsible role] - [Duration]

**Inputs**: [Required inputs]
**Outputs**: [Expected outputs]
**Quality Gates**: [Quality checkpoints]

### [Secondary Workflow Name]
[Similar detailed description]

## Role Definitions

### [Role 1 Name]
**Responsibilities**:
- [Primary responsibility 1]
- [Primary responsibility 2]
- [Primary responsibility 3]

**Required Skills**:
- [Skill 1]
- [Skill 2]
- [Skill 3]

**Interactions**: [How this role interacts with others]

### [Role 2 Name]
[Similar role definition]

## Ceremonies and Meetings

### [Ceremony 1 Name]
**Purpose**: [Why this ceremony exists]
**Frequency**: [How often it occurs]
**Duration**: [How long it takes]
**Participants**: [Who attends]
**Agenda**: [Standard agenda items]
**Deliverables**: [What comes out of it]

### [Ceremony 2 Name]
[Similar ceremony definition]

## Quality Gates and Standards

### [Quality Gate 1]
**Trigger**: [When this gate is activated]
**Criteria**: [What must be met]
**Process**: [How the gate works]
**Responsible**: [Who validates]

### [Quality Gate 2]
[Similar quality gate definition]

## Tool Integration

### Recommended Tools
- **[Tool Category 1]**: [Tool recommendations] - [Why recommended]
- **[Tool Category 2]**: [Tool recommendations] - [Why recommended]
- **[Tool Category 3]**: [Tool recommendations] - [Why recommended]

### Integration Patterns
[How tools integrate with the methodology processes]

## Metrics and Measurement

### Process Metrics
- **[Metric 1]**: [Description] - [How to measure] - [Target range]
- **[Metric 2]**: [Description] - [How to measure] - [Target range]

### Quality Metrics
- **[Metric 1]**: [Description] - [How to measure] - [Target range]
- **[Metric 2]**: [Description] - [How to measure] - [Target range]

### Business Metrics
- **[Metric 1]**: [Description] - [How to measure] - [Target range]
- **[Metric 2]**: [Description] - [How to measure] - [Target range]

## Common Challenges and Solutions

### Challenge: [Common Challenge 1]
**Symptoms**: [How to recognize this challenge]
**Root Causes**: [Why this happens]
**Solutions**: [How to address it]
**Prevention**: [How to prevent it]

### Challenge: [Common Challenge 2]
[Similar challenge breakdown]

## Scaling Considerations

### Small Teams (2-5 people)
[Methodology adaptations for small teams]

### Medium Teams (5-15 people)
[Methodology adaptations for medium teams]

### Large Teams (15+ people)
[Methodology adaptations for large teams]

### Distributed Teams
[Special considerations for remote/distributed teams]

## Continuous Improvement

### Retrospective Framework
[How to continuously improve the methodology implementation]

### Evolution Triggers
[When and why to evolve the methodology]

### Adaptation Guidelines
[How to adapt the methodology to changing circumstances]

## Resources and References
- [Resource 1]: [Description and link]
- [Resource 2]: [Description and link]
- [Resource 3]: [Description and link]

---
*Methodology guide created using PatternForge Template v1.0*
*For more methodology templates: /wizard help templates*
```

### 3. selector-integration.md Template
```markdown
# [Methodology Name] - Selector Integration

## Methodology Profile
**Name**: [Methodology Name]
**Type**: [Pure|Hybrid|Framework]
**Complexity**: [Low|Medium|High|Very High]
**Learning Curve**: [Gentle|Moderate|Steep|Very Steep]

## Selection Criteria Integration

### Context Matching
```yaml
methodology_fit:
  team_size:
    optimal: ["[size-range-1]", "[size-range-2]"]
    acceptable: ["[size-range-3]", "[size-range-4]"]
    challenging: ["[size-range-5]"]
    
  project_complexity:
    excellent: ["[complexity-level-1]", "[complexity-level-2]"]
    good: ["[complexity-level-3]"]
    challenging: ["[complexity-level-4]"]
    
  stakeholder_involvement:
    required: "[involvement-level-1]"
    preferred: "[involvement-level-2]"
    acceptable: "[involvement-level-3]"
    
  timeline_pressure:
    excellent: ["[pressure-level-1]"]
    good: ["[pressure-level-2]"]
    challenging: ["[pressure-level-3]"]
```

### Recommendation Scoring
```yaml
scoring_factors:
  primary_factors:
    - factor: "[primary-factor-1]"
      weight: 0.3
      scoring:
        high: "[condition-for-high-score]"
        medium: "[condition-for-medium-score]"
        low: "[condition-for-low-score]"
        
    - factor: "[primary-factor-2]"
      weight: 0.25
      scoring:
        high: "[condition-for-high-score]"
        medium: "[condition-for-medium-score]"
        low: "[condition-for-low-score]"
  
  secondary_factors:
    - factor: "[secondary-factor-1]"
      weight: 0.15
      scoring:
        high: "[condition-for-high-score]"
        medium: "[condition-for-medium-score]"
        low: "[condition-for-low-score]"
```

### Comparative Positioning
```yaml
methodology_comparison:
  strengths_vs_alternatives:
    - vs_agile_scrum:
        advantages: ["[advantage-1]", "[advantage-2]"]
        scenarios: ["[when-better-than-scrum-1]", "[when-better-than-scrum-2]"]
        
    - vs_waterfall:
        advantages: ["[advantage-1]", "[advantage-2]"]
        scenarios: ["[when-better-than-waterfall-1]", "[when-better-than-waterfall-2]"]
        
    - vs_[other_methodology]:
        advantages: ["[advantage-1]", "[advantage-2]"]
        scenarios: ["[when-better-scenario-1]", "[when-better-scenario-2]"]
  
  combination_potential:
    - with_methodology: "[methodology-name]"
      combination_type: "sequential|parallel|hybrid"
      benefits: ["[benefit-1]", "[benefit-2]"]
      use_cases: ["[use-case-1]", "[use-case-2]"]
```

## Selection Questionnaire Integration

### Required Questions
```yaml
required_questions:
  - question_id: "methodology_experience"
    question: "[Question about methodology experience]"
    type: "multiple_choice"
    options: ["[option-1]", "[option-2]", "[option-3]"]
    scoring:
      "[option-1]": +2
      "[option-2]": +1
      "[option-3]": -1
      
  - question_id: "team_collaboration_style"
    question: "[Question about collaboration preferences]"
    type: "multiple_choice"
    options: ["[option-1]", "[option-2]", "[option-3]"]
    scoring:
      "[option-1]": +3
      "[option-2]": +1
      "[option-3]": 0
```

### Conditional Questions
```yaml
conditional_questions:
  - trigger_condition: "team_size > 10"
    question_id: "large_team_experience"
    question: "[Question about large team experience]"
    type: "yes_no"
    scoring:
      "yes": +2
      "no": -1
      
  - trigger_condition: "project_complexity == 'very_high'"
    question_id: "complexity_tolerance"
    question: "[Question about complexity handling]"
    type: "scale"
    range: [1, 5]
    scoring_formula: "score * 0.5"
```

## Recommendation Templates

### High Confidence Recommendation
```markdown
## 🎯 Excellent Match: [Methodology Name]

**Match Score**: [score]/100

**Why this methodology fits perfectly:**
- ✅ [Reason 1 based on context]
- ✅ [Reason 2 based on context]  
- ✅ [Reason 3 based on context]

**Your Context Alignment:**
- **Team Size**: [context-value] - [alignment-explanation]
- **Project Complexity**: [context-value] - [alignment-explanation]
- **Timeline**: [context-value] - [alignment-explanation]

**Implementation Approach:**
1. [Step 1 with timeline]
2. [Step 2 with timeline]
3. [Step 3 with timeline]

**Expected Benefits:**
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

**Get Started**: `/wizard apply-methodology [methodology-id]`
```

### Conditional Recommendation
```markdown
## 🤔 Good Match with Considerations: [Methodology Name]

**Match Score**: [score]/100

**This methodology could work well if:**
- [Condition 1 that needs addressing]
- [Condition 2 that needs addressing]

**Potential Challenges:**
- ⚠️ [Challenge 1] - [Mitigation strategy]
- ⚠️ [Challenge 2] - [Mitigation strategy]

**Alternative Approach:** Consider [hybrid-approach] or [alternative-methodology]

**Get Started**: `/wizard apply-methodology [methodology-id] --guided`
```

---

This template ensures methodologies integrate seamlessly with the PatternForge selector system while providing comprehensive guidance for implementation.