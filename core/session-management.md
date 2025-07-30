# Session Management: Context Boundaries and Clear Protocols

## When to Use /clear

### Between Unrelated Domains
When switching from one domain to a completely different domain with no workflow connection:
```
/wizard business prd-creation
# ... work completed
/clear
/wizard development code-review
```

### Context Becomes Unwieldy
When conversation context grows too large and starts affecting performance or relevance:
- Long debugging sessions with extensive error logs
- Multi-step wizards with extensive research phases  
- Complex Q&A sessions with branching discussions

### After Complex Wizards
Some wizards generate significant context that isn't needed for subsequent work:
- Large project analysis with extensive codebase research
- Market research with extensive external data
- Complex refactoring with detailed code analysis

## Context Handoff Protocols

### Documenting Session Boundaries
When using /clear, document what was accomplished and what comes next:
- Update relevant .aiwizard files before clearing
- Note completion status in domain.module.state.md
- Document any context that needs to carry forward

### Resuming After /clear
When resuming work after context clear:
- Check .aiwizard directory for previous state
- Load domain.module.state.md for current status
- Review domain.module.log.md for recent actions
- Load domain.module.additionalcontext.md if needed for continuation

## Domain-Specific Context Loading

Each domain loads minimal required context:
- Always: core/master-rules.md (this universal context)
- Domain-specific: Relevant domain documentation
- Module-specific: Individual wizard/module files
- State-specific: Relevant .aiwizard files for continuation