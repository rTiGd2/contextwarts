# Claude Code Integration Guide

## Purpose
Complete guide for integrating Contextwarts with Claude Code through the `/wizard` command, enabling seamless AI-assisted pattern-based development.

---

## Integration Overview

Contextwarts integrates with Claude Code through a custom `/wizard` command that:
- Loads the complete Contextwarts pattern system
- Provides context-aware pattern recommendations
- Guides users through pattern application processes
- Enables continuous project evolution

---

## Setup Instructions

### Step 1: Install Contextwarts
Ensure Contextwarts is installed at `~/.contextwarts/` (see README.md for installation)

### Step 2: Locate Claude Code Settings File

**Windows:**
```
%APPDATA%\Roaming\claude-code\settings.json
```

**macOS:**
```
~/Library/Application Support/claude-code/settings.json
```

**Linux:**
```
~/.config/claude-code/settings.json
```

### Step 3: Add Wizard Command Configuration

Add this configuration to your `settings.json`:

```json
{
  "commands": {
    "/wizard": {
      "description": "Launch Contextwarts pattern-based project wizard",
      "prompt": "Load the Contextwarts system from ~/.contextwarts/ and help with pattern-based project development. Start by reading ~/.contextwarts/core/pattern-engine.md to understand the pattern system, then assess whether this is project creation, enhancement, gap filling, or upgrade. Provide context-aware pattern recommendations and guide through implementation."
    }
  }
}
```

### Step 4: Complete Settings File Example

If you're creating the settings file from scratch:

```json
{
  "commands": {
    "/wizard": {
      "description": "Launch Contextwarts pattern-based project wizard",
      "prompt": "Load the Contextwarts system from ~/.contextwarts/ and help with pattern-based project development. Start by reading ~/.contextwarts/core/pattern-engine.md to understand the pattern system, then assess whether this is project creation, enhancement, gap filling, or upgrade. Provide context-aware pattern recommendations and guide through implementation."
    }
  },
  "other_settings": {
    "comment": "Add your other Claude Code settings here"
  }
}
```

### Step 5: Restart Claude Code
After saving the settings file, restart Claude Code for the changes to take effect.

---

## Usage

### Basic Wizard Commands

```bash
# Get comprehensive help
/wizard help

# Create new project with patterns
/wizard create [project-type]

# Enhance existing project
/wizard enhance [capability]

# Analyze project for patterns
/wizard analyze

# Load existing project context
/wizard load-context

# Validate pattern adherence
/wizard validate patterns
```

### Example Workflows

#### Creating a New Startup Project
```bash
/wizard create startup web-app
```
**Expected Flow:**
1. System loads pattern engine and methodology selector
2. AI asks context questions (team size, complexity, timeline)
3. Recommends patterns: `modern-web-stack` + `monolith-first` + `basic-security` + `test-driven-development`
4. Guides through pattern application and project setup
5. Generates AI development context in `.contextwarts/` directory

#### Adding Authentication to Existing Project
```bash
/wizard enhance authentication
```
**Expected Flow:**
1. System analyzes current project structure
2. Detects existing patterns and architecture
3. Recommends appropriate authentication patterns
4. Checks for conflicts and dependencies
5. Guides through implementation with existing system integration

#### Converting Monolith to Microservices
```bash
/wizard upgrade monolith-first to microservices-architecture
```
**Expected Flow:**
1. System loads both patterns and migration strategies
2. Analyzes current monolith implementation
3. Provides step-by-step migration pathway
4. Maintains pattern adherence throughout transition
5. Updates project context with new architecture patterns

---

## Advanced Integration

### Custom Pattern Development
```bash
/wizard create-pattern [pattern-name] [category]
```
Uses templates from `~/.contextwarts/templates/` to guide custom pattern creation.

### Methodology Selection
```bash
/wizard select-methodology
```
Interactive methodology selection based on project context and team characteristics.

### Pattern Validation
```bash
/wizard validate patterns
```
Comprehensive validation of current pattern implementation and adherence.

---

## AI Context Loading

When the `/wizard` command is invoked, the AI assistant automatically:

1. **Loads Core System**: Reads `~/.contextwarts/core/pattern-engine.md`
2. **Understands Pattern Library**: Accesses all patterns in `~/.contextwarts/patterns/`
3. **Loads Help System**: References `~/.contextwarts/core/wizard-help-system.md`
4. **Accesses Templates**: Uses `~/.contextwarts/templates/` for guidance
5. **Detects Project Context**: Analyzes current project if `.contextwarts/` exists

### Context Files Read by AI
- `core/pattern-engine.md` - Understanding of pattern system
- `core/pattern-dependencies.md` - Dependency resolution logic
- `core/pattern-detection.md` - Gap analysis and detection
- `core/offline-context-generation.md` - AI context creation
- `core/wizard-help-system.md` - Complete command reference
- `patterns/*/dependencies.yaml` - Individual pattern definitions
- `templates/` - Templates for pattern and extension development

---

## Troubleshooting

### Command Not Found
**Issue**: `/wizard` command not recognized
**Solution**: 
1. Verify settings.json syntax is correct (use JSON validator)
2. Restart Claude Code
3. Check settings file location is correct for your OS

### Pattern Loading Errors
**Issue**: AI reports it cannot find pattern files
**Solution**:
1. Verify Contextwarts is installed at `~/.contextwarts/`
2. Check file permissions allow reading
3. Ensure git clone completed successfully

### Context Loading Issues
**Issue**: AI doesn't seem to understand the pattern system
**Solution**:
1. Verify `~/.contextwarts/core/pattern-engine.md` exists and is readable
2. Try `/wizard help` to force context loading
3. Check for any file corruption during installation

### Settings File Location
**Issue**: Can't find Claude Code settings file
**Solution**:
1. Create the directory structure if it doesn't exist
2. Start with a minimal settings.json file
3. Claude Code may store settings in a different location for custom installations

---

## Integration Benefits

### For Users
- **Seamless Workflow**: Pattern application directly in development environment
- **Context Awareness**: AI understands your project's current state
- **Continuous Evolution**: Projects grow and adapt over time
- **Quality Maintenance**: Automated pattern adherence validation

### For AI Assistants
- **Complete Context**: Full understanding of pattern-based development
- **Structured Guidance**: Clear workflows for all pattern operations
- **Extensible System**: Easy to add new patterns and capabilities
- **Self-Documenting**: System explains itself and its capabilities

---

## Security Considerations

### File System Access
- Contextwarts only reads from `~/.contextwarts/` directory
- Generated project contexts in `.contextwarts/` are project-specific
- No system-wide modifications required

### Network Access
- Initial installation requires GitHub access for git clone
- No ongoing network access required for operation
- All pattern processing is local

### Permissions
- Operates with user-level permissions only
- No administrative access required
- Respects existing file system permissions

---

This integration enables the full power of Contextwarts through Claude Code, creating a seamless AI-assisted pattern-based development experience.