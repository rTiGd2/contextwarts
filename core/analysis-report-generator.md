# Analysis Report Generator

## Purpose

The Analysis Report Generator creates comprehensive, human-readable reports from the project analysis and gap analysis engines. It generates both executive summaries and detailed technical reports for different audiences.

## Report Types

1. **Executive Summary** - High-level overview for stakeholders
2. **Technical Analysis** - Detailed findings for developers
3. **Implementation Roadmap** - Step-by-step guidance
4. **Gap Analysis Report** - Missing patterns and recommendations

## Implementation

```javascript
// scripts/generate-analysis-report.js
const fs = require('fs');
const path = require('path');

class AnalysisReportGenerator {
    constructor(projectRoot) {
        this.projectRoot = projectRoot;
        this.analysisData = {};
    }
    
    async generateFullReport() {
        console.log('📋 Generating comprehensive analysis report...');
        
        // Load all analysis data
        await this.loadAnalysisData();
        
        // Generate different report sections
        const executiveSummary = this.generateExecutiveSummary();
        const technicalAnalysis = this.generateTechnicalAnalysis();
        const gapAnalysis = this.generateGapAnalysisReport();
        const implementationRoadmap = this.generateImplementationRoadmap();
        
        // Create comprehensive report
        const fullReport = this.compileFullReport({
            executiveSummary,
            technicalAnalysis,
            gapAnalysis,
            implementationRoadmap
        });
        
        // Save reports
        await this.saveReports(fullReport);
        
        return fullReport;
    }
    
    async loadAnalysisData() {
        const analysisDir = path.join(this.projectRoot, '.contextwarts/analysis');
        
        try {
            this.analysisData = {
                inventory: JSON.parse(fs.readFileSync(path.join(analysisDir, 'project-inventory.json'), 'utf8')),
                technologies: JSON.parse(fs.readFileSync(path.join(analysisDir, 'technology-report.json'), 'utf8')),
                patterns: JSON.parse(fs.readFileSync(path.join(analysisDir, 'pattern-report.json'), 'utf8')),
                gaps: JSON.parse(fs.readFileSync(path.join(analysisDir, 'gap-analysis.json'), 'utf8')),
                context: this.loadProjectContext()
            };
        } catch (error) {
            console.error('⚠️ Some analysis data missing. Running with available data.');
        }
    }
    
    loadProjectContext() {
        try {
            return JSON.parse(fs.readFileSync('.contextwarts/analysis/project-context.json', 'utf8'));
        } catch {
            return {};
        }
    }
    
    generateExecutiveSummary() {
        const { technologies, patterns, gaps, context } = this.analysisData;
        
        return {
            projectOverview: this.generateProjectOverview(),
            currentState: this.generateCurrentStateOverview(),
            keyFindings: this.generateKeyFindings(),
            recommendations: this.generateExecutiveRecommendations(),
            nextSteps: this.generateNextSteps()
        };
    }
    
    generateProjectOverview() {
        const { context, technologies, inventory } = this.analysisData;
        
        return {
            type: context.projectType || 'Unknown',
            purpose: context.businessPurpose || 'Not specified',
            scale: context.expectedScale || 'Not specified',
            team_size: context.teamSize || 'Not specified',
            stage: context.developmentStage || 'Not specified',
            file_count: inventory.file_counts?.total_files || 0,
            technology_count: technologies.total_technologies || 0
        };
    }
    
    generateCurrentStateOverview() {
        const { technologies, patterns } = this.analysisData;
        
        const technologySummary = this.categorizeTechnologies(technologies.technologies);
        const patternSummary = this.categorizePatterns(patterns.patterns);
        
        return {
            technology_stack: technologySummary,
            implemented_patterns: patternSummary,
            maturity_score: this.calculateMaturityScore(),
            security_posture: this.assessSecurityPosture(),
            scalability_readiness: this.assessScalabilityReadiness()
        };
    }
    
    generateKeyFindings() {
        const { gaps, patterns, technologies } = this.analysisData;
        
        const findings = [];
        
        // Technology findings
        const highConfidenceTech = technologies.technologies.filter(t => t.confidence >= 0.8);
        findings.push({
            category: 'Technology Stack',
            type: 'positive',
            message: `Strong technology foundation with ${highConfidenceTech.length} well-implemented technologies`,
            details: highConfidenceTech.slice(0, 5).map(t => t.name)
        });
        
        // Pattern findings
        const wellImplementedPatterns = patterns.patterns.filter(p => p.completeness >= 0.8);
        if (wellImplementedPatterns.length > 0) {
            findings.push({
                category: 'Architecture Patterns',
                type: 'positive',
                message: `${wellImplementedPatterns.length} patterns are well-implemented`,
                details: wellImplementedPatterns.map(p => p.name)
            });
        }
        
        // Gap findings
        const criticalGaps = gaps.gaps.missing.filter(g => g.priority > 0.8);
        if (criticalGaps.length > 0) {
            findings.push({
                category: 'Critical Gaps',
                type: 'concern',
                message: `${criticalGaps.length} critical patterns missing`,
                details: criticalGaps.slice(0, 3).map(g => g.pattern.name)
            });
        }
        
        // Security findings
        const securityPatterns = patterns.patterns.filter(p => p.name.includes('security') || p.name.includes('auth'));
        if (securityPatterns.length === 0) {
            findings.push({
                category: 'Security',
                type: 'warning',
                message: 'Limited security patterns detected',
                details: ['Consider implementing authentication and security measures']
            });
        }
        
        return findings;
    }
    
    generateExecutiveRecommendations() {
        const { gaps } = this.analysisData;
        
        return gaps.recommendations.slice(0, 5).map(rec => ({
            priority: this.mapPriorityToLabel(rec.priority),
            pattern: rec.pattern,
            business_impact: this.getBusinessImpact(rec.pattern),
            implementation_effort: rec.effort.complexity || 'medium',
            timeline: this.getTimeline(rec.effort)
        }));
    }
    
    generateTechnicalAnalysis() {
        return {
            technology_analysis: this.generateTechnologyAnalysis(),
            architecture_analysis: this.generateArchitectureAnalysis(),
            security_analysis: this.generateSecurityAnalysis(),
            infrastructure_analysis: this.generateInfrastructureAnalysis(),
            code_quality_analysis: this.generateCodeQualityAnalysis()
        };
    }
    
    generateTechnologyAnalysis() {
        const { technologies } = this.analysisData;
        
        const byCategory = this.categorizeTechnologies(technologies.technologies);
        
        return {
            summary: {
                total_technologies: technologies.total_technologies,
                high_confidence: technologies.high_confidence,
                categories: Object.keys(byCategory).length
            },
            by_category: byCategory,
            technology_stack_assessment: this.assessTechnologyStack(byCategory)
        };
    }
    
    generateArchitectureAnalysis() {
        const { patterns } = this.analysisData;
        const architecturePatterns = patterns.patterns.filter(p => 
            ['monolith-first', 'microservices-architecture', 'serverless-native'].includes(p.id)
        );
        
        return {
            current_architecture: architecturePatterns.length > 0 ? architecturePatterns[0].name : 'Not clearly defined',
            architecture_maturity: this.calculateArchitectureMaturity(architecturePatterns),
            scalability_assessment: this.assessScalabilityReadiness(),
            evolution_path: this.suggestArchitectureEvolution(architecturePatterns)
        };
    }
    
    generateSecurityAnalysis() {
        const { patterns, gaps } = this.analysisData;
        const securityPatterns = patterns.patterns.filter(p => p.category === 'security');
        const securityGaps = gaps.gaps.missing.filter(g => g.pattern.category === 'security');
        
        return {
            current_security_patterns: securityPatterns.map(p => ({
                name: p.name,
                completeness: p.completeness,
                components: p.components
            })),
            security_gaps: securityGaps.map(g => ({
                pattern: g.pattern.name,
                priority: g.priority,
                reasoning: g.reasoning
            })),
            security_score: this.calculateSecurityScore(securityPatterns, securityGaps),
            compliance_assessment: this.assessComplianceReadiness()
        };
    }
    
    generateGapAnalysisReport() {
        const { gaps } = this.analysisData;
        
        return {
            summary: gaps.summary,
            critical_gaps: this.formatGaps(gaps.gaps.missing.filter(g => g.priority > 0.8)),
            incomplete_implementations: this.formatIncompletePatterns(gaps.gaps.incomplete),
            upgrade_opportunities: this.formatUpgradeOpportunities(gaps.gaps.upgrades),
            pattern_conflicts: gaps.gaps.conflicts,
            prioritized_recommendations: gaps.recommendations
        };
    }
    
    generateImplementationRoadmap() {
        const { gaps } = this.analysisData;
        
        return {
            roadmap: gaps.implementation_roadmap,
            detailed_phases: this.generateDetailedPhases(gaps.implementation_roadmap),
            resource_requirements: this.calculateResourceRequirements(gaps.recommendations),
            risk_assessment: this.assessImplementationRisks(gaps.recommendations)
        };
    }
    
    compileFullReport(sections) {
        const reportTimestamp = new Date().toISOString();
        const { context } = this.analysisData;
        
        return {
            metadata: {
                generated_at: reportTimestamp,
                project_root: this.projectRoot,
                project_context: context,
                analysis_version: '1.0.0'
            },
            executive_summary: sections.executiveSummary,
            technical_analysis: sections.technicalAnalysis,
            gap_analysis: sections.gapAnalysis,
            implementation_roadmap: sections.implementationRoadmap,
            appendices: {
                raw_data: {
                    technologies: this.analysisData.technologies,
                    patterns: this.analysisData.patterns,
                    inventory: this.analysisData.inventory
                }
            }
        };
    }
    
    async saveReports(fullReport) {
        const reportDir = path.join(this.projectRoot, '.contextwarts/reports');
        fs.mkdirSync(reportDir, { recursive: true });
        
        // Save full JSON report
        fs.writeFileSync(
            path.join(reportDir, 'full-analysis-report.json'),
            JSON.stringify(fullReport, null, 2)
        );
        
        // Generate and save markdown reports
        await this.generateMarkdownReports(fullReport, reportDir);
        
        // Generate and save executive summary
        await this.generateExecutiveSummaryReport(fullReport, reportDir);
        
        console.log(`📄 Reports saved to ${reportDir}/`);
    }
    
    async generateMarkdownReports(fullReport, reportDir) {
        // Executive Summary Markdown
        const execSummaryMd = this.generateExecutiveSummaryMarkdown(fullReport);
        fs.writeFileSync(path.join(reportDir, 'executive-summary.md'), execSummaryMd);
        
        // Technical Analysis Markdown
        const techAnalysisMd = this.generateTechnicalAnalysisMarkdown(fullReport);
        fs.writeFileSync(path.join(reportDir, 'technical-analysis.md'), techAnalysisMd);
        
        // Gap Analysis Markdown
        const gapAnalysisMd = this.generateGapAnalysisMarkdown(fullReport);
        fs.writeFileSync(path.join(reportDir, 'gap-analysis.md'), gapAnalysisMd);
        
        // Implementation Roadmap Markdown
        const roadmapMd = this.generateRoadmapMarkdown(fullReport);
        fs.writeFileSync(path.join(reportDir, 'implementation-roadmap.md'), roadmapMd);
    }
    
    generateExecutiveSummaryMarkdown(report) {
        const { executive_summary: exec, metadata } = report;
        
        return `# Project Analysis - Executive Summary

