---
description: Review recent git changes and summarise what was done
agent: plan
---

Here are the recent commits on this branch:
!`git log --oneline -15`

And the full diff:
!`git diff main...HEAD --stat`

Summarise what changed, flag anything that looks incomplete or risky,
and suggest anything I should verify before opening a PR.