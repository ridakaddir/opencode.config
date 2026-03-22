---
description: Comprehensive project analysis with documentation generation and issue reporting
agent: codebase-analyzer
---

# 📊 Project Analysis

## Comprehensive Codebase Analysis

**Target**: @$ARGUMENTS

## Branch Management Check
!`git branch --show-current`

**📍 Current branch**: !`git branch --show-current`

**If on main/master and making changes**: Consider creating analysis branch:
```bash
/start-work
# Choose: "review project analysis" → review/YYYYMMDD-project-analysis
```

## Analysis Scope

**Analysis Type:**
- 🏗️ **Architecture Review**: System design and component relationships
- 📊 **Quality Assessment**: Code quality, patterns, and technical debt
- 📚 **Documentation Generation**: Comprehensive project documentation  
- 🎯 **Action Plan**: Prioritized improvement roadmap

## Project Discovery

### Technology Stack Detection
!`find . -name "package.json" -o -name "go.mod" -o -name "requirements.txt" -o -name "Cargo.toml" | head -5`

### Project Structure Overview  
!`tree -I node_modules -L 2 2>/dev/null || find . -maxdepth 2 -type d | grep -v node_modules | head -10`

### Recent Development Activity
!`git log --oneline -5`

## Analysis Configuration

**Select analysis depth:**

### Quick Analysis (5-10 minutes)
- Project structure overview
- Technology stack identification  
- Critical issue identification
- Basic metrics and health check

### Standard Analysis (20-30 minutes) 
- Complete architecture analysis
- Quality assessment with detailed findings
- Documentation generation
- Comprehensive action plan

### Deep Analysis (45-60 minutes)
- Exhaustive codebase review
- Performance and security analysis integration
- Complete documentation suite
- Detailed refactoring roadmap

## Generated Outputs

**This analysis will generate:**

### 📋 Analysis Report
- **Executive Summary**: Project overview and quality score
- **Architecture Documentation**: System design and components
- **Issue Inventory**: Categorized problems with priorities
- **Improvement Roadmap**: Actionable plan with timelines

### 📚 Documentation Files (Optional)
- `docs/ARCHITECTURE.md` - System architecture
- `docs/API.md` - API reference (if applicable)
- `docs/SETUP.md` - Development setup
- `docs/DEPLOYMENT.md` - Deployment guide
- `docs/TESTING.md` - Testing strategy
- `docs/CONTRIBUTING.md` - Development workflow

### 🎯 Action Items
- **Critical fixes** (immediate attention)
- **Important improvements** (short-term)
- **Optimization opportunities** (long-term)
- **Documentation tasks** (ongoing)

## Integration with Review Workflow

**For security-focused analysis**: Use security agent
**For performance-focused analysis**: Use performance agent
**For specific file review**: Use `/check-file [filename]`

---

**🚀 Ready to analyze! Choose your analysis depth and let's get started.**