*Generated: ${new Date(metadata.generated_at).toLocaleDateString()}*

## Project Overview

- **Type**: ${exec.projectOverview.type}
- **Purpose**: ${exec.projectOverview.purpose}
- **Scale**: ${exec.projectOverview.scale}
- **Team Size**: ${exec.projectOverview.team_size}
- **Development Stage**: ${exec.projectOverview.stage}

## Current State

### Technology Stack
${this.formatTechnologyStackForMarkdown(exec.currentState.technology_stack)}

### Maturity Assessment
- **Overall Maturity Score**: ${exec.currentState.maturity_score}/10
- **Security Posture**: ${exec.currentState.security_posture}
- **Scalability Readiness**: ${exec.currentState.scalability_readiness}

## Key Findings

${exec.keyFindings.map(finding => `
### ${finding.category} ${this.getEmojiForFindingType(finding.type)}

**${finding.message}**

${finding.details ? finding.details.map(d => `- ${d}`).join('\n') : ''}
`).join('\n')}

## Priority Recommendations

${exec.recommendations.map((rec, index) => `
### ${index + 1}. ${rec.pattern} ${this.getPriorityEmoji(rec.priority)}

- **Business Impact**: ${rec.business_impact}
- **Implementation Effort**: ${rec.implementation_effort}
- **Timeline**: ${rec.timeline}
`).join('\n')}

