---
description: Stage all git changes in the repository
---

Stages all changes (modified, new, deleted files) in the repository.

## Arguments

$ARGUMENTS — No arguments needed

## Steps

1. **Stage all changes**
   - Run !`git add .`
   - Display output if any

2. **Show staged status**
   - Run !`git status --short`
   - Suggest next action (e.g., "Ready to commit. Use `/commit` to create a commit.")

3. **Error handling**
   - Git unavailable: Run !`which git`, suggest installation
   - Not in git repo: Run !`git rev-parse --git-dir`, suggest running from repo

## Example

- User: `/git-stage-all`
- Command runs: !`git add .`
- Result: Shows staged files and suggests using `/commit`