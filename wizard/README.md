# Wizard Domain: Meta-System Management

## Purpose

The wizard domain manages the wizard system itself - creating new domains, extending existing ones, and propagating improvements throughout the system.

## Available Actions

### Domain Management
- `create domain <name>` - Generate new domain structure with templates
- `extend domain <name>` - Add new actions to existing domain
- `validate domain <name>` - Check domain structure and completeness

### System Operations  
- `help bootstrap` - How to recreate the entire system from scratch
- `help create` - How to create new wizards and domains
- `help extend` - How to add capabilities to existing wizards
- `propagate improvements` - Update existing wizards with new patterns

### Documentation
- `help` - Overview of wizard system capabilities
- `help <topic>` - Detailed help for specific wizard functionality

## Command Examples

```bash
# Create a new domain for AI/ML workflows
/wizard wizard create domain ai-ml

# Add a new action to the development domain  
/wizard wizard extend domain development add performance-analysis

# Validate that a domain has all required files
/wizard wizard validate domain project

# Get help on creating wizards
/wizard wizard help create

# Propagate improvements to all domains
/wizard wizard propagate improvements
```

## Self-Documentation

This wizard domain was created as part of the initial system bootstrap. It demonstrates:

### Recursive Design
- The wizard domain documents how to create wizard domains
- It can modify and improve itself
- Improvements automatically propagate to new wizards

### Bootstrap Solution
- Documents its own creation methodology
- Provides templates for creating similar functionality
- Solves the meta-problem of system self-documentation

### Enhancement Protocol
When improvements are discovered:
1. Document the enhancement in wizard domain
2. Identify affected domains that could benefit  
3. Update existing implementations systematically
4. Update creation templates for future wizards
5. Test propagation doesn't break existing functionality

## Meta-Architecture

The wizard domain operates at three levels:

### Level 1: Documentation (Help)
- Explains how wizards work
- Provides templates and examples
- Documents creation methodology

### Level 2: Generation (Create)  
- Actually generates domain structures
- Creates template files
- Updates system indices

### Level 3: Evolution (Improve)
- Enhances existing wizards
- Propagates improvements
- Maintains system consistency

This tri-level approach solves the bootstrap problem while enabling continuous evolution.