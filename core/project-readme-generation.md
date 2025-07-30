# Project README Generation for Wizard Projects

## Purpose
Generate comprehensive README.md sections that inform developers about wizard-generated capabilities and provide clear instructions for leveraging AI development context and pattern adherence systems.

---

## README Generation Strategy

### Integration Approach
```yaml
readme_generation:
  strategy: "enhance_existing_or_create"
  
  if_readme_exists:
    - detect_wizard_section_presence
    - update_wizard_section_if_exists
    - insert_wizard_section_after_title_if_missing
    - preserve_existing_project_content
  
  if_no_readme:
    - create_complete_readme_with_wizard_section
    - include_standard_project_sections
    - generate_project_specific_content_placeholders
    - add_wizard_capabilities_prominently
```

### Content Customization
```yaml
readme_customization:
  dynamic_content:
    - applied_patterns_list: "from patterns-applied.yaml"
    - methodology_name: "from methodology-context.md" 
    - architecture_summary: "from architecture-decisions.md"
    - team_size_context: "from project-requirements.yaml"
    - technology_stack: "from project-resume-context.md"
  
  placeholders:
    - PATTERN_LIST_PLACEHOLDER: "Auto-generated pattern summary"
    - METHODOLOGY_PLACEHOLDER: "Active methodology name and phase"
    - PROJECT_SPECIFIC_CONTENT_PLACEHOLDER: "Existing/standard project content"
    - TECH_STACK_PLACEHOLDER: "Technology stack summary"
```

---

## Generated README Structure

### Wizard Section Placement
```markdown
# [Project Name]

[Brief project description - existing or generated]

## 🧙‍♂️ AI-Powered Development Ready
[Wizard capabilities section - ALWAYS PRESENT]

## 🚀 Quick Start
[Standard project quick start - enhanced with wizard context]

## 📁 Project Structure  
[Enhanced with .aiwizard directory explanation]

## 🎯 Applied Patterns
[Dynamic list of applied patterns with justifications]

## 🛠️ Development Workflow
[Pattern-aligned development process]

## 📚 Documentation
[Enhanced documentation section with wizard context]

## 🆘 Getting Help
[Wizard-specific help and troubleshooting]

## [Standard Project Sections]
[Installation, Usage, Contributing, etc.]
```

### AI Bootstrap Instructions

#### Primary AI Loading Prompt
```markdown
### 🤖 AI Assistant Quick Start

**Copy this prompt to any AI assistant:**

```
I'm working on a wizard-generated project. Please load my complete development context:

1. **Primary Context**: Read `.aiwizard/standalone-context/project-resume-context.md`
   - This contains complete project understanding, applied patterns, architecture, and development standards

2. **Pattern Configuration**: Review `.aiwizard/core/patterns-applied.yaml`
   - Lists all active patterns with their configurations and justifications

3. **Development Methodology**: Check `.aiwizard/standalone-context/methodology-context.md`
   - Contains team agreements, workflow processes, and methodology implementation

4. **Feature Development**: Reference `.aiwizard/standalone-context/feature-addition-guide.md`
   - Step-by-step guide for adding features within established patterns

After loading this context, you'll understand:
✓ All applied architectural patterns and their implementations
✓ Development methodology and team agreements  
✓ Code standards, testing strategies, and quality requirements
✓ Integration patterns and technical constraints
✓ Project history and architectural decisions

This enables you to provide pattern-aligned, methodology-aware development assistance that maintains project quality and consistency.

Current task: [Describe what you want help with]
```

**Alternative: Command-line bootstrap**
```bash
wizard load-project-context
```
```

#### Specialized AI Prompts
```markdown
### 🎯 Specialized AI Assistance

#### For Feature Development
```
Load my project context from .aiwizard/standalone-context/project-resume-context.md, then help me implement [FEATURE_DESCRIPTION] following the feature development guide in .aiwizard/standalone-context/feature-addition-guide.md. Ensure the implementation maintains adherence to all applied patterns listed in .aiwizard/core/patterns-applied.yaml.
```

#### For Architecture Decisions
```
Load my project context and review the architecture decisions in .aiwizard/core/architecture-decisions.md. Help me evaluate [ARCHITECTURE_QUESTION] within the constraints of applied patterns and established architectural principles. Consider impact on existing patterns and suggest pattern-aligned solutions.
```

#### For Requirements Updates
```
Load my project context and PRD enhancement framework from .aiwizard/standalone-context/prd-enhancement-context.md. Help me refine/update requirements for [REQUIREMENT_AREA] while maintaining alignment with applied patterns and development methodology.
```
```

---

## README Content Generation

### Pattern Summary Generation
```yaml
pattern_summary_generation:
  format: "bulleted_list_with_descriptions"
  
  template: |
    **Architecture Patterns:**
    - 🏗️ **[Pattern Name]**: [Brief description and benefit]
    
    **Security Patterns:**  
    - 🔒 **[Pattern Name]**: [Brief description and benefit]
    
    **Infrastructure Patterns:**
    - 🚀 **[Pattern Name]**: [Brief description and benefit]
    
    **Development Methodology:**
    - 🔄 **[Methodology Name]**: [Implementation phase and team approach]
  
  data_source: ".aiwizard/core/patterns-applied.yaml"
  max_patterns_displayed: 8
  grouping: "by_category"
```

