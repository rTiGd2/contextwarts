# Contextwarts 🧙‍♂️

*The context wizard for continuous project evolution*

**Created by**: Tig Campbell-Moore ([@rTiGd2](https://github.com/rTiGd2))

---

## Overview

Contextwarts is a revolutionary pattern-based project development system that transforms traditional one-time project wizards into continuous evolution enablement platforms. Instead of just setting up projects once, Contextwarts enables projects to evolve continuously through intelligent, composable patterns that can be applied at any stage of development.

### Key Innovation: From Tracks to Patterns

Traditional project wizards use "tracks" - linear, one-time setup processes. Contextwarts uses **patterns** that can be applied in four intelligent modes:

- **🆕 Creation Mode**: Bootstrap new projects with foundational patterns
- **⚡ Enhancement Mode**: Add new capabilities to existing projects
- **🔍 Gap Mode**: Fill missing or incomplete implementations  
- **🚀 Upgrade Mode**: Enhance existing patterns with advanced features

### Revolutionary Features

- **🎯 63+ Intelligent Patterns** across 5 categories (Technology, Architecture, Security, Infrastructure, Methodology)
- **🤖 AI-Ready Projects** with complete offline development context generation
- **🔄 Development Methodology Integration** (TDD, BDD, DDD, ATDD, EDD)
- **✅ Pattern Adherence Validation** with automated quality checking
- **👥 Self-Sufficient Framework** enabling development without wizard dependency
- **📚 Comprehensive Help System** with `/wizard help` command integration

---

## Quick Start

### Installation

#### AI-Assisted Installation (Recommended)
Ask any AI assistant to help you install Contextwarts:

```
Please help me install Contextwarts from https://github.com/rTiGd2/contextwarts

1. Clone the repository to ~/.contextwarts/ 
2. Set up the Claude Code /wizard command integration
3. Validate the installation by checking core files exist
4. Guide me through first usage

The system is designed to be installed by AI assistants and includes comprehensive documentation for setup guidance.
```

#### Manual Installation
```bash
# Clone the repository
git clone https://github.com/rTiGd2/contextwarts.git ~/.contextwarts
```

#### Claude Code Integration
Add to your Claude Code settings.json:
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

### First Use

```bash
# IMPORTANT: Clear context for optimal performance and accuracy
/clear

# Get help and see all capabilities
/wizard help

# Create a new project with patterns
/wizard create startup web-app

# Enhance existing project
/wizard enhance authentication

# Analyze project for pattern opportunities
/wizard analyze

# Load existing project context
/wizard load-context
```

---

## System Architecture

### Pattern Categories

#### 🏗️ **Technology Patterns** (23 patterns)
Modern technology stacks and implementations
- `modern-web-stack` - React/TypeScript/Node.js foundation
- `progressive-web-app` - PWA with service workers and offline capability
- `container-first-deployment` - Docker and Kubernetes with GitOps

#### 🏛️ **Architecture Patterns** (8 patterns)  
Architectural approaches and system design
- `microservices-architecture` - Service boundaries and communication
- `monolith-first` - Start simple, evolve to complexity
- `serverless-native` - Function-based architecture

#### 🔒 **Security Patterns** (12 patterns)
Security implementations and compliance
- `advanced-authentication` - WebAuthn, MFA, SSO integration
- `zero-trust-security` - Comprehensive security validation
- `pci-dss-compliance` - Payment card industry compliance

#### 🚀 **Infrastructure Patterns** (15 patterns)
Deployment and operational infrastructure  
- `reverse-proxy-load-balancer` - Traffic management and distribution
- `enterprise-monitoring` - OpenTelemetry observability stack
- `multi-database-architecture` - Polyglot persistence patterns

#### 🔄 **Methodology Patterns** (5 patterns)
Development methodologies and team processes
- `test-driven-development` - TDD with Red-Green-Refactor
- `behavior-driven-development` - Given-When-Then scenarios
- `domain-driven-design` - Strategic and tactical design approaches

### Core Components

- **Pattern Engine** (`core/pattern-engine.md`) - Intelligent pattern application system
- **Pattern Dependencies** (`core/pattern-dependencies.md`) - Dependency resolution and conflict management  
- **Pattern Detection** (`core/pattern-detection.md`) - Automatic pattern gap analysis
- **Offline Context Generation** (`core/offline-context-generation.md`) - AI-ready development contexts
- **Wizard Help System** (`core/wizard-help-system.md`) - Comprehensive command reference

---

## Usage Examples

### Creating a New Startup MVP
```bash
/clear
/wizard create startup-mvp
# Recommends: modern-web-stack + monolith-first + basic-security + test-driven-development
```

### Adding Authentication to Existing App
```bash
/clear
/wizard enhance authentication
# Analyzes current setup and recommends appropriate authentication patterns
```

### Converting to Microservices
```bash
/clear
/wizard upgrade monolith-first to microservices-architecture  
# Provides migration pathway and pattern upgrade guidance
```

### Development Methodology Selection
```bash
/clear
/wizard select-methodology
# Interactive methodology selection based on team size, complexity, and requirements
```

---

## AI Integration

Contextwarts generates complete AI development contexts that enable any AI assistant to understand and work with your project:

### Generated AI Context Files
- **`.contextwarts/standalone-context/project-resume-context.md`** - Complete project understanding
- **`.contextwarts/standalone-context/feature-addition-guide.md`** - Step-by-step development workflow
- **`.contextwarts/standalone-context/methodology-context.md`** - Development methodology guidance
- **`.contextwarts/ai-prompts/`** - Pre-configured prompts for common development tasks

### AI Bootstrap Prompt
Every Contextwarts project includes a README section with an AI bootstrap prompt that instantly loads complete project context into any AI assistant.

---

## Contributing

### For Users
- 🐛 [Report Issues](https://github.com/rTiGd2/contextwarts/issues)
- 💡 [Request Features](https://github.com/rTiGd2/contextwarts/issues/new?template=feature-request.md)
- 📖 [Improve Documentation](https://github.com/rTiGd2/contextwarts/tree/main/docs)

### For Developers
- 🎨 [Create Custom Patterns](https://github.com/rTiGd2/contextwarts/blob/main/templates/pattern-development-template.md)
- 🔧 [Build Wizard Extensions](https://github.com/rTiGd2/contextwarts/blob/main/templates/wizard-extension-template.md)
- 🔄 [Develop Methodology Patterns](https://github.com/rTiGd2/contextwarts/blob/main/templates/methodology-template.md)

---

## Documentation

- 📚 **[Complete Guide](docs/)** - Comprehensive system documentation
- 🎯 **[Pattern Library](patterns/)** - All available patterns with examples
- 🛠️ **[Developer Templates](templates/)** - Create custom patterns and extensions
- 🆘 **[Troubleshooting](docs/troubleshooting.md)** - Common issues and solutions
- 📝 **[Examples](examples/)** - Real-world usage examples

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Acknowledgments

Contextwarts represents a paradigm shift from traditional project setup to continuous project evolution. The pattern-based approach enables projects to grow and adapt throughout their entire lifecycle while maintaining quality, consistency, and AI-assisted development capabilities.

**The magic happens when patterns evolve your project** ✨

---

*Created by [Tig Campbell-Moore](https://github.com/rTiGd2) - Transforming how we build and evolve software projects*

**Created with AI, for AI** - Authored with the help of Claude Code, for use with Claude Code ✨