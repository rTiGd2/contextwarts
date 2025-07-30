# /wizard analyze Command Implementation

## Purpose

The `/wizard analyze` command is the main entry point for comprehensive project analysis. It orchestrates the entire analysis pipeline from project scanning to report generation.

## Command Syntax

```bash
/wizard analyze [options]
```

### Options

- `--quick` - Skip interactive context gathering, use existing or defaults
- `--context-only` - Only gather project context, skip technical analysis
- `--no-reports` - Skip report generation, output JSON only
- `--format=[json|markdown|both]` - Output format (default: both)
- `--categories=[tech|patterns|gaps|all]` - Limit analysis scope

## Implementation

### Main Command Handler

```bash
#!/bin/bash
# wizard/commands/analyze.sh

# Contextwarts Project Analysis Command
# Usage: /wizard analyze [options]

set -e

# Parse command line arguments
QUICK_MODE=false
CONTEXT_ONLY=false
NO_REPORTS=false
OUTPUT_FORMAT="both"
CATEGORIES="all"

while [[ $# -gt 0 ]]; do
    case $1 in
        --quick)
            QUICK_MODE=true
            shift
            ;;
        --context-only)
            CONTEXT_ONLY=true
            shift
            ;;
        --no-reports) 
            NO_REPORTS=true
            shift
            ;;
        --format=*)
            OUTPUT_FORMAT="${1#*=}"
            shift
            ;;
        --categories=*)
            CATEGORIES="${1#*=}"
            shift
            ;;
        -h|--help)
            show_analyze_help
            exit 0
            ;;
        *)
            echo "Unknown option: $1"
            show_analyze_help
            exit 1
            ;;
    esac
done

# Main analysis function
function main() {
    echo "🧙‍♂️ Contextwarts Project Analysis"
    echo "=================================="
    echo ""
    
    # Check if we're in a valid project directory
    if [ ! -f "package.json" ] && [ ! -f "requirements.txt" ] && [ ! -f "*.csproj" ] && [ ! -d "src" ]; then
        echo "⚠️ This doesn't appear to be a code project directory."
        echo "Are you sure you want to analyze this directory? (y/N)"
        read -r response
        if [[ ! "$response" =~ ^[Yy]$ ]]; then
            echo "Analysis cancelled."
            exit 0
        fi
    fi
    
    # Setup analysis environment
    setup_analysis_environment
    
    # Run analysis pipeline
    if [ "$CONTEXT_ONLY" = true ]; then
        run_context_gathering
    else
        run_full_analysis
    fi
    
    # Generate reports if requested
    if [ "$NO_REPORTS" = false ]; then
        generate_analysis_reports
    fi
    
    # Display results
    display_analysis_results
}

function setup_analysis_environment() {
    echo "🔧 Setting up analysis environment..."
    
    # Create directory structure
    mkdir -p .contextwarts/analysis
    mkdir -p .contextwarts/reports
    mkdir -p .contextwarts/temp
    
    # Check for required tools
    check_analysis_tools
    
    # Load Contextwarts pattern library
    load_pattern_library
}

function check_analysis_tools() {
    local missing_tools=()
    
    # Check for Node.js (for JavaScript analysis)
    if ! command -v node &> /dev/null; then
        missing_tools+=("node")
    fi
    
    # Check for Python (for Python project analysis)
    if ! command -v python3 &> /dev/null && ! command -v python &> /dev/null; then
        missing_tools+=("python")
    fi
    
    # Check for jq (for JSON processing)
    if ! command -v jq &> /dev/null; then
        missing_tools+=("jq")
    fi
    
    if [ ${#missing_tools[@]} -gt 0 ]; then
        echo "⚠️ Missing required tools: ${missing_tools[*]}"
        echo "Some analysis features may be limited."
        echo "Install missing tools for full analysis capabilities."
    fi
}

function load_pattern_library() {
    echo "📚 Loading Contextwarts pattern library..."
    
    local contextwarts_home="$HOME/.contextwarts"
    if [ ! -d "$contextwarts_home" ]; then
        echo "❌ Contextwarts not found at $contextwarts_home"
        echo "Please install Contextwarts first: https://github.com/rTiGd2/contextwarts"
        exit 1
    fi
    
    # Create symlink to pattern library for analysis
    ln -sf "$contextwarts_home/patterns" .contextwarts/patterns 2>/dev/null || true
    ln -sf "$contextwarts_home/core" .contextwarts/core 2>/dev/null || true
    
    echo "✅ Pattern library loaded ($(find .contextwarts/patterns -name "*.yaml" | wc -l) patterns)"
}

function run_context_gathering() {
    echo "💬 Gathering project context..."
    
    if [ "$QUICK_MODE" = true ]; then
        # Generate basic context from project structure
        generate_basic_context
    else
        # Run interactive context gathering
        if command -v node &> /dev/null; then
            node "$HOME/.contextwarts/scripts/interactive-context.js" || generate_basic_context
        else
            echo "⚠️ Node.js not available, generating basic context"
            generate_basic_context
        fi
    fi
}

function generate_basic_context() {
    echo "📝 Generating basic project context..."
    
    cat > .contextwarts/analysis/project-context.json << EOF
{
  "generated_at": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "generation_method": "basic",
  "projectType": "$(detect_project_type)",
  "developmentStage": "$(detect_development_stage)",
  "teamSize": "$(detect_team_size)",
  "securityRequirements": "basic",
  "expectedScale": "medium"
}
EOF
    
    echo "✅ Basic context generated"
}

function detect_project_type() {
    if [ -f "package.json" ]; then
        if grep -q "react\|vue\|angular" package.json 2>/dev/null; then
            echo "Web Application (Frontend + Backend)"
        else
            echo "Backend API"
        fi
    elif [ -f "requirements.txt" ] || [ -f "pyproject.toml" ]; then
        echo "Backend API"
    elif ls *.csproj &>/dev/null; then
        echo "Web Application (Frontend + Backend)"
    else
        echo "Other"
    fi
}

function detect_development_stage() {
    if [ -d ".git" ]; then
        local commit_count=$(git rev-list --count HEAD 2>/dev/null || echo 0)
        if [ "$commit_count" -lt 10 ]; then
            echo "Just Starting (prototype)"
        elif [ "$commit_count" -lt 100 ]; then
            echo "Early Development (MVP)"
        else
            echo "Active Development"
        fi
    else
        echo "Just Starting (prototype)"
    fi
}

function detect_team_size() {
    if [ -d ".git" ]; then
        local author_count=$(git log --format='%an' | sort -u | wc -l 2>/dev/null || echo 1)
        if [ "$author_count" -eq 1 ]; then
            echo "Individual (just me)"
        elif [ "$author_count" -le 5 ]; then
            echo "Small Team (2-5 people)"
        else
            echo "Medium Team (6-15 people)"
        fi
    else
        echo "Individual (just me)"
    fi
}

function run_full_analysis() {
    echo "🔍 Running comprehensive project analysis..."
    
    # Step 1: Project inventory
    echo "📁 Step 1/6: Scanning project structure..."
    run_project_scan
    
    # Step 2: Technology detection
    echo "🔍 Step 2/6: Detecting technologies..."
    run_technology_detection
    
    # Step 3: Pattern detection
    echo "🎯 Step 3/6: Detecting existing patterns..."
    run_pattern_detection
    
    # Step 4: Context gathering
    echo "💬 Step 4/6: Project context..."
    run_context_gathering
    
    # Step 5: Gap analysis
    echo "📈 Step 5/6: Performing gap analysis..."
    run_gap_analysis
    
    # Step 6: Quality assessment
    echo "✅ Step 6/6: Assessing implementation quality..."
    run_quality_assessment
    
    echo "✅ Analysis pipeline complete!"
}

function run_project_scan() {
    # Project structure scanning
    cat > .contextwarts/analysis/project-inventory.json << EOF
{
  "scan_timestamp": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "project_root": "$(pwd)",
  "file_counts": {
    "total_files": $(find . -type f | grep -v node_modules | grep -v .git | grep -v .contextwarts | wc -l),
    "source_files": $(find . -name "*.js" -o -name "*.ts" -o -name "*.jsx" -o -name "*.tsx" -o -name "*.py" -o -name "*.java" -o -name "*.cs" -o -name "*.go" | grep -v node_modules | wc -l),
    "config_files": $(find . -name "*.json" -o -name "*.yaml" -o -name "*.yml" -o -name "*.toml" -o -name "*.ini" | grep -v node_modules | wc -l),
    "documentation": $(find . -name "*.md" -o -name "*.rst" -o -name "*.txt" | grep -v node_modules | wc -l)
  },
  "key_files": $(find . -maxdepth 2 -name "package.json" -o -name "requirements.txt" -o -name "*.csproj" -o -name "Dockerfile" -o -name "docker-compose.yml" | jq -R . | jq -s . 2>/dev/null || echo '[]'),
  "directory_structure": $(find . -type d -maxdepth 3 | grep -v node_modules | grep -v .git | grep -v .contextwarts | head -20 | jq -R . | jq -s . 2>/dev/null || echo '[]')
}
EOF
}

function run_technology_detection() {
    if command -v node &> /dev/null; then
        # Use Node.js-based technology detector if available
        if [ -f "$HOME/.contextwarts/scripts/detect-technologies.js" ]; then
            node "$HOME/.contextwarts/scripts/detect-technologies.js" || run_basic_technology_detection
        else
            run_basic_technology_detection
        fi
    else
        run_basic_technology_detection
    fi
}

function run_basic_technology_detection() {
    echo "🔍 Running basic technology detection..."
    
    local technologies=()
    local confidence=()
    
    # JavaScript/Node.js detection
    if [ -f "package.json" ]; then
        technologies+=("\"node\"")
        confidence+=("0.9")
        
        if grep -q "react" package.json 2>/dev/null; then
            technologies+=("\"react\"")
            confidence+=("0.9")
        fi
        
        if grep -q "vue" package.json 2>/dev/null; then
            technologies+=("\"vue\"")
            confidence+=("0.9")
        fi
        
        if grep -q "typescript" package.json 2>/dev/null; then
            technologies+=("\"typescript\"")
            confidence+=("0.9")
        fi
        
        if grep -q "express" package.json 2>/dev/null; then
            technologies+=("\"express\"")
            confidence+=("0.8")
        fi
    fi
    
    # Python detection
    if [ -f "requirements.txt" ] || [ -f "pyproject.toml" ]; then
        technologies+=("\"python\"")
        confidence+=("0.9")
        
        if grep -q "django\|flask\|fastapi" requirements.txt pyproject.toml 2>/dev/null; then
            technologies+=("\"python-web\"")
            confidence+=("0.8")
        fi
    fi
    
    # .NET detection
    if ls *.csproj &>/dev/null; then
        technologies+=("\"dotnet\"")
        confidence+=("0.9")
    fi
    
    # Docker detection
    if [ -f "Dockerfile" ]; then
        technologies+=("\"docker\"")
        confidence+=("0.9")
    fi
    
    # Create technology report
    cat > .contextwarts/analysis/technology-report.json << EOF
{
  "scan_timestamp": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "detection_method": "basic",
  "total_technologies": ${#technologies[@]},
  "high_confidence": ${#technologies[@]},
  "technologies": [
$(for i in "${!technologies[@]}"; do
    echo "    {\"id\": ${technologies[$i]}, \"name\": ${technologies[$i]}, \"confidence\": ${confidence[$i]}, \"category\": \"detected\"}"
    [ $i -lt $((${#technologies[@]} - 1)) ] && echo ","
done)
  ]
}
EOF
}

function run_pattern_detection() {
    if command -v node &> /dev/null && [ -f "$HOME/.contextwarts/scripts/detect-patterns.js" ]; then
        node "$HOME/.contextwarts/scripts/detect-patterns.js" || run_basic_pattern_detection
    else
        run_basic_pattern_detection
    fi
}

function run_basic_pattern_detection() {
    echo "🎯 Running basic pattern detection..."
    
    local patterns=()
    
    # Modern web stack detection
    if [ -f "package.json" ] && grep -q "react\|vue" package.json 2>/dev/null && grep -q "typescript" package.json 2>/dev/null; then
        patterns+=('{"id": "modern-web-stack", "name": "Modern Web Stack", "confidence": 0.8, "completeness": 0.7}')
    fi
    
    # Container pattern detection
    if [ -f "Dockerfile" ]; then
        patterns+=('{"id": "container-first-deployment", "name": "Container First Deployment", "confidence": 0.9, "completeness": 0.6}')
    fi
    
    # API pattern detection
    if grep -r "app.get\|app.post\|@app.route\|ApiController" . --include="*.js" --include="*.py" --include="*.cs" 2>/dev/null | head -1 >/dev/null; then
        patterns+=('{"id": "rest-api-pattern", "name": "REST API", "confidence": 0.7, "completeness": 0.6}')
    fi
    
    # Authentication pattern detection
    if grep -r "auth\|login\|jwt\|passport" . --include="*.js" --include="*.py" --include="*.cs" 2>/dev/null | head -1 >/dev/null; then
        patterns+=('{"id": "basic-authentication", "name": "Basic Authentication", "confidence": 0.6, "completeness": 0.5}')
    fi
    
    # Create pattern report
    cat > .contextwarts/analysis/pattern-report.json << EOF
{
  "scan_timestamp": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "detection_method": "basic",
  "total_patterns": ${#patterns[@]},
  "high_confidence": ${#patterns[@]},
  "patterns": [
$(IFS=','; echo "${patterns[*]}")
  ]
}
EOF
}

function run_gap_analysis() {
    if command -v node &> /dev/null && [ -f "$HOME/.contextwarts/scripts/gap-analysis.js" ]; then
        node "$HOME/.contextwarts/scripts/gap-analysis.js" || run_basic_gap_analysis
    else
        run_basic_gap_analysis
    fi
}

function run_basic_gap_analysis() {
    echo "📈 Running basic gap analysis..."
    
    # Load detected patterns
    local detected_patterns=""
    if [ -f ".contextwarts/analysis/pattern-report.json" ]; then
        detected_patterns=$(cat .contextwarts/analysis/pattern-report.json | jq -r '.patterns[].id' 2>/dev/null || echo "")
    fi
    
    # Suggest common missing patterns
    local missing_patterns=()
    
    # Security gaps
    if ! echo "$detected_patterns" | grep -q "authentication"; then
        missing_patterns+=('{"pattern": {"name": "advanced-authentication"}, "priority": 0.8, "reasoning": ["No authentication system detected"]}')
    fi
    
    if ! echo "$detected_patterns" | grep -q "https"; then
        missing_patterns+=('{"pattern": {"name": "https-security"}, "priority": 0.9, "reasoning": ["HTTPS security not detected"]}')
    fi
    
    # Quality gaps
    if [ ! -f ".eslintrc.js" ] && [ ! -f ".eslintrc.json" ] && [ ! -f "pyproject.toml" ]; then
        missing_patterns+=('{"pattern": {"name": "development-quality-automation"}, "priority": 0.7, "reasoning": ["No quality automation detected"]}')
    fi
    
    # Create gap analysis report
    cat > .contextwarts/analysis/gap-analysis.json << EOF
{
  "analysis_timestamp": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "analysis_method": "basic",
  "summary": {
    "total_gaps": ${#missing_patterns[@]},
    "missing_patterns": ${#missing_patterns[@]},
    "incomplete_patterns": 0,
    "upgrade_opportunities": 0,
    "critical_gaps": $(echo "${missing_patterns[*]}" | grep -o "0\.[89]" | wc -l)
  },
  "gaps": {
    "missing": [
$(IFS=','; echo "${missing_patterns[*]}")
    ],
    "incomplete": [],
    "upgrades": [],
    "conflicts": []
  },
  "recommendations": [
$(for pattern in "${missing_patterns[@]}"; do
    echo "    {\"type\": \"missing\", \"pattern\": $(echo "$pattern" | jq -r '.pattern.name'), \"priority\": $(echo "$pattern" | jq -r '.priority'), \"effort\": {\"complexity\": \"medium\", \"hours\": 8}}"
    [ "$pattern" != "${missing_patterns[-1]}" ] && echo ","
done)
  ]
}
EOF
}

function run_quality_assessment() {
    echo "✅ Assessing implementation quality..."
    
    # Basic quality metrics
    local test_files=$(find . -name "*.test.*" -o -name "*_test.*" -o -name "test_*" | grep -v node_modules | wc -l)
    local source_files=$(find . -name "*.js" -o -name "*.ts" -o -name "*.py" -o -name "*.cs" | grep -v node_modules | wc -l)
    local has_linting=false
    local has_formatting=false
    
    if [ -f ".eslintrc.js" ] || [ -f ".eslintrc.json" ] || [ -f "pyproject.toml" ]; then
        has_linting=true
    fi
    
    if [ -f ".prettierrc" ] || [ -f "pyproject.toml" ]; then
        has_formatting=true
    fi
    
    # Calculate quality score
    local quality_score=0
    
    # Test coverage contribution (0-3 points)
    if [ "$source_files" -gt 0 ]; then
        local test_ratio=$((test_files * 100 / source_files))
        if [ "$test_ratio" -ge 80 ]; then
            quality_score=$((quality_score + 3))
        elif [ "$test_ratio" -ge 50 ]; then
            quality_score=$((quality_score + 2))
        elif [ "$test_ratio" -gt 0 ]; then
            quality_score=$((quality_score + 1))
        fi
    fi
    
    # Code quality tools (0-4 points)
    if [ "$has_linting" = true ]; then
        quality_score=$((quality_score + 2))
    fi
    if [ "$has_formatting" = true ]; then
        quality_score=$((quality_score + 2))
    fi
    
    # Documentation (0-2 points)
    if [ -f "README.md" ]; then
        quality_score=$((quality_score + 1))
    fi
    if [ -d "docs" ] || find . -name "*.md" | grep -v README | head -1 >/dev/null; then
        quality_score=$((quality_score + 1))
    fi
    
    # CI/CD (0-1 point)
    if [ -d ".github/workflows" ] || [ -f ".gitlab-ci.yml" ]; then
        quality_score=$((quality_score + 1))
    fi
    
    # Create quality assessment
    cat > .contextwarts/analysis/quality-assessment.json << EOF
{
  "assessment_timestamp": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "quality_score": $quality_score,
  "max_score": 10,
  "metrics": {
    "test_coverage_ratio": $([ "$source_files" -gt 0 ] && echo "$((test_files * 100 / source_files))" || echo "0"),
    "has_linting": $has_linting,
    "has_formatting": $has_formatting,
    "has_documentation": $([ -f "README.md" ] && echo "true" || echo "false"),
    "has_ci_cd": $([ -d ".github/workflows" ] || [ -f ".gitlab-ci.yml" ] && echo "true" || echo "false")
  },
  "recommendations": [
$([ "$quality_score" -lt 5 ] && echo "    \"Consider implementing basic quality automation\"")
$([ "$test_files" -eq 0 ] && echo "    \"Add automated testing to improve reliability\"")
$([ "$has_linting" = false ] && echo "    \"Add code linting for consistency\"")
$([ ! -f "README.md" ] && echo "    \"Create project documentation\"")
  ]
}
EOF
}

function generate_analysis_reports() {
    echo "📋 Generating analysis reports..."
    
    if command -v node &> /dev/null && [ -f "$HOME/.contextwarts/scripts/generate-analysis-report.js" ]; then
        node "$HOME/.contextwarts/scripts/generate-analysis-report.js" || generate_basic_reports
    else
        generate_basic_reports
    fi
}

function generate_basic_reports() {
    echo "📄 Generating basic analysis reports..."
    
    local report_dir=".contextwarts/reports"
    mkdir -p "$report_dir"
    
    # Generate executive summary
    cat > "$report_dir/executive-summary.md" << 'EOF'
# Project Analysis - Executive Summary

## Overview

This project has been analyzed using Contextwarts Pattern Analysis Engine.

## Key Findings

EOF
    
    # Add technology summary
    if [ -f ".contextwarts/analysis/technology-report.json" ]; then
        echo "### Detected Technologies" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
        jq -r '.technologies[] | "- " + .name + " (confidence: " + (.confidence * 100 | floor | tostring) + "%)"' .contextwarts/analysis/technology-report.json >> "$report_dir/executive-summary.md" 2>/dev/null || echo "- Technology detection data not available" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
    fi
    
    # Add pattern summary
    if [ -f ".contextwarts/analysis/pattern-report.json" ]; then
        echo "### Implemented Patterns" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
        jq -r '.patterns[] | "- " + .name + " (" + (.completeness * 100 | floor | tostring) + "% complete)"' .contextwarts/analysis/pattern-report.json >> "$report_dir/executive-summary.md" 2>/dev/null || echo "- Pattern detection data not available" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
    fi
    
    # Add recommendations
    if [ -f ".contextwarts/analysis/gap-analysis.json" ]; then
        echo "### Priority Recommendations" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
        jq -r '.recommendations[] | "1. Implement " + .pattern + " (Priority: " + (.priority * 10 | floor | tostring) + "/10)"' .contextwarts/analysis/gap-analysis.json >> "$report_dir/executive-summary.md" 2>/dev/null || echo "- Gap analysis data not available" >> "$report_dir/executive-summary.md"
        echo "" >> "$report_dir/executive-summary.md"
    fi
    
    cat >> "$report_dir/executive-summary.md" << 'EOF'

## Next Steps

1. Review the detailed technical analysis
2. Prioritize critical security and infrastructure gaps
3. Implement recommended patterns using `/wizard enhance [pattern-name]`
4. Re-run analysis after implementing improvements

---

*Generated by Contextwarts Pattern Analysis Engine*
EOF
    
    echo "✅ Basic reports generated in $report_dir/"
}

function display_analysis_results() {
    echo ""
    echo "🎉 Analysis Complete!"
    echo "===================="
    echo ""
    
    # Display summary statistics
    if [ -f ".contextwarts/analysis/technology-report.json" ]; then
        local tech_count=$(jq -r '.total_technologies' .contextwarts/analysis/technology-report.json 2>/dev/null || echo "0")
        echo "🔍 Technologies detected: $tech_count"
    fi
    
    if [ -f ".contextwarts/analysis/pattern-report.json" ]; then
        local pattern_count=$(jq -r '.total_patterns' .contextwarts/analysis/pattern-report.json 2>/dev/null || echo "0")
        echo "🎯 Patterns detected: $pattern_count"
    fi
    
    if [ -f ".contextwarts/analysis/gap-analysis.json" ]; then
        local gap_count=$(jq -r '.summary.total_gaps' .contextwarts/analysis/gap-analysis.json 2>/dev/null || echo "0")
        local critical_gaps=$(jq -r '.summary.critical_gaps' .contextwarts/analysis/gap-analysis.json 2>/dev/null || echo "0")
        echo "📈 Improvement opportunities: $gap_count ($critical_gaps critical)"
    fi
    
    if [ -f ".contextwarts/analysis/quality-assessment.json" ]; then
        local quality_score=$(jq -r '.quality_score' .contextwarts/analysis/quality-assessment.json 2>/dev/null || echo "0")
        echo "✅ Quality score: $quality_score/10"
    fi
    
    echo ""
    echo "📁 Analysis files saved to:"
    echo "  📊 Raw data: .contextwarts/analysis/"
    echo "  📋 Reports: .contextwarts/reports/"
    echo ""
    echo "📄 Key reports:"
    echo "  • Executive Summary: .contextwarts/reports/executive-summary.md"
    if [ -f ".contextwarts/reports/technical-analysis.md" ]; then
        echo "  • Technical Analysis: .contextwarts/reports/technical-analysis.md"
    fi
    if [ -f ".contextwarts/reports/gap-analysis.md" ]; then
        echo "  • Gap Analysis: .contextwarts/reports/gap-analysis.md"
    fi
    if [ -f ".contextwarts/reports/implementation-roadmap.md" ]; then
        echo "  • Implementation Roadmap: .contextwarts/reports/implementation-roadmap.md"
    fi
    
    echo ""
    echo "🚀 Next steps:"
    echo "  1. Review executive summary: cat .contextwarts/reports/executive-summary.md"
    echo "  2. Implement critical patterns: /wizard enhance [pattern-name]"
    echo "  3. Re-analyze after improvements: /wizard analyze"
    echo ""
    
    # Show top 3 recommendations
    if [ -f ".contextwarts/analysis/gap-analysis.json" ]; then
        echo "🎯 Top recommendations:"
        jq -r '.recommendations[0:3][] | "  • /wizard enhance " + .pattern + " (Priority: " + (.priority * 10 | floor | tostring) + "/10)"' .contextwarts/analysis/gap-analysis.json 2>/dev/null || echo "  • No specific recommendations available"
        echo ""
    fi
}

function show_analyze_help() {
    cat << 'EOF'
🧙‍♂️ Contextwarts Project Analysis

USAGE:
  /wizard analyze [options]

OPTIONS:
  --quick              Skip interactive context gathering
  --context-only       Only gather project context
  --no-reports         Skip report generation, output JSON only
  --format=[format]    Output format: json, markdown, both (default: both)
  --categories=[cats]  Analysis scope: tech, patterns, gaps, all (default: all)
  -h, --help          Show this help message

EXAMPLES:
  /wizard analyze                    # Full analysis with interactive context
  /wizard analyze --quick            # Quick analysis with basic context
  /wizard analyze --context-only     # Only gather project context
  /wizard analyze --format=json      # Output only JSON data

ANALYSIS PIPELINE:
  1. Project structure scanning
  2. Technology detection (languages, frameworks, tools)
  3. Pattern detection (existing architecture and methodology patterns)
  4. Context gathering (project requirements and constraints)
  5. Gap analysis (missing patterns and improvement opportunities)
  6. Report generation (executive summary and technical analysis)

OUTPUT:
  • .contextwarts/analysis/          Raw analysis data (JSON)
  • .contextwarts/reports/           Human-readable reports (Markdown)

The analysis identifies current implementation state and provides prioritized
recommendations for applying Contextwarts patterns to improve your project.

For more information: /wizard help analyze
EOF
}

# Run main function
main "$@"
```

This comprehensive analysis system provides:

1. **Full project scanning** - Technology, pattern, and structure detection
2. **Interactive context gathering** - Understanding project requirements and constraints
3. **Gap analysis** - Comparing current state against pattern library
4. **Report generation** - Executive summaries and technical analysis
5. **Actionable recommendations** - Prioritized next steps for improvement

The system works as both a standalone analysis tool and integrates with the full Contextwarts pattern application workflow.