### Technology Stack Summary
```yaml
tech_stack_generation:
  format: "categorized_list"
  
  template: |
    **Backend:** [Languages, frameworks, databases]
    **Frontend:** [Languages, frameworks, libraries]  
    **Infrastructure:** [Deployment, monitoring, CI/CD tools]
    **Development:** [Testing, linting, development tools]
  
  data_sources:
    - ".aiwizard/standalone-context/project-resume-context.md"
    - ".aiwizard/core/patterns-applied.yaml"
    - project_files_analysis
```

### Development Workflow Summary
```yaml
workflow_generation:
  format: "step_by_step_process"
  
  template: |
    1. **Feature Planning**: [Methodology-specific planning approach]
    2. **Pattern Assessment**: [How to evaluate pattern applicability]
    3. **Implementation**: [Development workflow with quality gates]
    4. **Validation**: [Testing and pattern adherence verification]
    5. **Documentation**: [Documentation update requirements]
  
  customization_based_on:
    - applied_methodology
    - team_size
    - project_complexity
    - quality_requirements
```

---

## Generation Process Integration

### Wizard Integration Point
```yaml
readme_generation_step:
  trigger: "offline_context_generation_complete"
  timing: "after_context_generation_before_completion"
  
  process:
    - detect_existing_readme
    - analyze_existing_content
    - generate_wizard_section_content
    - customize_based_on_applied_patterns
    - integrate_or_create_readme
    - validate_content_completeness
    - add_to_git_if_applicable
```

### Content Validation
```yaml
content_validation:
  required_elements:
    - ai_bootstrap_instructions: "clear and copy-pasteable"
    - wizard_capabilities_explanation: "prominent and informative"
    - applied_patterns_summary: "accurate and up-to-date"
    - development_workflow_guide: "methodology-aligned"
    - help_and_troubleshooting: "comprehensive coverage"
  
  quality_checks:
    - bootstrap_prompt_completeness: "contains all required context files"
    - pattern_information_accuracy: "matches patterns-applied.yaml"
    - methodology_alignment: "consistent with methodology-context.md"
    - user_experience_quality: "clear instructions and easy discovery"
```

---

## README Maintenance

### Dynamic Updates
```yaml
readme_maintenance:
  auto_update_triggers:
    - pattern_application_changes
    - methodology_evolution  
    - context_regeneration
    - architecture_decision_updates
  
  update_strategy:
    - preserve_manual_customizations
    - update_dynamic_content_only
    - maintain_version_history
    - validate_after_updates
```

### Manual Customization Support
```yaml
customization_support:
  protected_sections:
    - project_specific_installation_instructions
    - custom_usage_examples
    - project_specific_contributing_guidelines
    - custom_troubleshooting_additions
  
  customization_markers:
    - "<!-- WIZARD_GENERATED_CONTENT_START -->"
    - "<!-- WIZARD_GENERATED_CONTENT_END -->"
    - "<!-- CUSTOM_CONTENT_PROTECTED -->"
```

---

## Example Generated README Section

### Complete Wizard Section
```markdown
## 🧙‍♂️ AI-Powered Development Ready

This project was created using the **Pattern-Based Project Wizard** and is equipped with comprehensive AI development capabilities. The project maintains intelligent pattern adherence, methodology integration, and provides complete context for AI-assisted development.

### 🚀 Quick Start for AI Development

**For any AI assistant, copy this prompt:**
[Generated AI bootstrap prompt with project-specific context]

**For command-line users:**
```bash
wizard load-project-context
```

### 🎯 Applied Patterns

**Architecture Patterns:**
- 🏗️ **Microservices Architecture**: Service boundaries aligned with domain contexts
- 🏗️ **Clean Architecture**: Dependency inversion with domain-driven layers

**Security Patterns:**  
- 🔒 **Advanced Authentication**: WebAuthn, MFA, and SSO integration
- 🔒 **Zero Trust Security**: Comprehensive security validation at all boundaries

**Infrastructure Patterns:**
- 🚀 **Container-First Deployment**: Docker and Kubernetes with GitOps
- 📊 **Enterprise Monitoring**: OpenTelemetry with comprehensive observability

**Development Methodology:**
- 🔄 **Domain-Driven Design + TDD**: Strategic domain modeling with test-first implementation

### 🛠️ Development Workflow

1. **Load Context**: Use AI prompt above or `wizard load-project-context`
2. **Plan Feature**: Follow domain-driven design principles for feature planning
3. **Implement with TDD**: Red-Green-Refactor cycle within domain boundaries
4. **Validate Patterns**: Ensure microservice boundaries and clean architecture adherence
5. **Security Review**: Validate against zero trust and authentication patterns
6. **Update Documentation**: Maintain living documentation and pattern adherence

### 📚 Documentation & Help

- **AI Development Context**: `.aiwizard/standalone-context/project-resume-context.md`
- **Feature Development Guide**: `.aiwizard/standalone-context/feature-addition-guide.md` 
- **Pattern Validation**: `wizard validate-patterns`
- **Troubleshooting**: `.aiwizard/ai-prompts/troubleshooting.md`

*This project maintains pattern adherence and provides comprehensive AI development context for consistent, high-quality development.*
```

---

This README generation system ensures that wizard-generated projects are immediately discoverable and usable by developers and AI assistants, bridging the gap between sophisticated pattern-based generation and practical day-to-day development usage.