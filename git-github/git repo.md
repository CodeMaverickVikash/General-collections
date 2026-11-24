# Git & GitHub Complete Reference

## Git Architecture & Lifecycle
```text
Working Directory  ──(git add)──>  Staging Area  ──(git commit)──>  Git Repository
```

---

## 1. Initial Git Configuration (Run Once)
```bash
# Configure username and email
git config --global user.name "your_name"
git config --global user.email "your_email"
git config --global user.password "your_password"

# Verify global configuration
git config --global user.name
git config --global user.email
```

---

## 2. Basic Workflow Commands

```bash
# Initialize a new repository
git init

# Check current status
git status

# Stage all files
git add .

# Unstage a specific file
git restore --staged <file_name>

# Commit staged changes
git commit -m "initial commit"

# Check remotes
git remote -v

# Add remote origin (SSH or HTTPS)
git remote add origin git@github.com:username/repo.git

# Push code to remote
git push origin master

# Push with force (use with caution)
git push origin master --force

# Update existing remote URL
git remote set-url origin <new_url>

# Pull latest code from remote
git pull origin master

# View commit history
git log

# View compact graph log
git log --oneline --graph --decorate
```

---

## 3. Reviewing Changes
```bash
# View specific commit details
git show <commit_hash>

# Review unstaged changes in a file
git diff <file_name>

# Review staged changes
git diff --staged <file_name>
```

---

## 4. Branch Management

```bash
# List all branches
git branch

# Create a new branch
git branch <branch_name>

# Switch to an existing branch
git checkout <branch_name>

# Create and switch to a branch in one command
git checkout -b <branch_name>

# Merge branch into current branch
git checkout main
git merge <branch_name>

# Delete a local branch
git branch -d <branch_name>

# Push a new branch to remote and track it
git push --set-upstream origin <branch_name>

# Abort a merge in case of conflicts
git merge --abort
```

---

## 5. Stashing Changes
```bash
# Stash current uncommitted changes
git stash

# Apply the latest stash back to working directory
git stash pop
```

---

## 6. Undoing, Reverting & Resetting Changes

| Action | Command | Note |
| :--- | :--- | :--- |
| **Undo unstaged local changes** | `git checkout -- .` | Discards uncommitted edits |
| **Undo committed changes (safe)** | `git revert <commit_id>` | Creates a new reverse commit |
| **Revert without auto-commit** | `git revert -n <commit_id>` | Stages reverse changes |
| **Reset to a previous commit** | `git reset --hard <commit_id>` | Wipes working directory changes |
| **Remove commit but keep edits** | `git reset <commit_hash>` | Unstages commits, keeps files |

> [!WARNING]
> Force push (`git push --force`) is only safe if you are the sole contributor on that branch.

---

## 7. Fixing Author Info on the Last Commit
```bash
git commit --amend --author="Your Name <your@email.com>"
git push --force
```

---

## 8. Working with Forks & Upstream Repositories

```bash
# Check remote configuration
git remote -v

# Add upstream repository URL
git remote add upstream <forked_from_url>

# origin = your personal fork
# upstream = original repository
```

---

## 9. Cherry-Pick
```bash
# Apply a specific commit from another branch
git cherry-pick <commit_id>

# Stage changes from commit without auto-committing
git cherry-pick <commit_id> -n
```

---

## 10. Squash Merge Without Direct Commit
```bash
git merge --no-commit --squash <branch_name>
git reset HEAD # unstage changes if needed
```

---

## 11. Troubleshooting Common Errors

### "Please, commit your changes before merging"
```bash
git commit -m "Commit message / Ticket No"
```

### "There is no tracking information for the current branch"
```bash
git branch --set-upstream-to=origin/master master
```

### Discard changes not clearing
```bash
git rm --cached -r .
git reset --hard
```

---

## 12. Multiple GitHub Accounts Setup on One Machine

### Step 1: Create SSH Folder & Generate Keys
```bash
mkdir -p ~/.ssh && cd ~/.ssh

# Personal Account
ssh-keygen -t ed25519 -C "personal-email@example.com" -f ~/.ssh/id_ed25519_personal

# Work Account
ssh-keygen -t ed25519 -C "work-email@example.com" -f ~/.ssh/id_ed25519_work
```

### Step 2: Auto-start SSH Agent in `~/.bash_profile`
Add to `~/.bash_profile`:
```bash
# Auto-start ssh-agent
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add ~/.ssh/id_ed25519_personal
    ssh-add ~/.ssh/id_ed25519_work
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add ~/.ssh/id_ed25519_personal
    ssh-add ~/.ssh/id_ed25519_work
fi

unset env
```

Reload profile:
```bash
source ~/.bash_profile
ssh-add -l
```

### Step 3: Add Public Keys to GitHub / GitLab
Copy the public key content:
```bash
cat ~/.ssh/id_ed25519_personal.pub
```
Go to **GitHub → Settings → SSH and GPG keys → New SSH key** and paste. Repeat for work key.

### Step 4: Configure `~/.ssh/config`
```ini
# Personal GitHub
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal

# Work GitHub
Host github-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_work
```

Set file permissions:
```bash
chmod 600 ~/.ssh/config
```

### Step 5: Test Connections & Clone
```bash
# Test SSH connections
ssh -T git@github-personal
ssh -T git@github-work

# Clone using configured host aliases
git clone git@github-work:work-username/repo.git
git clone git@github-personal:personal-username/repo.git
```

---

## 13. Railway CLI Deployment Reference
```bash
# Install Railway CLI globally
npm i -g @railway/cli

# Login and verify account
railway login
railway whoami

# Project management
railway init   # Select workspace & create new project
railway link   # Link to existing project
railway up     # Deploy project from current directory
```