## Next Steps

${exec.nextSteps.map(step => `1. ${step}`).join('\n')}

---

*This analysis was generated by Contextwarts Pattern Analysis Engine*
`;
    }
    
    generateTechnicalAnalysisMarkdown(report) {
        const { technical_analysis: tech } = report;
        
        return `# Technical Analysis Report

## Technology Analysis

### Summary
- **Total Technologies**: ${tech.technology_analysis.summary.total_technologies}
- **High Confidence**: ${tech.technology_analysis.summary.high_confidence}
- **Categories**: ${tech.technology_analysis.summary.categories}

### Technology Stack by Category

${Object.entries(tech.technology_analysis.by_category).map(([category, techs]) => `
#### ${category.charAt(0).toUpperCase() + category.slice(1)}
${techs.map(t => `- **${t.name}** (confidence: ${Math.round(t.confidence * 100)}%)`).join('\n')}
`).join('\n')}

## Architecture Analysis

- **Current Architecture**: ${tech.architecture_analysis.current_architecture}
- **Architecture Maturity**: ${tech.architecture_analysis.architecture_maturity}/10
- **Scalability Assessment**: ${tech.architecture_analysis.scalability_assessment}

### Evolution Path
${tech.architecture_analysis.evolution_path.map(step => `1. ${step}`).join('\n')}

