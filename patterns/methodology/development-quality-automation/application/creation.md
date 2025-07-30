# Development Quality Automation - Creation Mode

## When to Use Creation Mode

Use this mode when starting a new project and want to establish comprehensive quality automation from the beginning. This ensures quality is built into the foundation rather than added later.

## Pre-Implementation Assessment

### Project Requirements Analysis
1. **Team Size**: Individual, small team (2-5), medium team (6-15), large team (15+)
2. **Project Complexity**: Simple, moderate, complex, enterprise-scale
3. **Technology Stack**: Frontend, backend, full-stack, mobile, desktop
4. **Deployment Frequency**: Multiple daily, daily, weekly, monthly
5. **Quality Standards**: Startup-flexible, corporate-standard, enterprise-strict

### Context Questions
```yaml
quality_automation_setup:
  team_experience:
    question: "What is your team's experience with quality automation?"
    impact: "Determines complexity of initial setup"
    
  quality_priorities:
    question: "Which quality aspects are most critical?"
    options:
      - code_consistency: "Formatting and style enforcement"
      - test_coverage: "Comprehensive testing requirements"
      - security: "Security scanning and vulnerability detection"
      - performance: "Performance monitoring and optimization"
    
  deployment_strategy:
    question: "What deployment strategy will you use?"
    impact: "Influences CI/CD quality gate configuration"
    
  compliance_requirements:
    question: "Are there regulatory or compliance requirements?"
    impact: "Adds specialized quality checks and documentation"
```

## Implementation Roadmap

### Phase 1: Foundation Setup (Day 1-2)

#### Step 1: Project Structure
```bash
# Create quality automation directories
mkdir -p .github/workflows
mkdir -p .husky
mkdir -p scripts
mkdir -p docs/quality

# Initialize basic configuration files
touch .editorconfig
touch .gitignore
touch .pre-commit-config.yaml
```

#### Step 2: Version Control Configuration
```bash
# Initialize git with quality-focused structure
git init
git config core.autocrlf false
git config core.eol lf

# Add initial .gitignore
cat > .gitignore << EOF
# Dependencies
node_modules/
__pycache__/
*.pyc
venv/
.env

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Coverage and testing
coverage/
.coverage
.nyc_output
htmlcov/

# Quality tools
.mypy_cache/
.pytest_cache/
.eslintcache
EOF
```

#### Step 3: Editor Configuration
```ini
# .editorconfig
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 2

[*.{py,pyi}]
indent_size = 4

[*.{md,yaml,yml}]
trim_trailing_whitespace = false

[Makefile]
indent_style = tab
```

### Phase 2: Core Quality Tools (Day 2-3)

#### Technology-Specific Setup

**For JavaScript/TypeScript Projects:**
```json
{
  "name": "your-project",
  "scripts": {
    "lint": "eslint src/ --ext .js,.jsx,.ts,.tsx",
    "lint:fix": "eslint src/ --ext .js,.jsx,.ts,.tsx --fix",
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "type-check": "tsc --noEmit",
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage",
    "quality": "npm run lint && npm run format:check && npm run type-check && npm run test"
  },
  "devDependencies": {
    "@typescript-eslint/eslint-plugin": "^5.0.0",
    "@typescript-eslint/parser": "^5.0.0",
    "eslint": "^8.0.0",
    "eslint-config-prettier": "^8.0.0",
    "eslint-plugin-react": "^7.0.0",
    "prettier": "^2.0.0",
    "typescript": "^4.0.0",
    "jest": "^29.0.0",
    "@types/jest": "^29.0.0",
    "husky": "^8.0.0",
    "lint-staged": "^13.0.0"
  }
}
```

**For Python Projects:**
```toml
# pyproject.toml
[tool.poetry.group.dev.dependencies]
black = "^22.10.0"
flake8 = "^5.0.4"
mypy = "^0.991"
pytest = "^7.2.0"
pytest-cov = "^4.0.0"
pre-commit = "^2.20.0"
isort = "^5.10.0"

[tool.black]
line-length = 88
target-version = ['py311']

[tool.isort]
profile = "black"
line_length = 88

[tool.mypy]
python_version = "3.11"
strict = true
warn_unused_ignores = true

[tool.pytest.ini_options]
testpaths = ["tests"]
python_files = ["test_*.py", "*_test.py"]
addopts = "--strict-markers --strict-config --cov=src --cov-report=html --cov-report=term"
```

