---
description: Comprehensive environment verification to prevent misinformation about installed software
agent: environment-validator
---

# 🔍 Environment Verification

## Current Environment Audit

**Purpose**: Verify actual installed software and available versions to prevent misinformation.

## System Information
**Operating System**: !`uname -a`
**Architecture**: !`uname -m`

## Programming Languages

### Go Language
**Installed Version**: !`go version 2>/dev/null || echo "Go not installed"`
**Go Module State**: !`if [ -f "go.mod" ]; then go mod tidy && echo "Go modules verified"; else echo "No go.mod found"; fi`

### Node.js & NPM  
**Node.js Version**: !`node --version 2>/dev/null || echo "Node.js not installed"`
**NPM Version**: !`npm --version 2>/dev/null || echo "NPM not installed"`

### Python
**Python Version**: !`python --version 2>/dev/null || python3 --version 2>/dev/null || echo "Python not installed"`

## Development Tools

### Version Control
**Git Version**: !`git --version 2>/dev/null || echo "Git not installed"`

### Containerization  
**Docker Version**: !`docker --version 2>/dev/null || echo "Docker not installed"`

### Build Tools
**Available Tools**: !`which make gcc clang 2>/dev/null || echo "Standard build tools not found"`

## Project-Specific Analysis

### Current Project Dependencies
**Package Managers Found**: !`ls -la | grep -E "(package\.json|go\.mod|requirements\.txt|Cargo\.toml|composer\.json)" || echo "No common package manager files found"`

### Go Project Analysis (if applicable)
!`if [ -f "go.mod" ]; then echo "=== Go Module Info ==="; cat go.mod | head -10; echo ""; echo "=== Go Dependencies ==="; go list -m all | head -10; else echo "Not a Go project"; fi`

### Node.js Project Analysis (if applicable)
!`if [ -f "package.json" ]; then echo "=== Package.json Info ==="; cat package.json | head -15; echo ""; echo "=== Installed Packages ==="; npm list --depth=0 2>/dev/null | head -10; else echo "Not a Node.js project"; fi`

## External Connectivity Check

### Internet Connection
**Connectivity Test**: !`curl -s --connect-timeout 5 https://google.com > /dev/null && echo "Internet connection available" || echo "No internet connection or restricted"`

### Official Sources Accessibility  
**Go Downloads**: !`curl -s --connect-timeout 5 https://go.dev/dl/ > /dev/null && echo "Go official site accessible" || echo "Cannot reach go.dev"`
**NPM Registry**: !`curl -s --connect-timeout 5 https://registry.npmjs.org > /dev/null && echo "NPM registry accessible" || echo "Cannot reach NPM registry"`

## Validation Summary

### ✅ Facts Verified
- Actual installed software versions (no assumptions)
- Real system capabilities and architecture
- Project-specific dependency states
- External connectivity for updates/verification

### ❌ Prevented Errors
- Outdated version availability claims
- Incorrect system requirement assumptions  
- Wrong compatibility assertions
- Unsupported recommendation suggestions

## Usage for Other Agents

**Before making ANY factual claims**, other agents should reference this environment audit to ensure:
- Version recommendations are based on actual installed versions
- Compatibility claims are verified against real system state
- Availability assertions are checked against accessible sources
- Requirements are validated against current environment

---

**🛡️ This verification prevents misinformation by establishing ground truth about the actual development environment.**