## Security Analysis

### Current Security Patterns
${tech.security_analysis.current_security_patterns.map(p => `
- **${p.name}** (${Math.round(p.completeness * 100)}% complete)
  ${p.components ? p.components.map(c => `  - ${c}`).join('\n') : ''}
`).join('\n')}

### Security Score: ${tech.security_analysis.security_score}/10

### Security Gaps
${tech.security_analysis.security_gaps.map(g => `
- **${g.pattern}** (Priority: ${this.mapPriorityToLabel(g.priority)})
  - ${g.reasoning.join(', ')}
`).join('\n')}

## Infrastructure Analysis

${tech.infrastructure_analysis ? this.formatInfrastructureAnalysis(tech.infrastructure_analysis) : 'Infrastructure analysis not available'}

## Code Quality Analysis

${tech.code_quality_analysis ? this.formatCodeQualityAnalysis(tech.code_quality_analysis) : 'Code quality analysis not available'}
`;
    }
    
    generateGapAnalysisMarkdown(report) {
        const { gap_analysis: gaps } = report;
        
        return `# Gap Analysis Report

## Summary

- **Total Gaps**: ${gaps.summary.total_gaps}
- **Missing Patterns**: ${gaps.summary.missing_patterns}
- **Incomplete Patterns**: ${gaps.summary.incomplete_patterns}
- **Upgrade Opportunities**: ${gaps.summary.upgrade_opportunities}
- **Critical Gaps**: ${gaps.summary.critical_gaps}

## 🔴 Critical Gaps

