# Development Methodology Pattern Selector

## Purpose
Help teams choose the optimal development methodology pattern based on their specific context, requirements, and constraints. This intelligent selector considers project characteristics, team dynamics, and business needs to recommend the best methodology approach.

---

## Quick Methodology Assessment

### Answer These Questions for Intelligent Recommendations:

#### 1. Primary Development Focus
- **Business Logic Complexity**: Simple CRUD | Moderate Rules | Complex Processes | Expert Domain
- **Stakeholder Involvement**: Developer-driven | Some Business Input | High Collaboration | Continuous Partnership
- **Requirements Clarity**: Clear & Stable | Mostly Clear | Evolving | Highly Uncertain

#### 2. Team & Project Context  
- **Team Size**: Solo Developer | Small Team (2-5) | Medium Team (5-15) | Large/Multiple Teams
- **Project Duration**: Short-term | Medium-term | Long-term | Strategic/Indefinite
- **Quality Requirements**: Standard | High | Critical | Life-Safety/Regulated

#### 3. Technical Context
- **System Complexity**: Simple Application | Moderate Complexity | Complex System | Enterprise/Distributed
- **Integration Needs**: Standalone | Few Integrations | Many Integrations | Complex Ecosystem
- **Performance Requirements**: Standard | High Performance | Real-time | Extreme Performance

---

## Methodology Pattern Recommendations

### For Simple to Moderate Complexity Projects

#### **Test-Driven Development (TDD)**
**Best When:**
- Well-understood business domain
- Quality and maintainability are priorities  
- Team has development focus
- Algorithmic or technical-heavy code
- Refactoring legacy systems

**Avoid When:**
- Very complex business domain requiring deep modeling
- High stakeholder involvement needed
- Requirements are highly uncertain
- Team resistance to test-first approach

---

### For Business-Critical & Stakeholder-Heavy Projects

#### **Behavior-Driven Development (BDD)**
**Best When:**
- Complex business requirements
- High stakeholder collaboration needed
- Customer-facing features
- Regulatory or compliance requirements
- Business-development communication gaps

**Avoid When:**
- Simple CRUD applications
- Technical/algorithmic code focus
- Limited stakeholder availability
- Team prefers technical focus over business focus

---

### For Complex Business Domains

#### **Domain-Driven Design (DDD)**
**Best When:**
- Complex business domain with intricate rules
- Long-term strategic system
- Large system requiring clear boundaries
- Multiple teams needing coordination
- Business logic is core system value

**Avoid When:**
- Simple business logic
- Short-term projects
- Small teams with simple domains
- CRUD-focused applications
- Limited domain expert access

---

### For Customer-Focused & Feature-Driven Projects

#### **Acceptance Test-Driven Development (ATDD)**
**Best When:**
- Customer acceptance is critical
- Feature-driven development approach
- Clear "definition of done" needed
- Quality assurance focus
- Whole-team collaboration possible

**Avoid When:**
- Limited stakeholder availability
- Technical-focused development
- Simple applications with obvious acceptance criteria
- Team prefers individual work over collaboration

---

### For Rule-Heavy & Documentation-Critical Projects

#### **Example-Driven Development (EDD)**
**Best When:**
- Complex business rules or calculations
- Documentation requirements (regulatory/compliance)
- API development with clear examples needed
- Stakeholder validation through concrete examples
- Business rule validation critical

**Avoid When:**
- Simple business logic
- Limited example availability
- Technical implementation focus
- Minimal documentation requirements

---

## Methodology Combination Strategies

### Hybrid Approaches (Often Most Effective)

#### **BDD + TDD Combination**
- **BDD for acceptance criteria** and business behavior
- **TDD for implementation** and technical design
- **Best for**: Complex business applications with quality focus

#### **DDD + TDD Combination**  
- **DDD for domain modeling** and strategic design
- **TDD for implementation** within domain boundaries
- **Best for**: Complex domains requiring both modeling and quality

#### **ATDD + TDD Combination**
- **ATDD for acceptance criteria** and customer focus
- **TDD for implementation** and technical quality
- **Best for**: Customer-critical applications with quality requirements

#### **EDD + BDD Combination**
- **EDD for business rule examples** and calculations
- **BDD for user behavior scenarios** and workflows
- **Best for**: Business rule-heavy applications with user interaction

---

## Context-Based Recommendations

### Startup/MVP Context
**Primary Recommendation**: **Test-Driven Development (TDD)**
- Rapid development with quality foundation
- Enables confident refactoring as product evolves
- Builds technical foundation for scaling

**Alternative**: **Acceptance Test-Driven Development (ATDD)**
- If customer validation is critical
- When product-market fit depends on precise feature delivery

### Enterprise/Regulated Context
**Primary Recommendation**: **Domain-Driven Design (DDD)**
- Handles complex business domain
- Provides clear boundaries for large teams
- Enables long-term system evolution

**Complement With**: **Behavior-Driven Development (BDD)**
- For stakeholder communication
- For regulatory documentation
- For compliance traceability

