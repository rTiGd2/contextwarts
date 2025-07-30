# Wizard Extension Development Template

## Purpose
Template for creating custom wizard commands and extensions that integrate with the PatternForge wizard system.

---

## Extension Types

### 1. Custom Commands
Add new `/wizard [command]` functionality for specific workflows or integrations.

### 2. Pattern Categories
Create new pattern categories beyond the core five (technology, architecture, security, infrastructure, methodology).

### 3. Integration Extensions
Connect PatternForge with third-party services, tools, or platforms.

### 4. Workflow Extensions
Add specialized workflows for specific industries, organizations, or use cases.

---

## Extension Structure

### Directory Template
```
[extension-name]/
├── extension.yaml              # Extension metadata and configuration
├── commands/                   # Custom command definitions
│   ├── [command-name].md      # Command implementation guide
│   ├── [command-name].yaml    # Command configuration
└── handlers/                  # Command handler logic
    └── [command-name]-handler.js
├── patterns/                   # Extension-specific patterns (if applicable)
│   └── [pattern-category]/
│       └── [pattern-name]/
├── integrations/               # Third-party integrations (if applicable)
│   ├── [service-name].yaml    # Integration configuration
│   └── [service-name].md      # Integration documentation
├── workflows/                  # Custom workflows (if applicable)
│   ├── [workflow-name].yaml   # Workflow definition
│   └── [workflow-name].md     # Workflow documentation
├── templates/                  # Extension-specific templates
│   ├── code/
│   ├── config/
│   └── docs/
├── validation/                 # Extension validation logic
│   ├── validators.js
│   └── validation-rules.yaml
└── examples/                   # Usage examples
    ├── basic-usage.md
    └── advanced-usage.md
```

---

## Extension Templates

### 1. extension.yaml Template
```yaml
extension:
  id: "[extension-id]"
  name: "[Extension Display Name]"
  version: "1.0"
  author: "[Your Name]"
  description: "[Brief description of extension purpose and functionality]"
  created: "[YYYY-MM-DD]"
  updated: "[YYYY-MM-DD]"
  
  compatibility:
    patternforge_version: ">=1.0"
    required_dependencies: ["[dependency-1]", "[dependency-2]"]
    optional_dependencies: ["[optional-1]", "[optional-2]"]

  extension_type: "command|pattern-category|integration|workflow"
  
  installation:
    install_location: "~/.patternforge/extensions/"
    requires_system_access: true|false
    requires_network_access: true|false
    configuration_required: true|false

commands:
  - command: "[command-name-1]"
    description: "[Command description]"
    usage: "/wizard [command-name-1] [arguments]"
    handler: "handlers/[command-name-1]-handler.js"
    validation: "validation/[command-name-1]-validator.js"
    
  - command: "[command-name-2]"
    description: "[Command description]"
    usage: "/wizard [command-name-2] [arguments]"
    handler: "handlers/[command-name-2]-handler.js"

patterns:
  - category: "[new-category-name]"
    description: "[Category description]"
    pattern_count: 0
    patterns_location: "patterns/[new-category-name]/"
    
integrations:
  - service: "[service-name-1]"
    type: "api|webhook|cli|database"
    description: "[Integration description]"
    configuration_file: "integrations/[service-name-1].yaml"
    authentication_required: true|false
    
workflows:
  - workflow: "[workflow-name-1]"
    description: "[Workflow description]"
    trigger: "command|pattern-application|schedule|event"
    definition_file: "workflows/[workflow-name-1].yaml"

permissions:
  file_system:
    read: ["[path-pattern-1]", "[path-pattern-2]"]
    write: ["[path-pattern-3]", "[path-pattern-4]"]
  network:
    endpoints: ["[allowed-endpoint-1]", "[allowed-endpoint-2]"]
  system:
    commands: ["[allowed-command-1]", "[allowed-command-2]"]

configuration:
  required_settings:
    - setting: "[setting-name-1]"
      type: "string|number|boolean|array|object"
      description: "[Setting description]"
      default: "[default-value]"
      
  optional_settings:
    - setting: "[setting-name-2]"
      type: "string|number|boolean|array|object"
      description: "[Setting description]"
      default: "[default-value]"

help_integration:
  help_topics:
    - topic: "[help-topic-1]"
      description: "[Topic description]"
      content_file: "help/[help-topic-1].md"
      
  examples:
    - example: "[example-name-1]"
      description: "[Example description]"
      content_file: "examples/[example-name-1].md"
```

### 2. Custom Command Template

