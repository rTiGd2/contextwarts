# Pattern Development Template

## Purpose
Complete template and guide for developers to create custom patterns for the PatternForge wizard system.

---

## Pattern Template Structure

### Directory Template
```
[pattern-name]/
├── pattern.md                  # Main implementation guide
├── dependencies.yaml           # Dependencies, conflicts, and metadata
├── detection.triggers          # Automatic detection rules
├── application/                # Application mode guidance
│   ├── creation.md            # New project application
│   ├── enhancement.md         # Existing project enhancement
│   ├── gap-filling.md         # Gap detection and filling
│   └── upgrade.md             # Pattern upgrade guidance
├── context/                   # Context gathering and customization
│   ├── questionnaire.md       # Context-gathering questions
│   ├── analysis.md            # Project analysis criteria
│   └── customization.md       # Context-based customization
├── validation/                # Quality and completion validation
│   ├── completion.md          # Pattern completion criteria
│   ├── quality.md             # Quality assessment
│   └── integration.md         # Integration validation
├── templates/                 # Code and configuration templates
│   ├── code/                  # Source code templates
│   ├── config/                # Configuration file templates
│   └── docs/                  # Documentation templates
└── examples/                  # Usage examples and demos
    ├── basic-usage.md
    ├── advanced-usage.md
    └── integration-examples.md
```

---

## Template Files

### 1. pattern.md Template
```markdown
# [Pattern Name] Pattern

## Overview
[Brief description of what this pattern provides and why it's valuable]

## Key Benefits
- [Primary benefit 1]
- [Primary benefit 2]
- [Primary benefit 3]

## When to Use
- ✅ **Good for**: [Scenario 1], [Scenario 2], [Scenario 3]
- ❌ **Avoid when**: [Anti-pattern 1], [Anti-pattern 2]

## Prerequisites
- [Required prerequisite 1]
- [Required prerequisite 2]
- [Optional prerequisite 3]

## Implementation Overview

### Core Components
1. **[Component 1]**: [Description and purpose]
2. **[Component 2]**: [Description and purpose]
3. **[Component 3]**: [Description and purpose]

### Architecture Impact
[How this pattern affects overall system architecture]

### Integration Points
[How this pattern integrates with other patterns or systems]

## Implementation Steps

### Phase 1: [Phase Name]
[Detailed implementation steps]

### Phase 2: [Phase Name]
[Detailed implementation steps]

### Phase 3: [Phase Name]
[Detailed implementation steps]

## Configuration Options

### Basic Configuration
```yaml
[pattern-name]:
  option1: value1
  option2: value2
```

### Advanced Configuration
```yaml
[pattern-name]:
  advanced:
    option1: advanced_value1
    option2: advanced_value2
```

## Validation Checklist
- [ ] [Validation item 1]
- [ ] [Validation item 2]
- [ ] [Validation item 3]

## Troubleshooting

### Common Issues
**Issue**: [Common problem description]
**Solution**: [Solution steps]

**Issue**: [Another common problem]
**Solution**: [Solution steps]

## Related Patterns
- **[Related Pattern 1]**: [Relationship description]
- **[Related Pattern 2]**: [Relationship description]

## Resources
- [Documentation link]
- [Tutorial link]
- [Community resource]

---
*Pattern created using PatternForge Template v1.0*
*For more templates: /wizard help templates*
```