${gaps.critical_gaps.map(gap => `
### ${gap.pattern.name}

**Priority**: ${this.mapPriorityToLabel(gap.priority)} | **Effort**: ${gap.effort.complexity} (${gap.effort.hours} hours)

**Why this matters**: ${gap.reasoning.join(', ')}

**Prerequisites**: ${gap.prerequisites.missing.length > 0 ? gap.prerequisites.missing.join(', ') : 'None'}
`).join('\n')}

## ⚠️ Incomplete Implementations

${gaps.incomplete_implementations.map(incomplete => `
### ${incomplete.pattern.name} (${Math.round(incomplete.current_completeness * 100)}% complete)

**Missing Components**:
${incomplete.missing_components.map(c => `- ${c.component}: ${c.description}`).join('\n')}

**Completion Effort**: ${incomplete.completion_effort.complexity} (${incomplete.completion_effort.hours} hours)
`).join('\n')}

## 🚀 Upgrade Opportunities

${gaps.upgrade_opportunities.map(upgrade => `
### ${upgrade.from} → ${upgrade.to}

**Benefits**: ${upgrade.benefits.join(', ')}

**Effort**: ${upgrade.effort.complexity} (${upgrade.effort.hours} hours)

**Compatibility**: ${upgrade.compatibility ? '✅ Compatible' : '⚠️ Requires changes'}
`).join('\n')}

## ⚡ Prioritized Recommendations

${gaps.prioritized_recommendations.slice(0, 10).map((rec, index) => `
${index + 1}. **${rec.pattern}** (${rec.type})
   - Priority: ${this.mapPriorityToLabel(rec.priority)}
   - Effort: ${rec.effort.complexity}
   - Reasoning: ${rec.reasoning}
`).join('\n')}

${gaps.pattern_conflicts.length > 0 ? `
## ⚠️ Pattern Conflicts

${gaps.pattern_conflicts.map(conflict => `
### ${conflict.pattern1} ↔ ${conflict.pattern2}

**Conflict Type**: ${conflict.conflict_type}

**Description**: ${conflict.description}

**Resolution**: ${conflict.resolution}
`).join('\n')}
` : ''}
`;
    }
    
    generateRoadmapMarkdown(report) {
        const { implementation_roadmap: roadmap } = report;
        
        return `# Implementation Roadmap

## Roadmap Overview

${Object.entries(roadmap.roadmap).map(([phase, data]) => `
## ${data.name}

${data.patterns.map(pattern => `
### ${pattern.pattern} (${pattern.type})
- **Priority**: ${this.mapPriorityToLabel(pattern.priority)}
- **Effort**: ${pattern.effort.complexity} (${pattern.effort.hours} hours)
- **Reasoning**: ${pattern.reasoning}
`).join('\n')}
`).join('\n')}

## Detailed Implementation Phases

${roadmap.detailed_phases.map(phase => `
### ${phase.name} (${phase.duration})

**Objectives**: ${phase.objectives.join(', ')}

**Deliverables**:
${phase.deliverables.map(d => `- ${d}`).join('\n')}

**Success Criteria**:
${phase.success_criteria.map(c => `- ${c}`).join('\n')}
`).join('\n')}

## Resource Requirements

- **Total Development Time**: ${roadmap.resource_requirements.total_hours} hours
- **Required Skills**: ${roadmap.resource_requirements.skills.join(', ')}
- **External Dependencies**: ${roadmap.resource_requirements.external_dependencies.join(', ')}

## Risk Assessment

${roadmap.risk_assessment.map(risk => `
### ${risk.category} - ${risk.level} Risk

**Description**: ${risk.description}

**Mitigation**: ${risk.mitigation}
`).join('\n')}

---