#### [command-name].yaml
```yaml
command:
  name: "[command-name]"
  aliases: ["[alias-1]", "[alias-2]"]
  description: "[Detailed command description]"
  category: "creation|enhancement|analysis|validation|utility"
  
  usage:
    syntax: "/wizard [command-name] [required-arg] [optional-arg]"
    examples:
      - "/wizard [command-name] example-value"
      - "/wizard [command-name] example-value --option"
  
  arguments:
    required:
      - name: "[arg-name-1]"
        type: "string|number|boolean|choice"
        description: "[Argument description]"
        choices: ["[choice-1]", "[choice-2]"] # if type is choice
        
    optional:
      - name: "[arg-name-2]"
        type: "string|number|boolean|choice"
        description: "[Argument description]"
        default: "[default-value]"
        
  options:
    - name: "[option-name-1]"
      short: "[short-form]"
      type: "flag|value"
      description: "[Option description]"
      default: "[default-value]"

  validation:
    pre_execution:
      - validator: "validate_project_context"
        required: true
        error_message: "[Error message if validation fails]"
        
      - validator: "validate_[custom_condition]"
        required: false
        warning_message: "[Warning message if validation fails]"
        
  execution:
    handler: "handlers/[command-name]-handler.js"
    timeout: 300 # seconds
    async: true|false
    
  output:
    format: "text|json|yaml|markdown"
    success_message: "[Success message template]"
    error_message: "[Error message template]"
    
  help:
    summary: "[Brief command summary]"
    detailed_help: "help/[command-name]-help.md"
    examples_file: "examples/[command-name]-examples.md"
```

#### [command-name].md
```markdown
# [Command Name] Command Implementation

## Purpose
[Detailed description of what this command does and why it's useful]

## Use Cases
- **[Use Case 1]**: [Description]
- **[Use Case 2]**: [Description]
- **[Use Case 3]**: [Description]

## Implementation Logic

### Pre-execution Validation
1. [Validation step 1]
2. [Validation step 2] 
3. [Validation step 3]

### Core Execution Steps
1. [Execution step 1]
2. [Execution step 2]
3. [Execution step 3]

### Post-execution Actions
1. [Post-action 1]
2. [Post-action 2]
3. [Post-action 3]

## Context Requirements
- **[Context Item 1]**: [Why needed and how used]
- **[Context Item 2]**: [Why needed and how used]
- **[Context Item 3]**: [Why needed and how used]

## Integration Points
- **Pattern System**: [How command integrates with patterns]
- **Project Context**: [How command uses project context]
- **File System**: [What files/directories are accessed]
- **External Services**: [Any external integrations]

## Error Handling
- **[Error Type 1]**: [How to handle] → [Error message]
- **[Error Type 2]**: [How to handle] → [Error message]
- **[Error Type 3]**: [How to handle] → [Error message]

## Output Format
```
[Example of command output format]
```

## Examples

### Basic Usage
```bash
/wizard [command-name] basic-example
```
**Expected Output:**
```
[Expected output example]
```

### Advanced Usage
```bash
/wizard [command-name] advanced-example --option value
```
**Expected Output:**
```
[Expected output example]
```

## Testing
- **Unit Tests**: [Test coverage description]
- **Integration Tests**: [Integration test scenarios]
- **Manual Testing**: [Manual test procedures]

## Performance Considerations
- **Execution Time**: [Expected execution time]
- **Resource Usage**: [Memory, CPU, network usage]
- **Scalability**: [How performance scales with project size]
```

### 3. Integration Extension Template

#### [service-name].yaml
```yaml
integration:
  service: "[service-name]"
  type: "api|webhook|cli|database|file-system"
  version: "1.0"
  description: "[Integration description and purpose]"
  
  authentication:
    type: "api-key|oauth|token|username-password|none"
    required: true|false
    configuration:
      - field: "[auth-field-1]"
        type: "string|secret"
        description: "[Field description]"
        required: true|false
        
  endpoints:
    base_url: "[base-url-if-api]"
    
    operations:
      - operation: "[operation-name-1]"
        method: "GET|POST|PUT|DELETE"
        endpoint: "[endpoint-path]"
        description: "[Operation description]"
        parameters:
          - name: "[param-name-1]"
            type: "string|number|boolean"
            required: true|false
            description: "[Parameter description]"
            
  data_mapping:
    # How external service data maps to PatternForge concepts
    patterns:
      external_field: "[external-field-name]"
      internal_field: "[internal-field-name]"
      transformation: "[transformation-logic]"
      
  webhooks:
    - event: "[webhook-event-1]"
      endpoint: "/webhook/[service-name]/[event]"
      handler: "webhooks/[event]-handler.js"
      security: "signature|token|none"
      
  rate_limiting:
    requests_per_minute: 60
    burst_limit: 10
    retry_strategy: "exponential-backoff"
    
  error_handling:
    - error_code: "[error-code-1]"
      description: "[Error description]"
      retry: true|false
      user_message: "[User-friendly error message]"
      
  data_synchronization:
    sync_frequency: "real-time|hourly|daily|on-demand"
    conflict_resolution: "local-wins|remote-wins|manual"
    data_validation: "strict|relaxed"
```

### 4. Workflow Extension Template

