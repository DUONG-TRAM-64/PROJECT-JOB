# Git & GitHub SSH Workflow on Windows

## 1. Move to Project Directory

```bash
cd C:\Users\Tram\Desktop\PROJECT-JOB
```

---

# 2. Initialize Git Repository

```bash
git init
```

### What it does

- Creates hidden `.git` folder
- Turns normal folder into Git repository
- Enables version control

---

# 3. Setup SSH Connection with GitHub (One-Time Setup)

## Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```

Press `Enter` continuously.

SSH keys will be stored in:

```bash
C:\Users\YourName\.ssh
```

---

## Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

---

## Add SSH Key to Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## Copy Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output beginning with:

```text
ssh-ed25519 AAAA...
```

---

## Add SSH Key to GitHub

GitHub SSH Settings:

https://github.com/settings/keys

- Click `New SSH Key`
- Paste the public key
- Save

---

## Test SSH Connection

```bash
ssh -T git@github.com
```

Successful output:

```text
Hi DUONG-TRAM-64! You've successfully authenticated...
```

---

# 4. Create GitHub Repository

Example repository name:

```text
PROJECT-JOB
```

Repository URL:

```text
https://github.com/DUONG-TRAM-64/PROJECT-JOB
```

---

# 5. Connect Local Project to GitHub

```bash
git remote add origin git@github.com:DUONG-TRAM-64/PROJECT-JOB.git
```

### What it does

- Connects local repository to GitHub
- `origin` is the nickname of remote repository

---

# 6. Rename Branch to main

```bash
git branch -M main
```

### Why

Modern GitHub repositories use:

```text
main
```

instead of:

```text
master
```

---

# 7. Add Files to Staging Area

```bash
git add .
```

### What it does

- Tracks files
- Prepares files for commit

---

# 8. Create Commit

```bash
git commit -m "first commit"
```

### What it does

- Creates a snapshot/checkpoint of source code
- Saves version history locally

---

# 9. Push Code to GitHub

```bash
git push -u origin main
```

### What it does

- Uploads source code to GitHub
- Links local branch with remote branch

After first push, you can simply use:

```bash
git push
```

---

# Daily Git Workflow (Real-World Usage)

```bash
git status
git add .
git commit -m "update feature"
git push
```

---

# Clone Existing Repository

```bash
git clone git@github.com:DUONG-TRAM-64/PROJECT-JOB.git
```

---

# Useful Git Commands

## Check Current Branch

```bash
git branch
```

---

## Check Remote Repository

```bash
git remote -v
```

---

## Check Git Status

```bash
git status
```

---

## Pull Latest Code

```bash
git pull
```

---

## View Commit History

```bash
git log
```

---

# Git Concepts

## Git Local Repository

Stores version history on your computer.

---

## GitHub Remote Repository

Stores project online.

---

## Commit

A saved version/checkpoint of code.

---

## Push

Uploads code to GitHub.

---

## Pull

Downloads latest code from GitHub.

---

# Git Workflow Diagram

```text
Local Project
    ↓
git init
    ↓
Git Local Repository
    ↓
git remote add origin
    ↓
Connected to GitHub
    ↓
git add .
git commit
    ↓
Save version locally
    ↓
git push
    ↓
Upload to GitHub
```

---

# README.md Example

```markdown
# PROJECT-JOB

## Description

Basic project initialized with Git and GitHub SSH integration.

## Installation

```bash
git clone git@github.com:DUONG-TRAM-64/PROJECT-JOB.git
```

## Usage

Describe project usage here.

## Author

DUONG-TRAM-64
```

---

# Common Errors

## Remote Already Exists

```text
error: remote origin already exists
```

### Fix

```bash
git remote remove origin
```

Then add remote again.

---

## Repository Not Found

```text
ERROR: Repository not found.
```

### Causes

- Repository does not exist
- Wrong repository name
- Wrong remote URL

---

## Permission Denied (SSH)

```text
Permission denied (publickey)
```

### Fix

- Add SSH key to GitHub
- Test SSH connection again

```bash
ssh -T git@github.com
```

---

# Complete Setup Commands (Quick Version)

```bash
cd PROJECT-JOB

git init

git remote add origin git@github.com:DUONG-TRAM-64/PROJECT-JOB.git

git branch -M main

git add .

git commit -m "first commit"

git push -u origin main
```