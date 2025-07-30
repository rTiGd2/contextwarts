# Contextwarts Wizard Help System

## Purpose
Comprehensive help and command reference system for the Contextwarts wizard, providing contextual assistance for all wizard capabilities and pattern operations.

---

## Help Command Structure

### Primary Help Command
```
/wizard help
```

**Response Format:**
```
🧙‍♂️ Contextwarts Wizard v1.0 by Tig Campbell-Moore

USAGE:
  /wizard [command] [options]
  /wizard help [topic]

COMMANDS:
  create          Create new project with patterns
  enhance         Add patterns to existing project  
  analyze         Analyze project and detect patterns
  validate        Validate pattern adherence
  list            List available patterns
  info            Get information about specific pattern
  load-context    Load existing project context
  refresh-context Update offline development context
  generate-tasks  Generate structured task list from PRD
  execute-tasks   Execute tasks with disciplined protocol
  update-tasks    Maintain task list as living documentation

HELP TOPICS:
  patterns        Available patterns and categories
  modes           Pattern application modes (create/enhance/gap/upgrade)
  methodology     Development methodology patterns
  task-management Task-driven development and execution
  context-management Context clearing best practices for performance
  examples        Usage examples and workflows
  troubleshooting Common issues and solutions
  templates       Creating custom patterns and extensions

EXAMPLES:
  /clear && /wizard create startup web-app
  /clear && /wizard enhance add authentication
  /clear && /wizard generate-tasks prd-user-auth.md
  /clear && /wizard execute-tasks tasks-prd-user-auth.md
  /wizard help patterns
  /wizard validate patterns

💡 TIP: Use /clear before wizard commands for optimal performance and accuracy

For detailed help: /wizard help [topic]
GitHub: https://github.com/rTiGd2/contextwarts
```

---

## Detailed Help Topics

### `/wizard help patterns`
```
🎯 PatternForge Pattern Library

PATTERN CATEGORIES:
  technology/        Technology stack patterns (23 patterns)
  architecture/      Architectural approach patterns (8 patterns)  
  security/          Security implementation patterns (12 patterns)
  infrastructure/    Deployment and infrastructure patterns (15 patterns)
  methodology/       Development methodology patterns (5 patterns)

POPULAR PATTERNS:
  • modern-web-stack           - React/TypeScript/Node.js foundation
  • advanced-authentication    - WebAuthn, MFA, SSO integration
  • container-first-deployment - Docker/Kubernetes with GitOps
  • microservices-architecture - Service boundaries and communication
  • test-driven-development    - TDD with Red-Green-Refactor cycle

USAGE:
  /wizard list [category]           - List patterns in category
  /wizard info [pattern-name]       - Get pattern details
  /wizard help examples            - See pattern usage examples

Pattern Count: 63 total patterns available
Last Updated: [current-date]
```

### `/wizard help modes`
```
🔄 Pattern Application Modes

PatternForge applies patterns in four intelligent modes:

1. CREATION MODE 🆕
   Purpose: Bootstrap new projects with foundational patterns
   Usage: /wizard create [project-type] [patterns...]
   Example: /wizard create startup-mvp modern-web-stack basic-security
   
2. ENHANCEMENT MODE ⚡
   Purpose: Add new capabilities to existing projects  
   Usage: /wizard enhance [capability] [patterns...]
   Example: /wizard enhance authentication advanced-authentication
   
3. GAP MODE 🔍
   Purpose: Fill missing or incomplete implementations
   Usage: /wizard analyze (detects gaps automatically)
   Example: Detects missing HTTPS and suggests basic-security pattern
   
4. UPGRADE MODE 🚀
   Purpose: Enhance existing patterns with advanced features
   Usage: /wizard upgrade [current-pattern] to [advanced-pattern]
   Example: /wizard upgrade basic-auth to advanced-authentication

INTELLIGENT FEATURES:
• Context-aware pattern selection
• Automatic dependency resolution  
• Conflict detection and resolution
• Compatibility validation
• Progressive implementation guidance

Use /wizard help examples for detailed workflows.
```

### `/wizard help methodology`
```
🔄 Development Methodology Patterns

PatternForge includes comprehensive methodology integration:

AVAILABLE METHODOLOGIES:
  • test-driven-development (TDD)        - Red-Green-Refactor cycle
  • behavior-driven-development (BDD)    - Given-When-Then scenarios  
  • domain-driven-design (DDD)           - Strategic and tactical design
  • acceptance-test-driven-development   - Whole-team collaboration
  • example-driven-development (EDD)     - Concrete examples as specs

METHODOLOGY SELECTOR:
  /wizard select-methodology             - Interactive methodology selection
  /wizard help methodology-comparison    - Compare methodologies
  /wizard methodology status            - Show current methodology

INTEGRATION FEATURES:
• Team size and expertise consideration
• Project complexity assessment
• Stakeholder involvement evaluation
• Hybrid methodology recommendations
• Implementation roadmaps and training

EXAMPLES:
  Small team, complex domain     → Domain-Driven Design + TDD
  High stakeholder involvement   → Behavior-Driven Development  
  Regulatory requirements       → Example-Driven Development
  
Use /wizard help examples for methodology workflows.
```

