---
description: Generate a PR description from the current branch diff
agent: plan
subtask: true
---

Branch: !`git branch --show-current`

Commits:
!`git log --oneline main...HEAD`

Diff summary:
!`git diff main...HEAD --stat`

Write a pull request description with:
- A one-sentence summary of what this PR does
- A bullet list of the main changes
- Any breaking changes or migration steps required
- Testing notes

Use plain markdown, no HTML.