# Contributing to Vehicloud

## How to Push Your Project to This Repository

This guide provides all the details you need to push code to the `seyedali/vehicloud` repository.

## Prerequisites

### 1. Install Git
First, ensure Git is installed on your system:

```bash
# Check if Git is installed
git --version

# If not installed:
# On Ubuntu/Debian
sudo apt-get install git

# On macOS
brew install git

# On Windows
# Download from https://git-scm.com/download/win
```

### 2. Configure Git
Set up your Git identity (required for commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 3. Authentication Setup

You need to authenticate with GitHub to push code. Choose one of these methods:

#### Option A: SSH Key (Recommended)

1. **Generate SSH Key:**
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   # Press Enter to accept default location
   # Optionally set a passphrase
   ```

2. **Add SSH Key to SSH Agent:**
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

3. **Copy Public Key:**
   ```bash
   cat ~/.ssh/id_ed25519.pub
   # Copy the output
   ```

4. **Add to GitHub:**
   - Go to GitHub.com → Settings → SSH and GPG keys → New SSH key
   - Paste your public key
   - Click "Add SSH key"

5. **Update Remote URL to SSH:**
   ```bash
   cd /path/to/vehicloud
   git remote set-url origin git@github.com:seyedali/vehicloud.git
   ```

#### Option B: Personal Access Token (HTTPS)

1. **Generate Token:**
   - Go to GitHub.com → Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Click "Generate new token (classic)"
   - Select scopes: `repo` (full control)
   - Generate and copy the token (save it securely!)

2. **Use Token When Pushing:**
   ```bash
   # When prompted for password, use your token instead
   git push
   # Username: your-github-username
   # Password: your-personal-access-token
   ```

3. **Cache Credentials (Optional):**
   ```bash
   # Store credentials for 1 hour
   git config --global credential.helper 'cache --timeout=3600'
   
   # Or store permanently (less secure)
   git config --global credential.helper store
   ```

## Workflow for Pushing Your Project

### If Starting Fresh (New Local Project)

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/seyedali/vehicloud.git
   cd vehicloud
   ```

2. **Add Your Project Files:**
   ```bash
   # Copy your project files into this directory
   cp -r /path/to/your/project/* .
   ```

3. **Check Status:**
   ```bash
   git status
   ```

4. **Stage Your Changes:**
   ```bash
   # Add all files
   git add .
   
   # Or add specific files
   git add file1.txt file2.txt
   ```

5. **Commit Your Changes:**
   ```bash
   git commit -m "Add initial project files"
   ```

6. **Push to GitHub:**
   ```bash
   # Push to main branch
   git push origin main
   
   # Or push to a feature branch
   git checkout -b feature/my-feature
   git push origin feature/my-feature
   ```

### If You Already Have a Local Repository

1. **Add Remote:**
   ```bash
   cd /path/to/your/existing/project
   git remote add origin https://github.com/seyedali/vehicloud.git
   ```

2. **Fetch and Merge:**
   ```bash
   git fetch origin
   git branch --set-upstream-to=origin/main main
   git pull origin main --allow-unrelated-histories
   ```

3. **Push Your Code:**
   ```bash
   git push origin main
   ```

## Best Practices

### Branch Workflow

1. **Create a Feature Branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make Changes and Commit:**
   ```bash
   git add .
   git commit -m "Descriptive commit message"
   ```

3. **Push Feature Branch:**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create Pull Request:**
   - Go to GitHub.com
   - Click "Compare & pull request"
   - Add description and submit

### Commit Message Guidelines

- Use present tense ("Add feature" not "Added feature")
- Be descriptive but concise
- Reference issues when applicable: "Fix issue #123"

### .gitignore

The repository includes a `.gitignore` file with common patterns for files that shouldn't be committed (dependencies, build artifacts, IDE files, etc.). Review and customize it for your specific project needs.

## Common Commands Cheat Sheet

```bash
# Check current status
git status

# View changes
git diff

# View commit history
git log --oneline

# Create and switch to new branch
git checkout -b branch-name

# Switch to existing branch
git checkout branch-name

# List all branches
git branch -a

# Pull latest changes
git pull origin main

# Push changes
git push origin branch-name

# Undo uncommitted changes
git checkout -- filename

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Update from remote
git fetch origin
git merge origin/main
```

## Troubleshooting

### Permission Denied (publickey)

**Problem:** Can't push due to SSH authentication failure.

**Solution:**
1. Verify SSH key is added to GitHub
2. Test connection: `ssh -T git@github.com`
3. Check SSH agent: `ssh-add -l`

### Authentication Failed (HTTPS)

**Problem:** Can't push with username/password.

**Solution:**
- GitHub no longer accepts password authentication
- Use a Personal Access Token instead (see Authentication Setup)

### Repository Not Found

**Problem:** `fatal: repository 'https://github.com/seyedali/vehicloud.git' not found`

**Solution:**
1. Verify the URL is correct
2. Ensure you have access to the repository
3. Check your authentication

### Merge Conflicts

**Problem:** Conflicts when pulling or merging.

**Solution:**
1. Pull latest changes: `git pull origin main`
2. Open conflicted files and resolve conflicts
3. Stage resolved files: `git add conflicted-file.txt`
4. Complete merge: `git commit`

### Push Rejected

**Problem:** `! [rejected] main -> main (fetch first)`

**Solution:**
```bash
# Pull latest changes first
git pull origin main

# Then push
git push origin main
```

## Getting Help

- **Git Documentation:** https://git-scm.com/doc
- **GitHub Guides:** https://guides.github.com/
- **Pro Git Book:** https://git-scm.com/book/en/v2

## Repository Information

- **Repository:** https://github.com/seyedali/vehicloud
- **Clone URL (HTTPS):** https://github.com/seyedali/vehicloud.git
- **Clone URL (SSH):** git@github.com:seyedali/vehicloud.git

## Quick Start Summary

For those who want the fastest path:

```bash
# 1. Clone the repository
git clone https://github.com/seyedali/vehicloud.git
cd vehicloud

# 2. Add your files
cp -r /path/to/your/project/* .

# 3. Stage, commit, and push
git add .
git commit -m "Add my project files"
git push origin main
```

Remember to set up authentication (SSH or Token) before pushing!