#### Pre-Commit Hooks Setup
```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-json
      - id: check-merge-conflict
      - id: check-case-conflict

  # Language-specific hooks
  - repo: https://github.com/psf/black
    rev: 22.10.0
    hooks:
      - id: black
  
  - repo: https://github.com/pycqa/isort
    rev: 5.10.1
    hooks:
      - id: isort
  
  - repo: https://github.com/pycqa/flake8
    rev: 5.0.4
    hooks:
      - id: flake8

  # Security hooks
  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.4
    hooks:
      - id: bandit
        args: ['-r', 'src/']
```

### Phase 3: Continuous Integration (Day 3-4)

#### GitHub Actions Workflow
```yaml
# .github/workflows/quality.yml
name: Quality Assurance

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

env:
  PYTHON_VERSION: '3.11'
  NODE_VERSION: '18.x'

jobs:
  quality-check:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: ${{ env.PYTHON_VERSION }}
        cache: 'pip'
    
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        pip install -r requirements-dev.txt
    
    - name: Code formatting check
      run: |
        black --check src/ tests/
        isort --check-only src/ tests/
    
    - name: Linting
      run: |
        flake8 src/ tests/
        mypy src/
    
    - name: Security scan
      run: |
        bandit -r src/
        safety check
    
    - name: Run tests
      run: |
        pytest --cov=src --cov-report=xml --cov-report=html --cov-fail-under=80
    
    - name: Upload coverage to Codecov
      uses: codecov/codecov-action@v3
      with:
        file: ./coverage.xml
        fail_ci_if_error: true
    
    - name: Generate coverage badge
      uses: tj-actions/coverage-badge-py@v2
      with:
        output: coverage.svg
```

### Phase 4: Advanced Quality Features (Day 4-5)

#### Code Quality Configuration

**ESLint Configuration (.eslintrc.js):**
```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 2021,
    sourceType: 'module',
    ecmaFeatures: {
      jsx: true,
    },
  },
  plugins: ['@typescript-eslint', 'react', 'react-hooks'],
  extends: [
    'eslint:recommended',
    '@typescript-eslint/recommended',
    'plugin:react/recommended',
    'plugin:react-hooks/recommended',
    'prettier',
  ],
  rules: {
    '@typescript-eslint/no-unused-vars': 'error',
    '@typescript-eslint/no-explicit-any': 'warn',
    'react/prop-types': 'off',
    'react/react-in-jsx-scope': 'off',
  },
  settings: {
    react: {
      version: 'detect',
    },
  },
};
```

**Prettier Configuration (.prettierrc):**
```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false
}
```

#### Testing Configuration

**Jest Configuration (jest.config.js):**
```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  roots: ['<rootDir>/src', '<rootDir>/tests'],
  testMatch: ['**/__tests__/**/*.ts', '**/?(*.)+(spec|test).ts'],
  collectCoverageFrom: [
    'src/**/*.ts',
    '!src/**/*.d.ts',
    '!src/index.ts',
  ],
  coverageReporters: ['text', 'lcov', 'html'],
  coverageThreshold: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },
  setupFilesAfterEnv: ['<rootDir>/tests/setup.ts'],
};
```

### Phase 5: Documentation and Process (Day 5)

#### Development Workflow Documentation
```markdown
# docs/quality/development-workflow.md

# Development Workflow Guide

## Daily Development Process

1. **Start Development**
   ```bash
   git checkout -b feature/new-feature
   ```

2. **Write Code with Quality in Mind**
   - Follow TDD: Write tests first
   - Use consistent formatting (automated)
   - Write clear, self-documenting code

3. **Pre-Commit Quality Check**
   ```bash
   # Automatic via pre-commit hooks
   git commit -m "feat: add new feature"
   ```

4. **Push and Create PR**
   ```bash
   git push origin feature/new-feature
   # Create PR via GitHub interface
   ```

5. **Quality Gates Validation**
   - Automated CI checks run
   - Code coverage validation
   - Security scanning
   - Performance checks

## Quality Standards

### Code Coverage
- Minimum 80% line coverage
- 70% branch coverage
- New code must have 90% coverage

### Code Style
- Automated formatting with Black/Prettier
- No linting errors allowed
- Type hints required for Python
- TypeScript strict mode enabled

### Security
- No high-severity vulnerabilities
- Dependency scanning on all PRs
- Secret scanning enabled
- Regular security audits
```

