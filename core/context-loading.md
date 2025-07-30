# Context Loading: How Subsystems Work

## Loading Hierarchy

### Universal Context (Always Loaded)
Every wizard loads:
- `core/master-rules.md` - Universal methodology and tracking system

### Domain Context (Domain-Specific) 
When executing `/wizard <domain> <action>`:
- `<domain>/README.md` - Domain purpose and available modules
- Any domain-specific configuration or shared context

### Module Context (Action-Specific)
When executing specific wizard:
- `<domain>/<action>/wizard.md` - The actual wizard implementation
- `<domain>/<action>/help.md` - Module-specific help and chain context

### State Context (Resume/Continue)
When resuming or continuing work:
- `.aiwizard/domain.module.state.md` - Current wizard state
- `.aiwizard/domain.module.additionalcontext.md` - Preserved Q&A context
- `.aiwizard/domain.module.log.md` - Recent actions for context

## Context Minimization Principles

### Load Only What's Needed
- Don't load all domain modules when only using one
- Don't load state files unless resuming/continuing
- Don't load help files unless help was requested

### Clear Context When Appropriate
- Between unrelated domains
- After complex wizards that generate extensive context
- When context becomes performance-limiting

## Command Processing Flow

1. **Parse Command**: Extract domain, action, parameters
2. **Load Universal**: Always load core/master-rules.md
3. **Check State**: Look for existing .aiwizard files for this domain.module
4. **Load Domain Context**: Load domain README and shared context
5. **Load Module Context**: Load specific wizard and help files
6. **Execute Wizard**: Run with minimal, focused context

## Inter-Domain Communication

### Context Handoffs
When one wizard needs to call another:
- Document handoff in current wizard's log
- Update state before context switch
- Use /clear if contexts are incompatible
- Resume with appropriate context for target wizard

### Shared Data
When wizards need to share information:
- Use .aiwizard files as interface
- Document shared dependencies in domain READMEs  
- Avoid tight coupling between domains
- Prefer explicit handoffs over shared context