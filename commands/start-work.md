---
description: Start development work with automatic branch creation
agent: build
---

# 🚀 Start Development Work

## Current Git Status
**Current branch**: !`git branch --show-current`
**Working tree status**: !`git status --porcelain`

## Branch Analysis

!`
CURRENT_BRANCH=$(git branch --show-current)
MAIN_BRANCHES="main master develop"

if echo "$MAIN_BRANCHES" | grep -q "$CURRENT_BRANCH"; then
    echo "📍 You're on the main branch: $CURRENT_BRANCH"
    echo "✨ RECOMMENDED: Create a new feature branch"
    echo "⚠️  OPTION: Continue on current branch (not recommended)"
elif [ -n "$(git status --porcelain)" ]; then
    echo "📍 You're on feature branch: $CURRENT_BRANCH"
    echo "⚠️  Warning: You have uncommitted changes"
    echo "💾 RECOMMENDED: Stash or commit changes before branching"
else
    echo "📍 You're on feature branch: $CURRENT_BRANCH"
    echo "🔄 CONTINUE: Keep working on current branch"
    echo "🆕 OPTION: Create new branch for different work"
fi
`

## What are you working on?

Please describe your work to generate an appropriate branch name:

**Branch Type Examples:**
- **"user authentication"** → `feature/$(date +%Y%m%d)-user-authentication`
- **"fix payment validation bug"** → `fix/$(date +%Y%m%d)-payment-validation`  
- **"review security issues"** → `review/$(date +%Y%m%d)-security-issues`
- **"POC analytics dashboard"** → `poc/$(date +%Y%m%d)-analytics-dashboard`
- **"update API docs"** → `docs/$(date +%Y%m%d)-api-docs`
- **"refactor auth module"** → `refactor/$(date +%Y%m%d)-auth-module`

## Quick Options

Type one of these for immediate action:
- **"current"** - Continue on current branch
- **"main"** - Work directly on main (⚠️ not recommended)
- **"stash"** - Stash changes and create new branch
- **"commit"** - Commit current work and create new branch

## Generated Branch Command

Once you tell me what you're working on, I'll generate and execute:

```bash
# Example for "user authentication":
git checkout -b feature/$(date +%Y%m%d)-user-authentication
```

**Ready to start! What are you working on?**