#### [workflow-name].yaml
```yaml
workflow:
  name: "[workflow-name]"
  description: "[Workflow description and purpose]"
  version: "1.0"
  
  trigger:
    type: "command|pattern-application|schedule|event|manual"
    
    # For command trigger
    command: "/wizard [trigger-command]"
    
    # For pattern-application trigger
    pattern_events: ["pattern-applied", "pattern-validated", "pattern-failed"]
    pattern_filters:
      categories: ["[category-1]", "[category-2]"]
      specific_patterns: ["[pattern-1]", "[pattern-2]"]
      
    # For schedule trigger
    schedule: "0 9 * * MON" # cron format
    
    # For event trigger
    events: ["[event-1]", "[event-2]"]
    
  steps:
    - step: "[step-name-1]"
      type: "command|validation|notification|integration|custom"
      description: "[Step description]"
      
      # For command step
      command: "/wizard [command-to-execute]"
      arguments: ["[arg-1]", "[arg-2]"]
      
      # For validation step
      validation:
        type: "pattern-adherence|quality-check|custom"
        rules: ["[rule-1]", "[rule-2]"]
        
      # For notification step
      notification:
        type: "email|slack|webhook|console"
        message: "[notification-message]"
        recipients: ["[recipient-1]", "[recipient-2]"]
        
      # For integration step
      integration:
        service: "[service-name]"
        operation: "[operation-name]"
        parameters:
          param1: "[value-1]"
          param2: "[value-2]"
          
      # For custom step
      custom:
        handler: "handlers/[step-handler].js"
        configuration:
          setting1: "[value-1]"
          setting2: "[value-2]"
          
      # Step execution control
      condition: "[condition-for-step-execution]"
      on_failure: "continue|stop|retry"
      timeout: 60 # seconds
      
  flow_control:
    parallel_execution: true|false
    max_concurrent_steps: 3
    failure_handling: "stop-on-first-failure|continue-all|stop-on-critical"
    
  outputs:
    - output: "[output-name-1]"
      type: "file|variable|notification|report"
      location: "[output-location]"
      format: "json|yaml|markdown|text"
      
  variables:
    - variable: "[variable-name-1]"
      type: "string|number|boolean|array|object"
      default: "[default-value]"
      description: "[Variable description]"
      
  configuration:
    max_execution_time: 600 # seconds
    retry_failed_steps: true|false
    log_level: "debug|info|warn|error"
    
  monitoring:
    metrics:
      - metric: "execution_time"
        type: "duration"
        
      - metric: "success_rate"
        type: "percentage"
        
    alerts:
      - condition: "execution_time > 300"
        action: "notify_admin"
        message: "Workflow taking longer than expected"
```

---

## Development Workflow

### 1. Extension Creation
```bash
# Create new extension structure
/wizard create-extension [extension-name] [extension-type]

# Example: Create integration extension
/wizard create-extension jira-integration integration
```

### 2. Extension Development Process
```yaml
development_steps:
  1_planning:
    - define_extension_purpose
    - identify_integration_points
    - design_command_interface
    - plan_validation_strategy
    
  2_implementation:
    - implement_core_functionality
    - create_command_handlers
    - develop_validation_logic
    - implement_error_handling
    
  3_integration:
    - integrate_with_pattern_system
    - test_with_existing_commands
    - validate_help_system_integration
    - test_extension_loading
    
  4_validation:
    - unit_test_extension_logic
    - integration_test_with_wizard
    - performance_test_if_applicable
    - security_review_if_network_access
    
  5_documentation:
    - create_usage_documentation
    - write_integration_examples
    - document_configuration_options
    - create_troubleshooting_guide
```

### 3. Extension Testing
```bash
# Test extension locally
/wizard test-extension [extension-path]

# Test specific command
/wizard test-command [extension-name] [command-name]

# Validate extension definition
/wizard validate-extension [extension-path]

# Load extension for testing
/wizard load-extension [extension-path] --dev-mode
```

### 4. Extension Installation
```bash
# Install extension locally
/wizard install-extension [extension-path]

# Install from repository
/wizard install-extension [github-url]

# List installed extensions
/wizard list-extensions

# Update extension
/wizard update-extension [extension-name]

# Uninstall extension
/wizard uninstall-extension [extension-name]
```

---

## Publishing Guidelines

### Extension Quality Standards
1. **Functionality**: Extension works as documented
2. **Integration**: Seamlessly integrates with PatternForge
3. **Error Handling**: Graceful error handling and user feedback
4. **Documentation**: Comprehensive documentation and examples
5. **Security**: Secure handling of credentials and data
6. **Performance**: Acceptable performance characteristics

### Submission Process
1. **Develop Extension**: Use provided templates
2. **Test Thoroughly**: Test all functionality and edge cases
3. **Document Completely**: Create comprehensive documentation
4. **Security Review**: Ensure secure implementation
5. **Submit for Review**: Submit to extension marketplace
6. **Address Feedback**: Respond to review feedback
7. **Publish**: Extension available for community use

### Community Guidelines
- Follow extension naming conventions
- Provide clear installation instructions
- Include comprehensive examples
- Maintain extension with updates
- Respond to user feedback and issues

---

This template system enables developers to create powerful extensions that seamlessly integrate with and extend the PatternForge wizard system.