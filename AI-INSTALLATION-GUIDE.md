# AI Installation Guide for Contextwarts

## Purpose
This guide enables any AI assistant to help users install and configure Contextwarts. The system is designed to be AI-installable and includes all necessary context for AI-guided setup.

---

## AI Installation Prompt

When a user asks for help installing Contextwarts, use this comprehensive approach:

### Step 1: System Assessment
```
I'll help you install Contextwarts! Let me first check your system setup:

1. **Operating System**: What OS are you using? (Windows/macOS/Linux)
2. **Git Availability**: Do you have git installed? (Check with: git --version)
3. **Claude Code**: Do you have Claude Code installed and configured?
4. **Directory Preference**: Where would you like to install? (Default: ~/.contextwarts/)
```

### Step 2: Repository Cloning
```bash
# Clone Contextwarts to the user's home directory
git clone https://github.com/rTiGd2/contextwarts.git ~/.contextwarts

# Verify the clone was successful
ls ~/.contextwarts/
```

**Expected files after cloning:**
- `README.md` - Main documentation
- `core/` - Pattern engine and core systems
- `patterns/` - Pattern library (63+ patterns)
- `templates/` - Developer templates
- `wizard/` - Wizard system files

### Step 3: Claude Code Integration
Help the user add the `/wizard` command to their Claude Code settings:

**Settings File Locations:**
- **Windows**: `%APPDATA%\Roaming\claude-code\settings.json`
- **macOS**: `~/Library/Application Support/claude-code/settings.json`  
- **Linux**: `~/.config/claude-code/settings.json`

**Configuration to Add:**
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

### Step 4: Installation Validation
```bash
# Check core system files exist
ls ~/.contextwarts/core/pattern-engine.md
ls ~/.contextwarts/core/wizard-help-system.md
ls ~/.contextwarts/patterns/
ls ~/.contextwarts/templates/

# Count patterns
find ~/.contextwarts/patterns -name "*.yaml" | wc -l
# Should show 60+ pattern files
```

### Step 5: First Usage Guidance
```
Great! Contextwarts is now installed. Here's how to get started:

🧙‍♂️ **Basic Commands (Always start with /clear for optimal performance):**
- `/clear && /wizard help` - Show all available commands and capabilities
- `/clear && /wizard create startup web-app` - Create new project with patterns
- `/clear && /wizard enhance authentication` - Add patterns to existing project
- `/clear && /wizard analyze` - Analyze current project for pattern opportunities

🎯 **First Project:**
Try creating a sample project to test the system:
1. Navigate to a development directory
2. Use: `/clear && /wizard create startup web-app`
3. Follow the guided pattern selection process

💡 **Performance Tip:** Always use `/clear` before wizard commands for 3-5x faster processing and more accurate recommendations.

📚 **Learn More:**
- Read ~/.contextwarts/README.md for comprehensive documentation
- Explore ~/.contextwarts/patterns/ to see all available patterns
- Check ~/.contextwarts/templates/ for creating custom patterns
```

---

## AI Troubleshooting Guide

### Common Installation Issues

#### Issue: Git not found
```
Git is required for installation. Please install git first:

**Windows**: Download from https://git-scm.com/download/win
**macOS**: Install via Homebrew: `brew install git` or Xcode Command Line Tools
**Linux**: Use package manager: `sudo apt install git` (Ubuntu/Debian) or `sudo yum install git` (RHEL/CentOS)

After installing git, try the installation again.
```

#### Issue: Claude Code settings file not found
```
Claude Code settings file not found. This usually means:

1. **Claude Code not installed**: Please install Claude Code first
2. **Different installation location**: Claude Code might be in a custom location
3. **First time setup**: Create the directory and settings file manually

Would you like me to help you locate your Claude Code installation or create the settings file manually?
```

#### Issue: Permission denied errors
```
Permission issues can occur when installing to system directories. Let's fix this:

**Option 1**: Install to user directory (recommended)
`git clone https://github.com/rTiGd2/contextwarts.git ~/contextwarts`

**Option 2**: Use sudo for system installation (not recommended)
`sudo git clone https://github.com/rTiGd2/contextwarts.git /usr/local/share/contextwarts`

The user directory installation is preferred for security and simplicity.
```

#### Issue: Repository clone fails
```
If the git clone fails, try these alternatives:

1. **Check internet connection**: Ensure you can access GitHub
2. **Use HTTPS instead of SSH**: The command above uses HTTPS which should work
3. **Download ZIP**: Download from https://github.com/rTiGd2/contextwarts/archive/main.zip
4. **Firewall/Proxy**: Check if corporate firewall is blocking GitHub access

Let me know which approach works for your environment.
```

---

## Post-Installation AI Guidance

### System Overview for AI Assistants
When helping users with Contextwarts after installation, remember:

**Core Concept**: Contextwarts uses patterns (not tracks) that can be applied in four modes:
- **Creation**: New project setup
- **Enhancement**: Adding capabilities  
- **Gap**: Filling missing implementations
- **Upgrade**: Improving existing patterns

**Key Directories**:
- `~/.contextwarts/core/` - System documentation and engines
- `~/.contextwarts/patterns/` - All pattern definitions
- `~/.contextwarts/templates/` - Templates for creating custom patterns

**AI Context Loading**:
Always start by reading `~/.contextwarts/core/pattern-engine.md` to understand the system before helping users.

### Helping Users Create Their First Pattern
```
Ready to create a custom pattern? Here's how:

1. **Choose Pattern Type**: 
   - Technology (frameworks, languages)
   - Architecture (system design approaches)
   - Security (authentication, compliance)
   - Infrastructure (deployment, monitoring)
   - Methodology (development processes)

2. **Use Template**: Copy from ~/.contextwarts/templates/pattern-development-template.md

3. **Follow Structure**: 
   - pattern.md (main guide)
   - dependencies.yaml (relationships)
   - detection.triggers (auto-detection)
   - application/ (mode-specific guidance)

4. **Test and Validate**: Use the pattern locally before sharing

Would you like to start with a specific pattern idea?
```

---

## AI Success Validation

After installation, validate success by checking:

1. **Files Exist**: Core files are present and readable
2. **Claude Code Integration**: `/wizard` command is configured
3. **Pattern Count**: 60+ patterns are available
4. **Basic Functionality**: User can run `/wizard help` successfully
5. **Context Loading**: System can load and understand patterns

---

This guide ensures any AI assistant can successfully help users install and configure Contextwarts, maintaining the system's AI-first design philosophy.