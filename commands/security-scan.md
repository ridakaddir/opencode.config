---
description: Quick security vulnerability scan with immediate feedback
agent: security
---

# 🛡️ Security Scan

## Quick Security Assessment

**Target**: @$ARGUMENTS

## Current Branch Check
!`git branch --show-current`

**If on main/master**: ⚠️ Consider creating a review branch: `/start-work`

## Scanning for Security Issues...

### 1. Secrets and Credentials Check
!`grep -r -i "password\|secret\|key\|token" --include="*.js" --include="*.ts" --include="*.go" --include="*.json" --include="*.env*" . | grep -v node_modules | head -10`

### 2. Common Vulnerability Patterns
!`grep -r "eval\|innerHTML\|dangerouslySetInnerHTML" --include="*.js" --include="*.ts" --include="*.jsx" --include="*.tsx" . | grep -v node_modules | head -5`

### 3. SQL Injection Indicators  
!`grep -r "SELECT.*+\|WHERE.*+" --include="*.js" --include="*.ts" --include="*.go" . | grep -v node_modules | head -5`

### 4. Package Security Audit
!`if [ -f package.json ]; then npm audit --audit-level=high 2>/dev/null | head -20 || echo "npm audit not available"; fi`

### 5. Environment File Check
!`find . -name ".env*" -not -path "./node_modules/*" | head -5`

## Quick Security Analysis

**🔍 Analysis Focus:**
- Hardcoded secrets and credentials
- XSS vulnerabilities (eval, innerHTML usage)
- SQL injection patterns
- Insecure dependencies
- Environment configuration exposure

**🚨 If Issues Found:**
Run comprehensive analysis: Use security agent for detailed review

**✅ For Clean Scan:**
Consider periodic security reviews with `/check-file` for specific components

## Next Steps

### For Detailed Analysis
```bash
# Run comprehensive security review
# (Uses security agent for deep analysis)
```

### For Specific File Review
```bash
/check-file path/to/security-critical-file.ts
```

### For Full Project Security Audit
```bash
# Run full codebase analysis with security focus
# (Uses codebase-analyzer agent)
```

---

**⚠️ Note**: This is a quick scan. For production systems, run comprehensive security analysis with security agent.