### `/wizard help examples`
```
📝 PatternForge Usage Examples

NEW PROJECT CREATION:
  /wizard create startup web-app
  > Recommends: modern-web-stack + monolith-first + basic-security
  
  /wizard create enterprise api-service  
  > Recommends: microservices + advanced-auth + enterprise-monitoring

ENHANCE EXISTING PROJECT:
  /wizard enhance security
  > Analyzes current setup and recommends security patterns
  
  /wizard enhance pwa
  > Adds progressive web app capabilities to existing React app

METHODOLOGY INTEGRATION:
  /wizard select-methodology
  > Interactive methodology selection based on project context
  
  /wizard apply-methodology tdd
  > Applies Test-Driven Development with team setup

ANALYSIS AND VALIDATION:
  /wizard analyze
  > Detects current patterns and identifies gaps
  
  /wizard validate patterns
  > Validates adherence to applied patterns

CONTEXT MANAGEMENT:
  /wizard load-context
  > Loads existing project context for AI assistance
  
  /wizard refresh-context
  > Updates offline development context with latest changes

PATTERN INFORMATION:
  /wizard list security
  > Lists all security patterns with descriptions
  
  /wizard info advanced-authentication
  > Detailed information about authentication pattern

COMPLETE WORKFLOWS:
  1. New Project: /wizard create → methodology selection → pattern application
  2. Enhancement: /wizard analyze → gap identification → pattern enhancement  
  3. Team Onboarding: /wizard load-context → README bootstrap → development start
```

### `/wizard help context-management`
```
🧠 Context Management Best Practices

For optimal Contextwarts performance and accuracy, follow these context management guidelines:

BEFORE WIZARD COMMANDS:
  /clear                              - Clear context before any wizard operation
  
  Why: Contextwarts loads extensive pattern libraries and project analysis. 
  Clean context ensures:
  • Faster loading and processing
  • More accurate pattern recommendations  
  • Reduced context confusion between different projects
  • Optimal AI assistant performance

RECOMMENDED WORKFLOW:
  /clear && /wizard [command]         - One-line context clearing + command
  
  Examples:
  /clear && /wizard create startup web-app
  /clear && /wizard enhance authentication
  /clear && /wizard generate-tasks prd-file.md

CONTEXT LOADING COMMANDS (No /clear needed):
  /wizard help                        - Help commands don't need context clearing
  /wizard load-context               - Explicitly loads project context
  /wizard info [pattern-name]        - Pattern info commands

WHEN TO ALWAYS USE /clear:
  • Switching between different projects
  • Starting any pattern application workflow
  • Generating tasks from PRD
  • Beginning any major wizard operation
  • When AI responses seem confused or irrelevant

PERFORMANCE BENEFITS:
  • 3-5x faster wizard command processing
  • More accurate pattern detection and recommendations
  • Reduced memory usage during complex operations
  • Better AI assistant response quality
```

### `/wizard help troubleshooting`
```
🔧 PatternForge Troubleshooting

COMMON ISSUES:

❌ "Pattern not found"
  • Check pattern name spelling: /wizard list [category]
  • Verify pattern exists: /wizard info [pattern-name]
  • Update pattern library: /wizard update

❌ "Context not found" 
  • Ensure .aiwizard directory exists in project root
  • Run: /wizard load-context to regenerate
  • Check file permissions on .aiwizard directory

❌ "Pattern conflict detected"
  • Review conflict resolution: /wizard info [conflicting-pattern]
  • Use upgrade mode: /wizard upgrade [old-pattern] to [new-pattern]
  • Manual resolution: /wizard resolve-conflict [pattern1] [pattern2]

❌ "Validation failed"
  • Check specific validation errors: /wizard validate patterns --verbose
  • Review pattern implementation: /wizard info [failing-pattern]
  • Update implementation: /wizard refresh-pattern [pattern-name]

❌ "Installation issues"
  • Verify installation: /wizard --version
  • Check permissions: ensure ~/.patternforge/ is accessible
  • Reinstall: See GitHub installation guide

GETTING HELP:
  • GitHub Issues: https://github.com/rTiGd2/pattern-based-wizard/issues
  • Documentation: https://github.com/rTiGd2/pattern-based-wizard/docs
  • Examples: https://github.com/rTiGd2/pattern-based-wizard/examples

DIAGNOSTIC COMMANDS:
  /wizard diagnose              - Run system diagnostics
  /wizard validate installation - Verify system setup
  /wizard logs                 - Show recent wizard activity
```

