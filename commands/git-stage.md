---
description: Stage git changes for files modified in the current conversation thread
---

Stages file modifications identified from the conversation thread for commit using git.

## Arguments

$ARGUMENTS — Optional flags:
- `--preview` — Show diff before staging (default: stage immediately)
- `--dry-run` — List files that would be staged without staging them

## Steps

1. **Identify modified files from thread**
   - Review conversation history for file operations (write, edit, create)
   - Extract unique file paths and categorize as: created, modified, or deleted

2. **Validate files exist**
   - Skip files that no longer exist or were hypothetical

3. **Handle flags**
   - `--dry-run`: List files with status (e.g., "Would stage: src/file.ts (modified)") and exit
   - `--preview`: Show diff for modified files, ask user to confirm before staging

4. **Stage files**
   - Run !`git add <file>` for each valid file
   - Display summary with count and status breakdown

5. **Show staged status**
   - Run !`git status --short`
   - Suggest next action (e.g., "Ready to commit. Use `/commit` to create a commit.")

6. **Error handling**
   - No modifications: Inform user and exit
   - Git unavailable: Run !`which git`, suggest installation
   - Not in git repo: Run !`git rev-parse --git-dir`, suggest running from repo

## Examples

### Stage all thread changes
- User: `/git-stage`
- Command finds 3 modified files
- Runs: !`git add src/file1.ts src/file2.ts src/new-file.ts`
- Result: "Staged 3 files (2 modified, 1 new). Ready to commit."

### Preview before staging
- User: `/git-stage --preview`
- Command shows diffs for each file
- User confirms or cancels

### Dry run
- User: `/git-stage --dry-run`
- Result:
  ```
  Would stage: src/components/Button.tsx (modified)
  Would stage: src/pages/new-page.tsx (new)
  ```