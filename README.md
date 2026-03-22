# OpenCode Configuration

My personal OpenCode global configuration with custom agents and commands for enhanced development workflow.

## Features

- **Automatic Branch Management**: OpenCode automatically creates feature branches for development work
- **Enhanced Review System**: Multi-agent code review with security, performance, and architecture analysis
- **Comprehensive Analysis**: Full codebase analysis with documentation generation and issue reporting
- **Review Agents**: 
  - **Security Agent** - Deep security vulnerability analysis
  - **Performance Agent** - Performance bottleneck identification  
  - **Codebase Analyzer** - Comprehensive project analysis and documentation
  - **Review Agent** - General code review focusing on correctness and maintainability
- **Testing Skills** (Implementing ["Testing with AI" Article](https://ridakaddir.com/blog/post/testing-with-ai-smarter-coverage-faster-feedback)):
  - **Adversarial Testing** - Edge case generation that finds scenarios developers miss
  - **Coverage-Driven Testing** - Precision testing targeting specific uncovered lines
  - **Mock Generation** - Jest/Go mocks with deep mockr integration for HTTP-level API mocking
  - **Integration Testing** - Complete test scaffolding with database setup and environment configuration
  - **Test-Driven Development** - Test-first workflow with AI-generated specifications
- **Review Skills**:
  - **Security Review** - Security-focused analysis with threat modeling
  - **Review Preparation** - Comprehensive review prep and checklist generation
  - **Enhanced File Review** - Multi-agent coordinated file analysis
- **Custom Commands**: 
  - `/start-work` - Begin development with automatic branch creation
  - `/security-scan` - Quick security vulnerability scan
  - `/analyze-project` - Comprehensive project analysis
  - `/check-file` - Review specific files for issues
  - `/pr-summary` - Generate PR descriptions from branch diff
  - `/review-changes` - Analyze recent git changes

## Setup

1. Clone this repository to your OpenCode config directory:
   ```bash
   git clone https://github.com/ridakaddir/opencode.config.git ~/.config/opencode
   ```

2. Copy the example configuration:
   ```bash
   cp opencode.example.json opencode.json
   ```

3. Set your Context7 API key:
   ```bash
   export CONTEXT7_API_KEY="your-api-key-here"
   ```
   
   Or add it to your shell profile for persistence:
   ```bash
   echo 'export CONTEXT7_API_KEY="your-api-key-here"' >> ~/.zshrc
   ```

4. Install dependencies:
   ```bash
   npm install
   ```

## Configuration

### Environment Variables

- `CONTEXT7_API_KEY`: Your Context7 API key for enhanced documentation access

### Agents

#### Review Agent (`agents/review.md`)
- Read-only code review agent
- Focuses on logic errors, security issues, and architectural violations
- Temperature: 0.1 for consistency
- Permissions: Read-only with limited git commands allowed

### Commands

#### `/start-work`
Begin development work with automatic branch creation and management.

**Features:**
- Automatically detects if you're on main/master branch
- Suggests appropriate branch names based on work type
- Provides clear opt-out options for working on current branch
- Handles dirty working tree scenarios

**Usage:**
```bash
/start-work
# Follow the prompts to describe your work
# Example: "user authentication" → feature/20260322-user-authentication
```

**Branch Types:**
- `feature/` - New functionality, testing, development
- `fix/` - Bug fixes and patches
- `review/` - Code review and analysis work
- `poc/` - Proof of concept and experiments
- `docs/` - Documentation updates
- `refactor/` - Code restructuring

**Opt-out Options:**
- Type "current" to continue on current branch
- Type "main" to work directly on main (not recommended)
- Use `--no-branch` flag to skip branch creation

#### `/security-scan [target]`
Quick security vulnerability scan with immediate feedback.

**Features:**
- Scans for hardcoded secrets and credentials
- Detects common XSS and SQL injection patterns
- Checks for insecure dependencies
- Reviews environment configuration
- Provides quick remediation guidance

**Usage:**
```bash
/security-scan
/security-scan src/auth/
```

#### `/analyze-project [target]`  
Comprehensive project analysis with documentation generation.

**Features:**
- Complete architecture analysis
- Quality assessment with detailed findings
- Documentation generation (ARCHITECTURE.md, SETUP.md, etc.)
- Prioritized improvement roadmap
- Integration with security and performance agents

**Analysis Depths:**
- **Quick** (5-10 min) - Overview and critical issues
- **Standard** (20-30 min) - Complete analysis with documentation
- **Deep** (45-60 min) - Exhaustive review with refactoring roadmap

#### `/check-file <file-path>`
Review a specific file for issues and improvements.

**Example:**
```bash
/check-file src/components/UserAuth.tsx
```

#### `/pr-summary` 
Generate a comprehensive PR description from the current branch diff.

**Features:**
- Analyzes commits from main branch
- Creates structured PR description
- Includes testing notes and breaking changes

#### `/review-changes`
Analyze recent commits and flag potential issues before opening a PR.

**Features:**
- Reviews last 15 commits
- Provides diff summary
- Suggests verification steps

## Usage

Once configured, these agents and commands are available globally in OpenCode:

```bash
# Start development work (recommended first step)
/start-work

# Quick security scan
/security-scan

# Comprehensive project analysis
/analyze-project

# Testing Skills (Implementing your testing article)
!skill testing-adversarial "validatePaymentAmount function --security --performance"
!skill testing-coverage "--file src/service.ts --lines 45-52,78-84"
!skill testing-mocks "UserRepository, EmailService --include-mockr"
!skill testing-integration "user authentication flow --include-mockr"
!skill testing-tdd "rate limiter for API endpoints"

# Enhanced file review with multi-agent analysis
!skill review-file-enhanced "src/auth/login.ts"

# Security-focused review with threat modeling
!skill review-security "src/api/users.go --focus authorization"

# Review preparation with automated checklists
!skill review-preparation "current branch --comprehensive"

# Review a specific file
/check-file src/components/UserAuth.tsx

# Generate PR description
/pr-summary

# Review recent changes
/review-changes
```

## Workflow Examples

### Starting New Work
```bash
# 1. Begin development with branch management
/start-work
# → Detects you're on main, suggests: feature/20260322-user-auth

# 2. Continue with development
# OpenCode will automatically use the new branch for all work

# 3. When ready, create PR
/pr-summary
```

### Working on Current Branch
```bash
# Skip branch creation when needed
/start-work
# → Choose "current" when prompted
# → Or work on existing feature branch
```

### Testing Workflow (Your Article Implementation)
```bash
# 1. Test-Driven Development - Start with tests
!skill testing-tdd "user authentication with JWT and role permissions"
# → Generates comprehensive test specification before implementation

# 2. Adversarial Testing - Find edge cases developers miss
!skill testing-adversarial "loginUser function --security --performance" 
# → Generates 20+ edge cases including injection attempts, race conditions

# 3. Coverage-Driven Testing - Target specific gaps
!skill testing-coverage "--file src/auth.ts --lines 67-89"
# → Generates tests for exact uncovered lines from coverage report

# 4. Mock Generation with Mockr Integration
!skill testing-mocks "AuthService, EmailService --include-mockr"
# → Generates Jest mocks AND mockr HTTP-level configurations

# 5. Complete Integration Testing
!skill testing-integration "authentication flow --include-mockr"
# → Full integration test setup with database and external service mocking
```

### Enhanced Review Workflow
```bash
# 1. Prepare comprehensive review
!skill review-preparation "feature/user-auth"
# → Generates review checklist and impact analysis

# 2. Security-focused analysis  
!skill review-security "src/auth/ --comprehensive"
# → Deep security vulnerability assessment

# 3. Multi-agent file review
!skill review-file-enhanced "src/auth/jwt.ts --all-agents" 
# → Security + Performance + Architecture analysis

# 4. Full project analysis
/analyze-project
# → Complete codebase documentation and improvement roadmap

# 5. Quick security scan
/security-scan
# → Rapid vulnerability detection
```

## Project Structure

```
├── agents/
│   └── review.md                   # Code review agent configuration
├── commands/
│   ├── check-file.md              # File review command
│   ├── pr-summary.md              # PR description generator
│   ├── review-changes.md          # Change analysis command
│   └── start-work.md              # Branch management command
├── prompts/
│   └── build-with-auto-branch.txt # Build agent prompt for branch automation
├── opencode.example.json          # Configuration template
├── package.json                   # Dependencies
└── README.md                      # This file
```

## Branch Management

This configuration includes automatic git branch management:

### How It Works
- **Build Agent**: Automatically checks branch status before development work
- **Smart Detection**: Identifies when you're on main/master and suggests branching
- **Opt-out Support**: Always provides options to continue on current branch
- **Consistent Naming**: Uses date-based naming for clear organization

### Branch Naming Convention
```bash
feature/YYYYMMDD-description    # New features and development
fix/YYYYMMDD-description        # Bug fixes
review/YYYYMMDD-description     # Code review work  
poc/YYYYMMDD-description        # Proof of concepts
docs/YYYYMMDD-description       # Documentation updates
refactor/YYYYMMDD-description   # Code restructuring
```

### Configuration
The automatic branching is configured through:
- Enhanced `opencode.json` with git branch permissions
- Custom build agent prompt in `prompts/build-with-auto-branch.txt`
- `/start-work` command for explicit branch management

## Requirements

- Node.js >= 16.0.0
- OpenCode AI
- Context7 API key (optional, for enhanced documentation)

## License

MIT