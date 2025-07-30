# Project Create-New Help

## Purpose
Creates comprehensive Product Requirements Documents with intelligent section recommendations based on your project context and needs.

## What This Wizard Does

### Core Functionality
- **Gathers essential project context** through proven Q&A methodology
- **Analyses your responses** to intelligently recommend additional PRD sections
- **Creates comprehensive PRDs** tailored to your project's complexity and goals
- **Preserves context** for future project development and analysis

### Smart Recommendations
The wizard automatically detects when additional PRD sections would be beneficial:
- **Technical Deep-dive**: For complex integrations, performance requirements, or architectural considerations
- **Security Requirements**: For user data, authentication, compliance, or public-facing applications
- **Growth Planning**: For projects with scaling expectations or team growth plans
- **Market Analysis**: For competitive positioning, business context, or commercial projects

## When to Use This Wizard

### Ideal For
- **New project initiation** where you need comprehensive requirements documentation
- **POC projects** that might evolve into larger applications
- **Startup projects** requiring detailed planning and stakeholder alignment
- **Any project** where clear requirements will guide development decisions

### Also Supports
- **Quick POCs** with minimal complexity (automatically skips unnecessary sections)
- **Personal projects** with appropriate scope and detail levels
- **Enterprise projects** with full compliance and scalability planning

## Usage

```
/wizard project create-new
```

The wizard will guide you through:
1. **Core questions** (essential for any PRD)
2. **Smart recommendations** (which additional sections would benefit your project)
3. **Enhanced Q&A** (detailed questions for recommended sections)
4. **PRD generation** (comprehensive document tailored to your needs)

## Integration with Other Wizards

### Downstream Usage
Your enhanced PRD provides better context for:
- **Task generation** (`/wizard project generate-tasks`)
- **Architecture planning** (`/wizard development architecture-design`)
- **Security planning** (security track wizards)
- **Project analysis** (`/wizard project analyse-existing`)

### Context Preservation
- **Q&A sessions** can be saved to `.aiwizard/` for future reference
- **Research outputs** preserved for project documentation
- **PRD updates** possible as project requirements evolve

## Key Features

### Intelligent Section Detection
Automatically analyses your responses for triggers like:
- API integrations → Technical deep-dive recommended
- User accounts → Security requirements recommended  
- Multiple users → Growth planning recommended
- Competitive mentions → Market analysis recommended

### Transparent Decision Making
Shows you exactly why sections are recommended or skipped:
```
✅ INCLUDING Security Requirements Section
   → You mentioned user accounts and personal data storage

⚠️ SKIPPING Growth Planning Section  
   → You described this as a "personal POC for learning"
```

### Conversational Overrides
Simple, natural way to adjust recommendations:
- "Don't skip growth planning"
- "Tell me about market analysis"  
- "Actually I do need security because..."

## Output Quality

### Always Maintains
- **Junior developer focus**: Clear, actionable requirements
- **Comprehensive coverage**: All essential PRD elements
- **Practical structure**: Ready for implementation planning
- **Context preservation**: Rich information for downstream processes

### Adapts Complexity
- **POC projects**: Focused, minimal overhead
- **Enterprise projects**: Comprehensive planning and compliance
- **Startup projects**: Growth and business context included
- **Personal projects**: Appropriate scope and detail level

## Creation Methodology

This wizard was created by combining:
- **Proven PRD methodology** (30+ years professional experience)
- **Modern project initiation research** (2025 best practices)
- **AI context optimization** (how to provide best information for effective AI assistance)
- **Conversational interface design** (natural, non-overwhelming user experience)

The key innovation is intelligent section recommendations with transparent decision-making, providing enterprise-level depth when beneficial while maintaining simplicity for straightforward projects.

## Common Use Cases

### "Quick POC to Test an Idea"
- Core questions only
- Technical considerations if integration needed
- Skips growth, market, complex security

### "Startup MVP Planning"  
- Full technical and security planning
- Growth considerations for scaling
- Market positioning for competitive advantage
- Business context for stakeholder alignment

### "Personal Learning Project"
- Core requirements with some technical depth
- Basic security if user accounts involved
- Skips business/market sections
- Growth planning only if thinking about sharing

### "Enterprise Feature Addition"
- Comprehensive technical integration requirements
- Full security and compliance considerations
- Stakeholder alignment and business context
- Detailed acceptance criteria and success metrics