### 2. dependencies.yaml Template
```yaml
pattern:
  id: "[pattern-id]"
  version: "1.0"
  category: "[technology|architecture|security|infrastructure|methodology]"
  name: "[Human Readable Pattern Name]"
  description: "[Brief pattern description]"
  author: "[Your Name]"
  created: "[YYYY-MM-DD]"
  updated: "[YYYY-MM-DD]"

dependencies:
  required:
    - pattern: "[required-pattern-1]"
      reason: "[Why this dependency is required]"
      auto_apply: true|false
      alternatives: ["[alternative-1]", "[alternative-2]"]
      
    - pattern: "[required-pattern-2]"
      reason: "[Why this dependency is required]"
      auto_apply: true|false

  optional:
    - pattern: "[optional-pattern-1]"
      reason: "[Why this enhances the pattern]"
      benefit: "[Benefit description]"
      compatibility: "high|medium|low"
      
    - pattern: "[optional-pattern-2]"
      reason: "[Why this enhances the pattern]"
      benefit: "[Benefit description]"
      applies_when: "[condition_when_recommended]"

  contextual:
    - condition: "[context_condition_1] OR [context_condition_2]"
      pattern: "[contextual-pattern-1]"
      reason: "[Why needed in this context]"
      auto_apply: true|false
      
    - condition: "[context_condition_3]"
      pattern: "[contextual-pattern-2]"
      reason: "[Why needed in this context]"
      auto_apply: true|false

conflicts:
  direct:
    - pattern: "[conflicting-pattern-1]"
      resolution: "replace|upgrade|merge"
      message: "[Explanation of conflict and resolution]"
      migration_path: "[path-to-migration-guide]"
      breaking_change: true|false
      
    - pattern: "[conflicting-pattern-2]"
      resolution: "replace|upgrade|merge"
      message: "[Explanation of conflict and resolution]"
      requires_manual_intervention: true|false

  soft:
    - pattern: "[soft-conflicting-pattern-1]"
      resolution: "complement|adjust|replace"
      message: "[Explanation of soft conflict]"
      adjustment: "[What adjustment is needed]"
      compatibility: true|false

application_modes:
  creation:
    complexity: "low|medium|high|very-high"
    time_estimate: "[time estimate]"
    prerequisites: ["[prerequisite-1]", "[prerequisite-2]"]
    suitable_for: ["[project-type-1]", "[project-type-2]"]
    team_expertise_required: "[expertise level description]"
    
  enhancement:
    complexity: "low|medium|high|very-high"
    time_estimate: "[time estimate]"
    compatibility_check: true|false
    suitable_for: ["[scenario-1]", "[scenario-2]"]
    migration_required: true|false
    
  gap_filling:
    detection_confidence: 0.0-1.0
    auto_apply: true|false
    validation_required: true|false
    suitable_for: ["[gap-scenario-1]", "[gap-scenario-2]"]
    
  upgrade:
    from_patterns: ["[upgradeable-pattern-1]", "[upgradeable-pattern-2]"]
    breaking_changes: true|false
    data_migration: true|false
    enhanced_features: ["[feature-1]", "[feature-2]"]

context_requirements:
  essential:
    - context_key_1: "[Question for gathering this context]"
    - context_key_2: "[Question for gathering this context]"
    - context_key_3: "[Question for gathering this context]"
    
  pattern_specific:
    - specific_context_1: "[Pattern-specific question]"
    - specific_context_2: "[Pattern-specific question]"
    
  technical:
    - technical_context_1: "[Technical context question]"
    - technical_context_2: "[Technical context question]"
    
  organizational:
    - org_context_1: "[Organizational context question]"
    - org_context_2: "[Organizational context question]"

validation_criteria:
  implementation:
    - criterion_1: "[What to validate for implementation]"
    - criterion_2: "[What to validate for implementation]"
    
  integration:
    - integration_criterion_1: "[Integration validation point]"
    - integration_criterion_2: "[Integration validation point]"
    
  quality:
    - quality_criterion_1: "[Quality validation point]"
    - quality_criterion_2: "[Quality validation point]"
    
  business_impact:
    - business_criterion_1: "[Business impact validation]"
    - business_criterion_2: "[Business impact validation]"
```

### 3. detection.triggers Template
```yaml
# Automatic Pattern Detection Rules
detection:
  confidence_threshold: 0.7
  
  file_patterns:
    high_confidence:
      - pattern: "[file-pattern-1]"
        confidence: 0.9
        description: "[Why this indicates the pattern]"
        
      - pattern: "[file-pattern-2]"
        confidence: 0.85
        description: "[Why this indicates the pattern]"
    
    medium_confidence:
      - pattern: "[file-pattern-3]"
        confidence: 0.7
        description: "[Why this suggests the pattern]"
        
      - pattern: "[file-pattern-4]"
        confidence: 0.6
        description: "[Why this suggests the pattern]"

  content_patterns:
    code_signatures:
      - pattern: "[regex-or-string-pattern-1]"
        confidence: 0.8
        file_types: ["[file-extension-1]", "[file-extension-2]"]
        description: "[What this code pattern indicates]"
        
      - pattern: "[regex-or-string-pattern-2]"
        confidence: 0.75
        file_types: ["[file-extension-3]"]
        description: "[What this code pattern indicates]"
    
    configuration_signatures:
      - pattern: "[config-pattern-1]"
        confidence: 0.9
        file_types: ["json", "yaml", "xml"]
        description: "[What this configuration indicates]"

  dependency_patterns:
    package_dependencies:
      - dependency: "[package-name-1]"
        confidence: 0.85
        package_managers: ["npm", "pip", "nuget", "composer"]
        description: "[Why this dependency indicates the pattern]"
        
      - dependency: "[package-name-2]"
        confidence: 0.8
        package_managers: ["npm", "pip"]
        description: "[Why this dependency indicates the pattern]"

  directory_structures:
    - structure: "[directory-pattern-1]"
      confidence: 0.8
      description: "[What this structure indicates]"
      
    - structure: "[directory-pattern-2]"
      confidence: 0.7
      description: "[What this structure indicates]"

  exclusion_patterns:
    # Patterns that indicate this pattern should NOT be detected
    - pattern: "[exclusion-pattern-1]"
      reason: "[Why this excludes the pattern]"
      
    - pattern: "[exclusion-pattern-2]"
      reason: "[Why this excludes the pattern]"

gap_detection:
  # Conditions that suggest this pattern is missing
  missing_indicators:
    - condition: "[condition-1] AND NOT [condition-2]"
      confidence: 0.9
      description: "[Why this gap should be filled]"
      
    - condition: "[condition-3]"
      confidence: 0.8
      description: "[Why this gap should be filled]"

upgrade_detection:
  # Conditions that suggest pattern needs upgrading
  upgrade_indicators:
    - from_pattern: "[old-pattern-id]"
      trigger_condition: "[condition-for-upgrade]"
      confidence: 0.8
      description: "[Why upgrade is recommended]"
```

