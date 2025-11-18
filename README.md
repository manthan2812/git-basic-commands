# 🚀 Git Basic Commands - Advanced Guide

A comprehensive guide to essential Git commands for developers. This repository serves as a quick reference for Git workflows, from basic operations to advanced techniques used in professional development.

> **Last Updated:** November 2025 | **Perfect for:** Beginners to Advanced Developers

## 📚 Table of Contents

- [Quick Start Tips](#-quick-start-tips)
- [Configuration](#-configuration)
- [Basic Commands](#-basic-commands)
- [Branching](#-branching)
- [Comparing Changes](#-comparing-changes)
- [Stashing](#-stashing)
- [Undoing Changes](#️-undoing-changes)
- [Remote Repository](#-remote-repository)
- [Remote Branches](#-remote-branches)
- [Fetching & Pulling](#️-fetching--pulling)
- [Rebasing](#-rebasing)
- [Cherry Pick](#-cherry-pick)
- [Tags](#️-tags)
- [Searching & Inspection](#-searching--inspection)
- [Hooks](#-hooks)
- [Cleaning](#-cleaning)
- [Advanced Techniques](#️-advanced-techniques)
- [Pro Tips & Best Practices](#-pro-tips--best-practices)
- [Security Tips](#-security-tips)
- [Resources](#-resources)
- [Quick Reference](#️-quick-reference)
- [Commit Message Convention](#-commit-message-convention)
- [Contributing](#-contributing)

---

## 📖 Quick Start Tips

**Before you begin:**

- Use `git status` frequently to understand your repository state
- Write meaningful commit messages
- Pull before you push
- Create feature branches for new work
- Review changes before committing (`git diff`)

---

## 🔧 Configuration

**Local vs Global Configuration:**

- `git config` - Sets config for current repository only
- `git config --global` - Sets config for all repositories on your machine
- `git config --system` - Sets config for all users on your machine

### Retrieve Git Username

```bash
git config user.name
```

### Set Git Username

```bash
git config --global user.name "Manthan Patel"
```

### Retrieve Git User Email

```bash
git config user.email
```

### Set Git User Email

```bash
git config --global user.email "manthan@gmail.com"
```

### Using Visual Studio Code as Editor

```bash
git config --global core.editor "code --wait"
```

### View All Configuration Settings

```bash
git config --list              # Show all settings
git config --global --list     # Show global settings
git config --local --list      # Show local repository settings
```

### Unset Configuration

```bash
git config --global --unset user.name
```

### Set Default Branch Name

```bash
git config --global init.defaultBranch main
```

---

## 📝 Basic Commands

### Initialize Repository

```bash
git init
```

### Track Changes

```bash
git status
```

### Moving Changes from Working Directory to Staging Area

```bash
git add file1 file2
```

### Moving All Changes from Working Directory to Staging Area

```bash
git add .
```

### Interactive Staging (Stage Changes Interactively)

```bash
git add -p
# or
git add --patch
# Allows you to review and choose which changes to stage
```

### Unstage All Files

```bash
git reset
# or
git restore --staged .
```

### Commit Changes

```bash
git commit -m "Commit Message"
```

### Commit All Changes Directly (Without git add)

```bash
git commit -a -m "Commit Message"
# or
git commit -am "Commit Message"
```

### Redo Last Commit

```bash
git commit --amend
# Opens editor to change commit message and add/remove files

# Amend without changing commit message
git commit --amend --no-edit
```

### Commit History

```bash
git log
```

### Commit History in One Line

```bash
git log --oneline
```

### Exit Vim Editor

```bash
:wq
```

---

## 🌳 Branching

### List All Branches

```bash
git branch
```

### List All Branches with Last Commit Details

```bash
git branch -v
```

### Create New Branch

```bash
git branch <branch-name>
```

### Change Branch

```bash
git switch <branch-name>
# or
git checkout <branch-name>
```

### Create New Branch and Switch to It

```bash
git switch -c <branch-name>
# or
git checkout -b <branch-name>
```

### Delete Branch

_Note: First switch to a different branch_

```bash
git branch -D <branch-name>
# -D forces deletion (even if not merged)

# Safe delete (only if merged)
git branch -d <branch-name>
```

### Delete Remote Branch

```bash
git push origin --delete <branch-name>
# or
git push origin -d <branch-name>
```

### Rename Branch

_Note: First switch to the branch you want to rename_

```bash
git branch -m <new-name>
```

### Merge a Branch

_Note: Switch to the destination branch first (e.g., master), then merge the source branch_

```bash
git switch master
git merge bugfix
```

### Abort Merge

```bash
git merge --abort
```

### View Merge Conflicts

```bash
git status          # Shows files with conflicts
git diff            # Shows all conflicts
```

### List Merged/Unmerged Branches

```bash
git branch --merged      # Branches already merged into current branch
git branch --no-merged   # Branches not yet merged
```

---

## 🔍 Comparing Changes

### Compare Unstaged Changes

Compares Staging Area and Working Directory

```bash
git diff
```

### Compare Staged & Unstaged Changes

Compares Working Directory and Last Commit

```bash
git diff HEAD
```

### Compare Staged Changes

Compares Staging Area and Last Commit

```bash
git diff --staged
# or
git diff --cached
```

### Compare Specific File

```bash
git diff <file-name>
# or
git diff HEAD <file-name>
```

### Compare Multiple Files

```bash
git diff <file1> <file2> <file3>
# or
git diff HEAD <file1> <file2> <file3>
```

### Compare Branches

```bash
git diff <branch1>..<branch2>
# or
git diff <branch1> <branch2>
```

### Compare Commits

```bash
git diff <commit1>..<commit2>
# or
git diff <commit1> <commit2>
```

### View Changes in Pretty Format

```bash
git show --stat <commit-hash>   # Show which files changed
git diff --color-words          # Show word-level differences with colors
git diff --word-diff            # Alternative word diff
```

---

## 📦 Stashing

### Stash All Changes (Staged and Unstaged)

```bash
git stash
# or
git stash save
```

### Remove Most Recently Stashed Changes and Reapply

```bash
git stash pop
```

### Apply Stashed Changes Without Removing from Stash

```bash
git stash apply
```

### View All Stashes

```bash
git stash list
```

### Apply Specific Stash

```bash
git stash apply stash@{2}
```

### Delete Particular Stash

```bash
git stash drop stash@{2}
```

### Clear All Stashes

```bash
git stash clear
```

---

## ↩️ Undoing Changes

### Go to Particular Commit

```bash
git checkout <commit-hash>
# Example:
git checkout d824w94
```

### Go to Previous Commits

```bash
git checkout HEAD~1  # 1st previous commit
git checkout HEAD~2  # 2nd previous commit
git checkout HEAD~3  # 3rd previous commit
git checkout HEAD~4  # 4th previous commit
```

### Discard Changes on Specific Files (Recommended)

```bash
git restore <file-name>
git restore <file1> <file2> <file3>
# Modern approach (Git 2.23+)
```

### Discard Changes on Specific Files (Legacy)

```bash
git checkout HEAD <file-name>
# or
git checkout -- <file-name>
```

### Unmodify Changes on Specific Files to Specific Commit

```bash
git restore --source HEAD~1 <file-name>
git restore --source HEAD~1 <file1> <file2> <file3>
```

### Unstage File

```bash
git restore --staged <file-name>
```

### Reset Commits (Soft Reset - Keep All Changes)

Keeps changes in working directory and staging area

```bash
git reset --soft <commit-hash>
```

### Reset Commits (Mixed Reset - Keep Changes in Working Directory)

Keeps changes in working directory, clears staging area (default)

```bash
git reset <commit-hash>
# or
git reset --mixed <commit-hash>
# Example:
git reset d824w94
```

### Reset Commits (Hard Reset - Remove All Changes)

⚠️ **Warning:** This permanently deletes changes

```bash
git reset --hard <commit-hash>
# Example:
git reset --hard d824w94
```

### Revert Commit

Creates a new commit that undoes the specified commit

```bash
git revert <commit-hash>
# Example:
git revert d824w94
```

---

## 🌐 Remote Repository

### Clone Remote Repository to Local Directory

```bash
git clone <url>
```

### View Remote

```bash
git remote
# or with details
git remote -v
```

### Add a New Remote

```bash
git remote add <name> <url>
# Example:
git remote add origin https://github.com/test/test-repo.git
```

### Rename Remote

```bash
git remote rename <old-name> <new-name>
```

### Remove Remote

```bash
git remote remove <name>
```

### Push Local Code Changes to Remote Branch

```bash
git push <remote> <branch>
# Example:
git push origin master
```

### Push Local Branch to Different Remote Branch

```bash
git push <remote> <local-branch>:<remote-branch>
# Example:
git push origin dev:master
```

### Set Upstream of the Branch

```bash
git push -u origin <branch-name>
# Example:
git push -u origin master
```

### Push All Branches

```bash
git push --all
```

### Force Push (Use with Caution!)

```bash
# Safe force push (recommended)
git push --force-with-lease

# Dangerous force push (use only if you know what you're doing)
git push --force
```

### Delete Remote Branch

```bash
git push <remote> --delete <branch-name>
# or
git push <remote> -d <branch-name>
```

---

## 🔀 Remote Branches

### View Remote Branches

```bash
git branch -r
```

### Change Remote Branch in Local Workspace

```bash
git switch <remote-branch-name>
# Example:
git switch bugfix
# or
git checkout --track <remote>/<remote-branch-name>
# Example:
git checkout --track origin/bugfix
```

---

## ⬇️ Fetching & Pulling

### Fetch Changes from Remote

_If not specified, defaults to origin_

```bash
git fetch <remote>
# Example:
git fetch origin
```

### Fetch Particular Remote Branch

```bash
git fetch <remote> <branch>
# Example:
git fetch origin master
```

### Pull Remote Changes

_If not specified, defaults to origin and the tracking connection configured for your current branch_

```bash
git pull <remote> <branch>
# Example:
git pull origin master
```

### Pull with Rebase Instead of Merge

```bash
git pull --rebase
# Fetches changes and rebases your commits on top
```

### Set Pull Strategy Globally

```bash
git config --global pull.rebase true
```

---

## 🔄 Rebasing

### Rebase Branch

Re-applies commits from one branch on top of another (rewrites history)

```bash
git switch bugfix
git rebase master
# Moves bugfix commits to start from tip of master
```

### Continue Rebase After Fixing Conflicts

```bash
git rebase --continue
```

### Abort Rebase When Conflicts Occur

```bash
git rebase --abort
```

### Interactive Rebase

_HEAD~5 means you are trying to edit the last five commits_

```bash
git rebase -i HEAD~5
```

**Interactive Rebase Commands:**

```
p, pick <commit>     = use commit
r, reword <commit>   = use commit, but edit the commit message
e, edit <commit>     = use commit, but stop for amending
s, squash <commit>   = use commit, but meld into previous commit
f, fixup <commit>    = like "squash", but discard this commit's log message
d, drop <commit>     = remove commit
```

---

## 🎯 Cherry Pick

Cherry-picking allows you to apply specific commits from one branch to another.

### Cherry Pick a Specific Commit

```bash
git cherry-pick <commit-hash>
# Example:
git cherry-pick a1b2c3d
```

### Cherry Pick Multiple Commits

```bash
git cherry-pick <commit1> <commit2> <commit3>
# Example:
git cherry-pick a1b2c3d e5f6g7h i9j0k1l
```

### Cherry Pick a Range of Commits

```bash
git cherry-pick <start-commit>..<end-commit>
# Example:
git cherry-pick a1b2c3d..e5f6g7h
```

### Continue Cherry Pick After Resolving Conflicts

```bash
git cherry-pick --continue
```

### Abort Cherry Pick

```bash
git cherry-pick --abort
```

---

## 🏷️ Tags

### View Tags

```bash
git tag
```

### View Tags by Particular Pattern

```bash
git tag -l "*beta*"
# This lists all tags containing "beta" in their name
```

### Check Out Tag

```bash
git checkout <tag-name>
```

### Compare Tags

```bash
git diff <tag1> <tag2>
```

### Create Lightweight Tag

```bash
git tag <tag-name>
```

### Create Annotated Tag

```bash
git tag -a <tag-name>
```

### View Tag Information

```bash
git show <tag-name>
```

### Create Tag of Previous Commit

```bash
git tag <tag-name> <commit-hash>
# or
git tag -a <tag-name> <commit-hash>
```

### Replace/Reuse Tag with Force

```bash
git tag -f <tag-name>
# Forcefully change existing tag
```

### Delete Tag

```bash
git tag -d <tag-name>
```

### Push Single Tag

```bash
git push <remote> <tag-name>
```

### Push All Tags

```bash
git push <remote> --tags
```

---

## 🔍 Searching & Inspection

### Search for Text in Commits

```bash
git log -S "<text>"
# Example:
git log -S "TODO"
```

### Search Commit Messages

```bash
git log --grep="<pattern>"
# Example:
git log --grep="bug fix"
```

### Search by Author

```bash
git log --author="<author-name>"
# Example:
git log --author="Manthan"
```

### Search by Date

```bash
git log --since="2 weeks ago"
git log --until="2023-12-31"
git log --after="2023-01-01" --before="2023-12-31"
```

### Show Commits that Modified a Specific File

```bash
git log <file-name>
# Example:
git log src/index.js
```

### Show Who Changed Each Line (Blame)

```bash
git blame <file-name>
# Example:
git blame src/index.js
```

### Show Specific Commit Details

```bash
git show <commit-hash>
# Example:
git show a1b2c3d
```

### Show File at Specific Commit

```bash
git show <commit-hash>:<file-path>
# Example:
git show a1b2c3d:src/index.js
```

### List Commits Not Yet Merged

```bash
git log --oneline <branch>..<other-branch>
# Example:
git log --oneline develop..main
```

---

## 🪝 Hooks

Git hooks are scripts that run automatically on certain Git events. They live in `.git/hooks/` directory.

### Common Git Hooks

| Hook          | When it runs                        | Use case                |
| ------------- | ----------------------------------- | ----------------------- |
| pre-commit    | Before commit                       | Lint, format, test      |
| pre-push      | Before push                         | Run tests, checks       |
| commit-msg    | When commit message is being edited | Validate message format |
| post-checkout | After branch switch                 | Install dependencies    |
| pre-rebase    | Before rebase                       | Validate branch state   |

### Pre-commit Hook Example

Runs linting before commit

```bash
#!/bin/bash
# .git/hooks/pre-commit
echo "Running linter..."
npm run lint
if [ $? -ne 0 ]; then
  echo "Linting failed. Commit aborted."
  exit 1
fi
```

### Pre-push Hook Example

Runs tests before push

```bash
#!/bin/bash
# .git/hooks/pre-push
echo "Running tests..."
npm run test
if [ $? -ne 0 ]; then
  echo "Tests failed. Push aborted."
  exit 1
fi
```

### Commit Message Hook Example

Ensures meaningful commit messages

```bash
#!/bin/bash
# .git/hooks/commit-msg
MESSAGE=$(cat "$1")
if [[ ! $MESSAGE =~ ^(feat|fix|docs|style|refactor|test|chore): ]]; then
  echo "Commit message must start with: feat, fix, docs, style, refactor, test, or chore"
  exit 1
fi
```

### Make Hook Executable

```bash
chmod +x .git/hooks/pre-commit
```

### Temporarily Skip Hooks

```bash
git commit --no-verify      # Skip pre-commit hook
git push --no-verify        # Skip pre-push hook
```

### Using Husky (Node.js Projects)

Manage Git hooks easily with Husky

```bash
npm install husky --save-dev
npx husky install
npx husky add .husky/pre-commit "npm run lint"
npx husky add .husky/pre-push "npm run test"
```

---

## 🧹 Cleaning

### List Untracked Files

```bash
git clean -n
# -n flag shows what would be deleted without actually deleting
```

### Delete Untracked Files

```bash
git clean -f
```

### Delete Untracked Files and Directories

```bash
git clean -fd
```

### Delete Untracked Files, Directories, and Ignored Files

```bash
git clean -fdx
```

### Remove Empty Directories

```bash
git clean -d
```

### Garbage Collection & Optimization

```bash
git gc
```

### Prune Unreachable Objects

```bash
git prune
```

---

## ⚙️ Advanced Techniques

### 1. **Squashing Commits**

Combine multiple commits into one before pushing

```bash
# Interactive rebase to squash last 3 commits
git rebase -i HEAD~3
# Change 'pick' to 'squash' (or 's') for commits you want to squash
```

### 2. **Fixing Commits in the Past**

```bash
# Amend a specific commit from history
git rebase -i HEAD~5
# Mark the commit with 'edit'
# Make your changes
git add .
git commit --amend --no-edit
git rebase --continue
```

### 3. **Undoing a Pushed Commit**

```bash
# For public branches, use revert (safe)
git revert <commit-hash>

# For private branches, use reset (not safe for public)
git reset --hard <commit-hash>
git push --force-with-lease
```

### 4. **Moving Commits Between Branches**

```bash
# Create new branch from current point
git branch new-feature

# Reset current branch to old state
git reset --hard <old-commit>

# Switch to new branch with your commits
git switch new-feature
```

### 5. **Bisecting to Find Problematic Commit**

```bash
git bisect start
git bisect bad HEAD        # current commit has the bug
git bisect good <commit>   # this commit was ok
# Git will checkout commits in between for you to test
git bisect reset          # exit bisect mode
```

### 6. **Creating a Worktree**

Work on multiple branches simultaneously

```bash
git worktree list
git worktree add <path> <branch>
# Example:
git worktree add ../bugfix bugfix-branch

# Remove worktree
git worktree remove <path>
```

### 7. **Using Git Attributes**

Control how files are treated in `.gitattributes`

```
# .gitattributes example
*.js text eol=lf
*.md text
*.zip binary
```

### 8. **Shallow Clone**

Clone only recent history (faster for large repos)

```bash
git clone --depth 1 <url>
# --depth N means clone only last N commits

# Fetch full history later
git fetch --unshallow
```

### 9. **Submodules**

Include other repositories in your project

```bash
# Add submodule
git submodule add <url> <path>

# Clone with submodules
git clone --recurse-submodules <url>

# Update submodules
git submodule update --recursive
```

### 10. **Sparse Checkout**

Clone only specific directories

```bash
git clone --sparse <url>
git sparse-checkout init --cone
git sparse-checkout set <directory>
```

### 11. **Using Git Aliases for Productivity**

```bash
# Setup useful aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'restore --staged'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --graph --oneline --all'
git config --global alias.amend 'commit --amend --no-edit'
```

### 12. **Advanced Logging**

```bash
# Show commits in graph format
git log --graph --oneline --all --decorate

# Show commits with statistics
git log --stat

# Show detailed changes
git log -p

# Show commits by date
git log --date=short --format="%h %ad %s"

# Show commits in reverse order
git log --reverse
```

### 13. **Finding Changes with Pickaxe**

```bash
# Find commits that added or removed specific text
git log -S "searchText" -p

# Find commits where specific function was added/removed
git log -S "functionName()" --follow -- <file>
```

### 14. **Conditional Configuration**

Apply different configs for different directories

```bash
# In .gitconfig
[includeIf "gitdir:~/work/"]
    path = .gitconfig-work

[includeIf "gitdir:~/personal/"]
    path = .gitconfig-personal
```

### 15. **Using .gitignore Effectively**

```bash
# .gitignore patterns
node_modules/          # Ignore directories
*.log                  # Ignore file types
!important.log         # Negation - don't ignore this
/root-file.txt        # Ignore at root only
**/deep-file.txt      # Ignore at any depth
```

### 16. **Stash with Message**

```bash
git stash push -m "work on feature X"
```

### 17. **View Stash Diff**

```bash
git stash show -p stash@{0}
```

### 18. **Create Branch from Stash**

```bash
git stash branch <branch-name> stash@{0}
```

### 19. **Merge Strategies**

```bash
# Resolve merge conflicts using specific strategy
git merge -s recursive <branch>      # default
git merge -s resolve <branch>
git merge -s octopus <branch>        # merge multiple branches
git merge -s ours <branch>           # keep our version
git merge -s subtree <branch>
```

### 20. **Reflog Advanced Usage**

Recovery deleted commits

```bash
git reflog                    # see all operations
git reflog show <branch>
git checkout <reflog-entry>  # recover deleted work
```

---

## 💡 Pro Tips & Best Practices

| Tip                                     | Description                                     |
| --------------------------------------- | ----------------------------------------------- |
| **Use branches**                        | Create a new branch for each feature/bug        |
| **Commit often**                        | Make small, logical commits                     |
| **Write good messages**                 | Start with verb (Add, Fix, Update, Remove)      |
| **Pull before push**                    | Avoid merge conflicts by updating first         |
| **Use .gitignore**                      | Never commit sensitive files (keys, passwords)  |
| **Review before commit**                | Use `git diff` to check changes                 |
| **Rebase for clean history**            | Keep history linear when possible               |
| **Don't force push to shared branches** | Use `--force-with-lease` if you must            |
| **Tag releases**                        | Mark important versions with tags               |
| **Use meaningful branch names**         | e.g., `feature/user-auth`, `bugfix/login-issue` |

---

## 🔐 Security Tips

```bash
# Sign commits with GPG
git config --global user.signingKey <key-id>
git commit -S -m "Signed commit"

# Verify signed commits
git log --show-signature

# Check for exposed secrets
git log -p | grep -i "password\|secret\|token"
```

---

## 📚 Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book (Free)](https://git-scm.com/book/en/v2)
- [GitHub Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)

---

## ⚡ Quick Reference

### Most Used Commands

```bash
echo "Daily Workflow:"
git status                          # Check status
git add .                          # Stage changes
git commit -m "message"            # Commit
git push origin branch-name        # Push to remote
git pull origin branch-name        # Pull from remote
git log --oneline                  # View history
```

### Emergency Commands

```bash
echo "When things go wrong:"
git reflog                         # See all operations
git reset --hard <commit>         # Nuclear option (be careful!)
git cherry-pick <commit>          # Copy a specific commit
git bisect start                   # Find problematic commit
```

---

## 📝 Commit Message Convention

**Format:** `<type>(<scope>): <subject>`

**Types:**

- `feat` - A new feature
- `fix` - A bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, missing semicolons, etc.)
- `refactor` - Code refactoring without feature changes
- `test` - Adding or updating tests
- `chore` - Dependency updates, tooling changes
- `perf` - Performance improvements

**Examples:**

```
feat(auth): add JWT authentication
fix(login): resolve email validation bug
docs: update installation instructions
chore(deps): upgrade Node.js to v18
```

---

## 🤝 Contributing

Find an issue? Want to add more commands? Feel free to:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-commands`
3. Make your changes
4. Commit: `git commit -m "feat: add new git commands"`
5. Push: `git push origin feature/new-commands`
6. Submit a Pull Request

---

## 📄 License

This project is open source and available under the MIT License.
