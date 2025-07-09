# 📘 Git Essentials & Configuration Guide

### Quick Help

```bash
git config -h
git config --help
```

---

## 🫠 Lesson 1: What Is Git?

Git is a **version control system** — it tracks changes in your code over time, lets you collaborate with others, and helps you roll back to previous versions if needed.

---

## 🚀 Lesson 2: Git Setup

### Configuration Scopes

| Scope  | Command flag          | Affects...              | Location                                 |
| ------ | --------------------- | ----------------------- | ---------------------------------------- |
| System | `--system`            | All users on the system | `/etc/gitconfig`                         |
| Global | `--global`            | Your user account       | `~/.gitconfig` or `~/.config/git/config` |
| Local  | `--local` *(default)* | Only current repository | `.git/config` inside the repo            |

### Editing Configuration Files

```bash
git config --global --edit     # ~/.gitconfig
git config --system --edit     # /etc/gitconfig
git config --local --edit      # .git/config
```

### Set Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Enable Colored Output

```bash
git config --global color.ui auto
```

### Set Default Editor

```bash
git config --global core.editor "code --wait"   # VS Code
```

### Configure Line Endings

```bash
git config --global core.autocrlf true
```

### Credential Caching

```bash
git config --global credential.helper cache
```

### Set Aliases

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
```

### Verify Setup

```bash
git config --list
```

---

## 📓 Lesson 3: Git Basics

### Create a New Repo

```bash
git init
```

### Check Status

```bash
git status
```

### Stage Files

```bash
git add filename.txt  # One file
git add .             # All files
```

### Commit Changes

```bash
git commit -m "Your commit message"
```

### Stage & Commit Together

```bash
git commit -am "Your commit message"
```

### Amend Commit

```bash
git commit --amend -m "Updated commit message"
git commit --amend --no-edit  # Keep message, change content
```

---

## 🗵️ Lesson 4: Working With History

### View Commit History

```bash
git log
git log --oneline --graph --decorate
```

### Show What Changed

```bash
git diff
```

### View File-Specific History

```bash
git log filename.txt
```

---

## 🔀 Lesson 5: Branching & Merging

### Rename Default Branch

```bash
git branch -M main
```

### Create a New Branch

```bash
git branch new-feature
```

### Switch to a Branch

```bash
git checkout new-feature
```

### Create and Switch

```bash
git checkout -b new-feature
```

### Merge Branch

```bash
git checkout main
git merge new-feature
```

### Delete Branch

```bash
git branch -d new-feature
```

---

## 🌍 Lesson 6: Git Remotes

### Add Remote

```bash
git remote add origin https://github.com/user/repo.git
```

### Push to Remote

```bash
git push -u origin main
```

### Clone Repo

```bash
git clone https://github.com/user/repo.git
```

### Pull Changes

```bash
git pull origin main
```

---

## 🛠️ Lesson 7: Fixing Mistakes

### Unstage a File

```bash
git reset filename.txt
```

### Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1
```

### Undo Last Commit (Discard Changes)

```bash
git reset --hard HEAD~1
```

### Revert a Commit

```bash
git revert <commit-hash>
git revert --abort  # Cancel revert
```

### Stash Changes

```bash
git stash               # Save changes
git checkout main       # Switch branch
# Fix bug...
git commit -am "Bug fix"
git checkout feature-branch
git stash pop           # Reapply stashed changes
```

### Squash Commits

Used to combine multiple commits into one:

```bash
git rebase -i HEAD~3
# Change 'pick' to 'squash' for commits to combine
```

---

## ❌ Remove Git Tracking

```bash
rm -rf .git           # Completely removes Git from a folder
cp -r .git .git_backup  # Optional backup
```

---

## 🔐 GitHub Authentication

### Personal Access Token (PAT)

> 📍 Generate from:
> **GitHub** → **Settings** → **Developer Settings** → **Personal access tokens** → **Tokens (classic)** → **Generate token**

---

### SSH Key Authentication

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

* Public key: `~/.ssh/id_ed25519.pub`
* Private key: `~/.ssh/id_ed25519`

📍 Add the **public key** to:
**GitHub** → **Settings** → **SSH and GPG Keys** → **New SSH key**

> 💡 `ed25519` is a secure modern cryptographic algorithm.

---

## 🧪 Git with PowerShell (Optional)

### Install posh-git

```powershell
Install-Module PowerShellGet -Force
PowerShellGet\Install-Module posh-git -Scope CurrentUser -Force
PowerShellGet\Update-Module posh-git
```

---

