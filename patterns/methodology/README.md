# Development Methodology Patterns

## Purpose
Development Methodology Patterns define structured approaches to how teams build software. These patterns affect everything from testing strategies to code organization, tooling choices, and team collaboration models.

## Why Methodology Patterns Matter

Your development methodology choice impacts:

- **Testing Strategy**: TDD drives different testing than BDD or DDD
- **Code Organization**: DDD emphasizes domain models, TDD emphasizes testable units
- **Team Collaboration**: BDD requires business involvement, TDD can be developer-focused
- **Tooling Requirements**: Each methodology has specific tooling ecosystem needs
- **Quality Automation**: Different methodologies require different automation approaches

---

## Available Methodology Patterns

### Test-Driven Development (TDD)
**Focus**: Tests drive design and implementation
**Best For**: Well-understood domains, algorithmic code, refactoring legacy systems
**Key Practice**: Red-Green-Refactor cycle

### Behavior-Driven Development (BDD)  
**Focus**: Business behavior drives development
**Best For**: Business-critical applications, complex requirements, stakeholder collaboration
**Key Practice**: Given-When-Then scenarios

### Domain-Driven Design (DDD)
**Focus**: Deep domain understanding drives architecture
**Best For**: Complex business domains, large systems, enterprise applications
**Key Practice**: Ubiquitous language and bounded contexts

### Acceptance Test-Driven Development (ATDD)
**Focus**: Acceptance criteria drive development
**Best For**: Customer-facing features, regulatory compliance, clear requirements
**Key Practice**: Whole-team acceptance test definition

---

## Quick Methodology Selector

**Answer these questions for a recommendation:**

1. **Domain Complexity**: Simple/Well-understood vs Complex/Evolving
2. **Business Involvement**: High stakeholder collaboration vs Developer-driven
3. **Requirements Clarity**: Clear specifications vs Exploratory development
4. **Team Experience**: Methodology expertise vs Learning new approaches
5. **Project Risk**: High-risk business logic vs Standard development

---

## Pattern Relationships

Development Methodology Patterns integrate with:

- **Technology Patterns**: Methodology affects tool and framework choices
- **Architecture Patterns**: Some methodologies work better with certain architectures
- **Quality Automation Patterns**: Each methodology requires different automation strategies
- **Project Patterns**: Startup vs Enterprise projects may prefer different methodologies

---

## Implementation Modes

### Creation Mode
Choose methodology for new project based on context assessment

### Enhancement Mode  
Introduce methodology to existing team or project

### Gap Mode
Add structured approach to ad-hoc development process

### Upgrade Mode
Enhance existing methodology with advanced practices