### `/wizard help task-management`
```
📋 Task-Driven Development Integration

Contextwarts includes sophisticated task management capabilities for structured development.

TASK GENERATION FROM PRD:
  /wizard generate-tasks [prd-file]     - Generate pattern-aware task list from PRD
  
  Process:
  1. Analyze PRD + Current codebase + Applied patterns
  2. Generate 5-7 high-level parent tasks
  3. Wait for user confirmation: "Ready for sub-tasks? Type 'Go'"
  4. Generate detailed sub-tasks with pattern guidance
  5. Identify relevant files (implementation + tests)
  6. Create tasks-[prd-name].md in /tasks/ directory

DISCIPLINED TASK EXECUTION:
  /wizard execute-tasks [task-file]     - Execute tasks with quality gates
  
  Protocol:
  1. Load next incomplete sub-task
  2. Request user permission to proceed
  3. Provide pattern-specific implementation guidance
  4. Mark sub-task complete when finished
  5. For parent task completion: Run tests → Git add → Clean → Commit
  6. Request permission before starting next sub-task

TASK MAINTENANCE:
  /wizard update-tasks [task-file]      - Maintain task list as living documentation
  
  Updates:
  • Mark completed tasks as [x]
  • Add newly discovered tasks
  • Update "Relevant Files" section
  • Sync with actual codebase state

FEATURES:
  • Two-phase generation with user confirmation
  • Pattern-aware sub-task guidance
  • Hierarchical parent-child task relationships
  • Quality integration with test suite execution
  • Git workflow integration with conventional commits
  • File relevance identification and tracking
  • Junior developer friendly with detailed guidance

COMPLETION PROTOCOL:
  Sub-task: Implement → Mark [x] → Request permission
  Parent task: All sub-tasks [x] → Run tests → Git commit → Mark [x]

QUALITY GATES:
  • All tests must pass before parent task completion
  • Pattern adherence validation
  • Conventional commit format with detailed messages
  • Clean code - no temporary files or debug code
```

### `/wizard help templates`
```
🛠️ Creating Custom Patterns and Extensions

Contextwarts supports custom pattern development and wizard extensions.

DEVELOPER TEMPLATES:
  ~/.contextwarts/templates/pattern-template/     - New pattern template
  ~/.contextwarts/templates/methodology/          - Custom methodology template  
  ~/.contextwarts/templates/integration/          - Third-party integration template
  ~/.contextwarts/templates/wizard-extension/     - Wizard command extension template

CREATING A NEW PATTERN:
  1. /wizard create-pattern [pattern-name] [category]
  2. Edit generated template files
  3. Test with: /wizard test-pattern [pattern-name]
  4. Install with: /wizard install-pattern [pattern-path]

PATTERN STRUCTURE:
  my-pattern/
  ├── pattern.md              # Main implementation guide
  ├── dependencies.yaml       # Dependencies and conflicts
  ├── detection.triggers      # Auto-detection rules
  ├── application/            # Mode-specific guidance
  │   ├── creation.md
  │   ├── enhancement.md
  │   ├── gap-filling.md
  │   └── upgrade.md
  ├── context/               # Context gathering
  │   ├── questionnaire.md
  │   └── customization.md
  └── validation/            # Quality checks
      ├── completion.md
      └── integration.md

METHODOLOGY TEMPLATES:
  - Team collaboration patterns
  - Process workflow definitions  
  - Quality gate specifications
  - Tool integration guides

WIZARD EXTENSIONS:
  - Custom commands and workflows
  - Third-party service integrations
  - Organization-specific patterns
  - Industry-specific methodologies

EXAMPLES:
  /wizard create-pattern company-security security
  /wizard create-methodology agile-scrum
  /wizard create-extension jira-integration

See: /wizard help pattern-development for detailed guide.
```

---

## Context-Sensitive Help

### Project Context Detection
```yaml
help_context_detection:
  new_project:
    - show creation mode examples
    - highlight popular starter patterns
    - emphasize methodology selection
    
  existing_project:
    - show enhancement mode examples  
    - suggest gap analysis
    - highlight context loading
    
  pattern_project:
    - show validation commands
    - highlight refresh-context
    - emphasize adherence checking
```

### Intelligent Help Suggestions
```yaml
intelligent_suggestions:
  incomplete_command:
    trigger: "/wizard cr"
    suggestion: "Did you mean: /wizard create ?"
    
  pattern_typo:
    trigger: "/wizard info advance-auth"
    suggestion: "Did you mean: advanced-authentication ?"
    
  context_missing:
    trigger: "No .aiwizard directory found"
    suggestion: "Run: /wizard load-context or /wizard create"
```

---

## Help System Integration

### AI Assistant Integration
```markdown
# Help system prompt integration
When user requests help (/wizard help [topic]):
1. Load help content from core/wizard-help-system.md
2. Provide contextual information based on project state
3. Include relevant examples and next steps
4. Offer to demonstrate commands or create examples
5. Reference GitHub documentation for advanced topics
```

### Command Completion
```yaml
command_completion:
  commands: [create, enhance, analyze, validate, list, info, load-context, refresh-context, help]
  
  categories: [technology, architecture, security, infrastructure, methodology]
  
  patterns: # Dynamic from pattern library
    - advanced-authentication
    - modern-web-stack  
    - container-first-deployment
    - microservices-architecture
    - test-driven-development
    # ... all 63 patterns
```

---

This comprehensive help system ensures users can discover and effectively use all PatternForge capabilities, from basic pattern application to advanced customization and extension development.