### API/Integration-Heavy Context
**Primary Recommendation**: **Example-Driven Development (EDD)**
- Concrete API request/response examples
- Living documentation for integrations
- Clear integration contract validation

**Complement With**: **Test-Driven Development (TDD)**
- For internal implementation quality
- For integration point reliability

### Customer-Facing Product Context
**Primary Recommendation**: **Behavior-Driven Development (BDD)**
- Focus on user behavior and experience
- Strong stakeholder involvement
- Business value validation

**Complement With**: **Acceptance Test-Driven Development (ATDD)**
- For customer acceptance validation
- For feature completion criteria

---

## Implementation Roadmap by Methodology

### Test-Driven Development (TDD) Roadmap
**Week 1-2**: Setup and Training
- Choose testing framework
- Team TDD training and practice
- Establish Red-Green-Refactor rhythm

**Week 3-4**: Application and Refinement  
- Apply TDD to new features
- Refactor existing code with tests
- Establish team TDD standards

### Behavior-Driven Development (BDD) Roadmap
**Week 1-2**: Foundation and Collaboration
- Setup BDD framework (Cucumber, SpecFlow)
- Establish three-amigos collaboration
- Define scenario writing standards

**Week 3-6**: Implementation and Automation
- Write scenarios for existing features
- Automate scenario execution
- Integrate with CI/CD pipeline

### Domain-Driven Design (DDD) Roadmap
**Week 1-4**: Strategic Design
- Event storming and domain discovery
- Identify bounded contexts
- Establish ubiquitous language

**Week 5-12**: Tactical Implementation
- Implement domain models
- Create aggregates and entities
- Establish context integration patterns

### Acceptance Test-Driven Development (ATDD) Roadmap
**Week 1-2**: Process and Collaboration
- Define acceptance criteria process
- Establish three-amigos collaboration
- Choose automation framework

**Week 3-5**: Automation and Integration
- Automate acceptance criteria
- Integrate with development workflow
- Establish definition of done

### Example-Driven Development (EDD) Roadmap
**Week 1-2**: Framework and Examples
- Choose example framework (Concordion, FitNesse)
- Gather existing examples
- Define example format standards

**Week 3-4**: Automation and Documentation
- Automate example execution
- Generate living documentation
- Integrate with development process

---

## Success Factors by Methodology

### Test-Driven Development (TDD)
**Critical Success Factors:**
- Team commitment to test-first discipline
- Good refactoring skills and tools
- Appropriate testing framework choice
- Management support for "slower" initial development

### Behavior-Driven Development (BDD)
**Critical Success Factors:**
- Active business stakeholder participation
- Good facilitation of three-amigos sessions
- Appropriate BDD tooling selection
- Cultural commitment to collaboration

### Domain-Driven Design (DDD)
**Critical Success Factors:**
- Access to domain experts
- Senior developer capability
- Long-term commitment to approach
- Investment in strategic design activities

### Acceptance Test-Driven Development (ATDD)
**Critical Success Factors:**
- Clear definition of acceptance criteria
- Whole-team collaboration commitment
- Appropriate test automation framework
- Customer or proxy customer availability

### Example-Driven Development (EDD)
**Critical Success Factors:**
- Rich set of concrete business examples
- Stakeholder availability for example validation
- Appropriate tooling for executable examples
- Documentation culture and requirements

---

## Methodology Transition Strategies

### From No Methodology to Structured Approach
**Recommended Path**: Start with **TDD**
- Lowest barrier to entry
- Immediate quality benefits
- Foundation for other methodologies

### From Waterfall to Agile Methodology
**Recommended Path**: **ATDD** → **BDD**
- Bridges traditional acceptance testing
- Maintains stakeholder involvement
- Introduces collaboration gradually

### From Simple to Complex Domain
**Recommended Path**: **TDD** → **DDD** + **TDD**
- Build quality foundation first
- Add domain modeling as complexity grows
- Maintain implementation quality

### From Technical to Business Focus  
**Recommended Path**: **TDD** → **BDD** + **TDD**
- Maintain technical quality
- Add business collaboration layer
- Bridge technical and business perspectives

---

## Anti-Patterns and Red Flags

### Methodology Selection Anti-Patterns
❌ **Choosing methodology based on hype rather than context**
❌ **Forcing complex methodology on simple problems**
❌ **Selecting methodology without team buy-in**
❌ **Ignoring organizational culture in methodology choice**
❌ **Attempting to implement multiple new methodologies simultaneously**

### Implementation Red Flags
🚨 **TDD**: Writing tests after implementation (not test-first)
🚨 **BDD**: Scenarios written by developers without business input
🚨 **DDD**: Over-engineering simple domains with complex patterns
🚨 **ATDD**: Acceptance criteria defined without customer involvement
🚨 **EDD**: Examples that are abstract rather than concrete

---

This selector helps teams make informed decisions about development methodology patterns based on their specific context and requirements, ensuring optimal alignment between methodology choice and project success factors.