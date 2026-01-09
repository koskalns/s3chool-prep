# Git Essentials Guide

## What is Git?
Git is a version control system that tracks changes to files over time. It allows you to:
- Save snapshots of your code (commits)
- Track who made changes and when
- Collaborate with others
- Revert to previous versions if needed
- Work on different features simultaneously (branches)

---

## Key Concepts

### Repository
A repository (repo) is a folder that Git tracks. It contains all your files and the complete history of changes.

### Commit
A commit is a snapshot of your code at a specific point in time. Each commit has:
- A unique ID (hash)
- A message describing the changes
- Author information
- Timestamp

### Branch
A branch is a separate line of development. The default branch is `main` (or `master` in older repos).

### Remote
A remote is a copy of the repository on a server (e.g., GitHub, GitLab). `origin` is typically the remote on GitHub.

---

## Basic Workflow

```
1. Make changes to files
2. Stage changes (git add)
3. Commit changes (git commit)
4. Push to remote (git push)
```

---

## Essential Git Commands

### Setup (First Time)
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list                    # Verify your settings
```

### Create and Clone Repositories
```bash
git init                             # Create a new repository in current folder
git clone https://github.com/user/repo.git    # Copy a remote repository
```

### Check Status
```bash
git status                           # Show which files changed
git diff                             # Show detailed changes (additions/deletions)
git log                              # Show commit history
git log --oneline                    # Show commit history in compact format
```

### Staging and Committing
```bash
git add filename.py                  # Stage a specific file
git add .                            # Stage ALL changed files
git commit -m "Clear message about changes"   # Create a commit
git commit -am "Message"             # Stage and commit tracked files (not new files)
```

### Viewing Changes
```bash
git show commit_id                   # Show what changed in a specific commit
git blame filename.py                # Show who changed each line
git diff HEAD~1                      # Compare current changes with previous commit
```

### Branches
```bash
git branch                           # List local branches
git branch -a                        # List all branches (local and remote)
git branch feature_name              # Create a new branch
git checkout feature_name            # Switch to a branch
git checkout -b feature_name         # Create and switch to new branch
git switch feature_name              # Alternative to checkout (newer Git versions)
git merge feature_name               # Merge feature_name into current branch
git branch -d feature_name           # Delete a branch
```

### Working with Remotes
```bash
git remote -v                        # Show remote repositories
git remote add origin https://github.com/user/repo.git   # Add a remote
git push                             # Push commits to remote
git push origin branch_name          # Push specific branch
git pull                             # Fetch and merge remote changes
git fetch                            # Download remote changes (without merging)
```

### Undoing Changes
```bash
git restore filename.py              # Discard changes to a file
git reset HEAD filename.py           # Unstage a file
git revert commit_id                 # Create new commit undoing changes
git log --oneline | head -5          # See recent commits to revert
```

---

## Common Workflows

### Initialize a local project and push to GitHub

```bash
cd my_project
git init
git add .
git commit -m "Initial commit"
git branch -M main                   # Rename to main (if needed)
git remote add origin https://github.com/user/repo.git
git push -u origin main
```

### Working on a feature branch

```bash
git checkout -b feature/new-feature
# ... make changes ...
git add .
git commit -m "Add new feature"
git push origin feature/new-feature
# Then create a Pull Request on GitHub
```

### Sync with remote

```bash
git fetch origin                     # Get latest from remote
git status                           # Check if you're behind
git pull origin main                 # Update local branch
```

### Undo recent commits

```bash
git log --oneline                    # See recent commits
git reset --soft HEAD~1              # Undo last commit, keep changes staged
git reset --mixed HEAD~1             # Undo last commit, keep changes unstaged
git reset --hard HEAD~1              # Undo last commit, discard all changes!
```

---

## Best Practices

### Commit Messages
- Start with a verb: "Add", "Fix", "Remove", "Update"
- Be specific: ✅ "Fix bug in login validation" vs ❌ "Fixed stuff"
- Keep first line under 50 characters
- Add details on new lines if needed

### Commit Frequency
- Commit related changes together
- Avoid giant commits with dozens of unrelated changes
- Aim for meaningful snapshots, not every keystroke

### Branching
- Use descriptive branch names: `feature/login`, `bugfix/navbar-spacing`
- Create a branch for each feature or fix
- Keep branches short-lived (days, not weeks)

### Before Pushing
- Review changes: `git diff`
- Test your code
- Check commit messages are clear

---

## Example: A Complete Session

```bash
# Clone a repository
git clone https://github.com/user/project.git
cd project

# Create a feature branch
git checkout -b feature/add-search

# Make changes to files
# ... edit search.py ...

# Check what changed
git status
git diff

# Stage and commit
git add search.py
git commit -m "Add search functionality to homepage"

# Push to remote
git push origin feature/add-search

# Create a Pull Request on GitHub for review

# After approval, merge to main
git checkout main
git pull origin main
git merge feature/add-search
git push origin main

# Clean up
git branch -d feature/add-search
git push origin --delete feature/add-search
```

---

## Useful Tools

- **GitHub Desktop**: GUI for Git operations
- **VS Code Git Integration**: Built-in Git commands and visualization
- **gitk**: Visual commit history viewer
- **GitHub CLI (`gh`)**: Command-line interface for GitHub

---

## Troubleshooting

### I committed to the wrong branch
```bash
git reset HEAD~1          # Undo the commit
git stash                 # Save changes temporarily
git checkout correct_branch
git stash pop             # Apply changes to correct branch
git commit -m "Message"
```

### I need to undo a push (use cautiously!)
```bash
git reset --hard HEAD~1
git push --force origin branch_name   # Forces the remote to match local
```

### Merge conflict
```bash
# 1. Open the conflicted file(s)
# 2. Look for <<<<<<, ======, >>>>>>
# 3. Manually edit to keep desired changes
# 4. Stage and commit the resolution
git add .
git commit -m "Resolve merge conflict"
```

