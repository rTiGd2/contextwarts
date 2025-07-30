# Core Context: Universal Wizard Rules

This context is loaded by ALL wizards in the system.

## Methodology

### Q&A Sessions
When you need to ask multiple questions, ask one at a time. Either party can discuss, ask for clarification, or request more information. Continue until the question is answered or conversation suggests a new direction/action.

### Don't Rush
Always step back and analyze what is really going on first. Don't jump immediately into implementation.

### Research-First Approach
Don't assume training data is current. Research new tools, models, patterns, system commands, best practices, etc. before proceeding.

## Command Structure

### Help Hierarchy
- `/wizard` or `/wizard help` → Shows all domains with brief descriptions
- `/wizard help <domain>` → Domain purpose and available modules/commands  
- `/wizard <domain> help <module>` → Specific module help, usage, chain context

### Chain Context Awareness
Modules should indicate if they're typically used alone or as part of a command chain. If part of a chain, suggest where the chain typically starts (especially important if this is the 3rd step in a sequence).

## Wizard Tracking System

### .aiwizard Directory
All projects require a `.aiwizard/` directory for wizard state management.

### Standardized Files (Required)
- `domain.module.todo.md` - Current task list and progress tracking
- `domain.module.log.md` - Chronological record of actions taken  
- `domain.module.additionalcontext.md` - Q&A responses and extracted context
- `domain.module.state.md` - Current wizard state for resume functionality

### Additional Files
Domains can define additional tracking files as needed for module processing using `domain.module.<type>.md` naming convention. Not for project files the module creates, only for wizard internal tracking.

### State Detection
Wizards should check for existing files and intelligently respond:
- **Partial files exist** → Prompt for resume
- **Complete files exist** → Depends on wizard type:
  - Update-capable wizards: Ask if user wants to update/refresh output
  - One-time wizards: Report completed, ask if user wants to re-run

Examples provided in wizard creation documentation, not rigid enforcement.

## Context Management

### Minimal Loading Principles
Load only the context required for the specific wizard task. Avoid context bloat.

### Session Boundaries
Use `/clear` commands to reset context when switching between unrelated domains or when context becomes unwieldy.