#### Quality Metrics Dashboard
```markdown
# docs/quality/metrics.md

# Quality Metrics

## Current Status
![Coverage](coverage.svg)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=your-project&metric=alert_status)](https://sonarcloud.io/dashboard?id=your-project)

## Metrics Tracking

### Code Quality
- **Code Coverage**: Target 80%+
- **Technical Debt**: < 30 minutes
- **Maintainability Rating**: A
- **Reliability Rating**: A
- **Security Rating**: A

### Process Metrics
- **Build Success Rate**: Target 95%+
- **Deployment Success Rate**: Target 99%+
- **Mean Time to Recovery**: < 1 hour
- **PR Review Time**: < 24 hours
```

## Success Validation

### Automated Validation Checklist
```bash
#!/bin/bash
# scripts/validate-quality-setup.sh

echo "🔍 Validating Quality Automation Setup..."

# Check pre-commit hooks
if pre-commit --version > /dev/null 2>&1; then
    echo "✅ Pre-commit hooks installed"
else
    echo "❌ Pre-commit hooks missing"
    exit 1
fi

# Check quality tools
echo "🔧 Checking quality tools..."
black --version || echo "❌ Black not installed"
flake8 --version || echo "❌ Flake8 not installed"
mypy --version || echo "❌ MyPy not installed"

# Run quality checks
echo "🧪 Running quality validation..."
pre-commit run --all-files
pytest --cov=src --cov-fail-under=80

echo "✅ Quality automation setup complete!"
```

### Manual Validation Steps
1. **Create test commit**: Verify pre-commit hooks work
2. **Create PR**: Verify CI pipeline runs
3. **Check coverage**: Verify coverage reporting works
4. **Review metrics**: Confirm quality metrics are being collected
5. **Test deployment**: Verify deployment gates work

## Customization Options

### Strict Quality Mode
```yaml
# For enterprise or critical applications
quality_strictness: strict
coverage_threshold: 90
security_scanning: comprehensive
performance_testing: required
documentation_coverage: 80
```

### Balanced Quality Mode  
```yaml
# For most development teams
quality_strictness: balanced
coverage_threshold: 80
security_scanning: standard
performance_testing: optional
documentation_coverage: 60
```

### Flexible Quality Mode
```yaml
# For rapid prototyping or startups
quality_strictness: flexible
coverage_threshold: 60
security_scanning: basic
performance_testing: disabled
documentation_coverage: 40
```

## Integration with Other Patterns

### Test-Driven Development
- Pre-commit hooks ensure tests run before commit
- CI pipeline validates TDD cycle compliance
- Coverage requirements enforce test-first approach

### Behavior-Driven Development  
- Gherkin scenario validation
- Living documentation generation
- Scenario-to-code traceability

### Container-First Deployment
- Quality checks in Docker builds
- Multi-stage builds with quality gates
- Container security scanning

## Next Steps

1. **Week 1**: Complete basic setup and team training
2. **Week 2**: Monitor quality metrics and adjust thresholds
3. **Week 3**: Add advanced features (security scanning, performance testing)
4. **Week 4**: Optimize CI performance and developer experience
5. **Month 2+**: Continuous improvement based on metrics and feedback

## Troubleshooting

### Common Setup Issues
- **Pre-commit hooks not running**: Check git hooks installation
- **CI failing on setup**: Verify dependency versions match
- **Coverage too low**: Review test strategy and add missing tests
- **Linting errors**: Run auto-fix commands and update configuration

### Performance Optimization
- **Slow CI builds**: Use caching and parallel execution
- **Large repository**: Use incremental linting and testing
- **Complex quality checks**: Split into separate jobs

This creation mode implementation provides a comprehensive foundation for quality automation that can be customized based on project needs and team preferences.