*Generated by Contextwarts Pattern Analysis Engine*
`;
    }
    
    // Utility methods for formatting and calculations
    categorizeTechnologies(technologies) {
        const categories = {};
        
        technologies.forEach(tech => {
            const category = tech.category || 'other';
            if (!categories[category]) categories[category] = [];
            categories[category].push(tech);
        });
        
        return categories;
    }
    
    calculateMaturityScore() {
        const { patterns, technologies } = this.analysisData;
        
        let score = 0;
        let maxScore = 10;
        
        // Technology diversity
        score += Math.min(technologies.technologies.length / 10, 2);
        
        // Pattern implementation
        score += Math.min(patterns.patterns.length / 5, 3);
        
        // Implementation quality
        const avgCompleteness = patterns.patterns.reduce((sum, p) => sum + (p.completeness || 0), 0) / patterns.patterns.length;
        score += avgCompleteness * 3;
        
        // Security consideration
        const hasSecurityPatterns = patterns.patterns.some(p => p.name.includes('security') || p.name.includes('auth'));
        if (hasSecurityPatterns) score += 2;
        
        return Math.round(score * 10) / 10;
    }
    
    mapPriorityToLabel(priority) {
        if (priority > 0.8) return 'Critical';
        if (priority > 0.6) return 'High';
        if (priority > 0.4) return 'Medium';
        return 'Low';
    }
    
    getPriorityEmoji(priority) {
        const label = this.mapPriorityToLabel(typeof priority === 'string' ? 0.5 : priority);
        switch (label) {
            case 'Critical': return '🔴';
            case 'High': return '🟡';
            case 'Medium': return '🟢';
            default: return '⚪';
        }
    }
    
    getEmojiForFindingType(type) {
        switch (type) {
            case 'positive': return '✅';
            case 'concern': return '🔴';
            case 'warning': return '⚠️';
            default: return 'ℹ️';
        }
    }
}

module.exports = AnalysisReportGenerator;

// CLI usage
if (require.main === module) {
    const generator = new AnalysisReportGenerator(process.cwd());
    generator.generateFullReport().then(report => {
        console.log('✅ Full analysis report generated');
        console.log('📁 Check .contextwarts/reports/ for detailed reports');
    });
}
```

## Master Analysis Script

```bash
#!/bin/bash
# scripts/analyze-project.sh

echo "🧙‍♂️ Contextwarts Project Analysis Starting..."

# Ensure analysis directory exists
mkdir -p .contextwarts/analysis

# Step 1: Project inventory
echo "📁 Step 1: Scanning project structure..."
bash scripts/scan-project.sh

# Step 2: Technology detection
echo "🔍 Step 2: Detecting technologies..."
node scripts/detect-technologies.js

# Step 3: Pattern detection
echo "🎯 Step 3: Detecting existing patterns..."
node scripts/detect-patterns.js

# Step 4: Interactive context gathering (if not exists)
if [ ! -f ".contextwarts/analysis/project-context.json" ]; then
    echo "💬 Step 4: Gathering project context..."
    node scripts/interactive-context.js
else
    echo "💬 Step 4: Using existing project context..."
fi

# Step 5: Gap analysis
echo "🔍 Step 5: Performing gap analysis..."
node scripts/gap-analysis.js

# Step 6: Generate comprehensive reports
echo "📋 Step 6: Generating analysis reports..."
node scripts/generate-analysis-report.js

echo "✅ Analysis complete!"
echo ""
echo "📊 Analysis Results:"
echo "  📁 Reports: .contextwarts/reports/"
echo "  📄 Executive Summary: .contextwarts/reports/executive-summary.md"
echo "  🔧 Technical Analysis: .contextwarts/reports/technical-analysis.md"
echo "  📈 Gap Analysis: .contextwarts/reports/gap-analysis.md"
echo "  🗺️ Implementation Roadmap: .contextwarts/reports/implementation-roadmap.md"
echo ""
echo "🎯 Next Steps:"
echo "  1. Review the executive summary"
echo "  2. Prioritize critical gaps"
echo "  3. Start with Phase 1 of the implementation roadmap"
echo "  4. Use '/wizard enhance [pattern-name]' to implement patterns"
```

This creates a comprehensive analysis system that can detect existing technologies and patterns, perform gap analysis, and generate detailed reports with recommendations. The system integrates with the `/wizard analyze` command to provide actionable insights for project improvement.