---

## Application Mode Templates

### creation.md Template
```markdown
# [Pattern Name] - Creation Mode Application

## Purpose
Guide for applying [Pattern Name] pattern during new project creation.

## Prerequisites
- [Prerequisite 1]
- [Prerequisite 2]
- [Prerequisite 3]

## Context Assessment

### Required Context
- **[Context Key 1]**: [Description and importance]
- **[Context Key 2]**: [Description and importance]
- **[Context Key 3]**: [Description and importance]

### Context-Based Customization
- **If [context condition 1]**: [Customization approach]
- **If [context condition 2]**: [Customization approach]
- **If [context condition 3]**: [Customization approach]

## Implementation Process

### Phase 1: Foundation Setup
[Detailed steps for foundation setup]

1. [Step 1]
2. [Step 2]
3. [Step 3]

### Phase 2: Core Implementation
[Detailed steps for core implementation]

1. [Step 1]
2. [Step 2]
3. [Step 3]

### Phase 3: Integration and Validation
[Detailed steps for integration]

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Code Templates

### Template 1: [Template Name]
```[language]
[Template code with placeholders]
```

### Template 2: [Template Name]
```[language]
[Template code with placeholders]
```

## Configuration Templates

### Basic Configuration
```yaml
[Configuration template]
```

### Advanced Configuration
```yaml
[Advanced configuration template]
```

## Validation Steps
1. [Validation step 1]
2. [Validation step 2]
3. [Validation step 3]

## Success Criteria
- [ ] [Success criterion 1]
- [ ] [Success criterion 2]
- [ ] [Success criterion 3]

## Common Issues
- **Issue**: [Problem description]
  **Solution**: [Solution approach]

## Next Steps
After successful application:
1. [Next step 1]
2. [Next step 2]
3. [Next step 3]
```

---

## Pattern Development Workflow

### 1. Pattern Creation Command
```bash
/wizard create-pattern [pattern-name] [category]
```

**Generated Structure:**
- Creates complete directory structure from templates
- Populates template files with pattern-specific placeholders
- Sets up basic validation and testing framework

### 2. Pattern Development Process
```yaml
development_workflow:
  1_design:
    - define_pattern_purpose
    - identify_dependencies_and_conflicts
    - design_implementation_approach
    
  2_implement:
    - create_pattern_documentation
    - define_detection_rules
    - implement_application_modes
    - create_code_templates
    
  3_test:
    - test_pattern_detection
    - validate_application_modes
    - verify_dependency_resolution
    - test_context_gathering
    
  4_integrate:
    - install_pattern_locally
    - test_with_real_projects
    - gather_feedback
    - iterate_and_improve
    
  5_publish:
    - document_pattern_thoroughly
    - create_usage_examples
    - submit_for_review
    - publish_to_pattern_library
```

### 3. Pattern Testing Commands
```bash
# Test pattern detection
/wizard test-detection [pattern-name] [project-path]

# Test pattern application
/wizard test-application [pattern-name] [mode] [project-path]

# Validate pattern definition
/wizard validate-pattern [pattern-path]

# Generate pattern documentation
/wizard generate-docs [pattern-name]
```

---

## Publishing Guidelines

### Pattern Quality Standards
1. **Documentation Completeness**: All template sections filled
2. **Detection Accuracy**: >80% detection accuracy on test projects
3. **Application Success**: Successful application in all supported modes
4. **Integration Testing**: Compatible with existing pattern library
5. **Example Projects**: At least 2 working example implementations

### Submission Process
1. **Fork Repository**: Fork the pattern-based-wizard repository
2. **Create Pattern**: Use pattern development templates
3. **Test Thoroughly**: Test on multiple project types
4. **Document Examples**: Create comprehensive usage examples
5. **Submit PR**: Submit pull request with pattern implementation
6. **Review Process**: Community and maintainer review
7. **Integration**: Merge into main pattern library

### Community Guidelines
- Follow existing pattern naming conventions
- Provide clear, actionable documentation
- Include comprehensive examples
- Test across multiple environments
- Respond to review feedback promptly

---

This template system enables developers to create high-quality, consistent patterns that integrate seamlessly with the PatternForge wizard system.