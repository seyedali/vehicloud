# Git Quick Reference for Vehicloud

## Essential Commands for Daily Use

### Initial Setup (One-Time)

```bash
# Configure your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Clone this repository
git clone https://github.com/seyedali/vehicloud.git
cd vehicloud
```

### Daily Workflow

```bash
# 1. Check what changed
git status

# 2. Add files to staging
git add filename.txt          # Add specific file
git add .                     # Add all changes

# 3. Commit with message
git commit -m "Brief description of changes"

# 4. Push to GitHub
git push origin main          # Push to main branch
git push origin branch-name   # Push to specific branch

# 5. Pull latest changes
git pull origin main
```

### Working with Branches

```bash
# Create new branch
git checkout -b feature/my-feature

# Switch to existing branch
git checkout branch-name

# List all branches
git branch -a

# Delete local branch
git branch -d branch-name

# Push new branch to GitHub
git push origin feature/my-feature
```

### Viewing History and Changes

```bash
# View commit history
git log --oneline -10         # Last 10 commits
git log --graph --oneline     # With branch visualization

# View changes
git diff                      # Uncommitted changes
git diff HEAD~1               # Compare with previous commit
git show commit-hash          # View specific commit

# View file at specific commit
git show commit-hash:path/to/file
```

### Undoing Changes

```bash
# Discard uncommitted changes to a file
git checkout -- filename.txt

# Unstage a file (keep changes)
git reset filename.txt

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes) - CAREFUL!
git reset --hard HEAD~1
```

### Authentication Quick Setup

#### SSH (Recommended)

```bash
# Generate key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Start SSH agent and add key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key (add to GitHub Settings)
cat ~/.ssh/id_ed25519.pub

# Change remote to SSH
git remote set-url origin git@github.com:seyedali/vehicloud.git

# Test connection
ssh -T git@github.com
```

#### Personal Access Token (HTTPS)

1. Generate at: GitHub.com → Settings → Developer settings → Personal access tokens
2. Use token as password when pushing
3. Cache credentials: `git config --global credential.helper cache`

### Common Issues & Fixes

```bash
# Push rejected - need to pull first
git pull --rebase origin main  # Preferred: keeps history cleaner
# Or: git pull origin main      # Creates merge commit
git push origin main

# Merge conflicts
git pull origin main          # Conflicts appear
# Edit files to resolve conflicts
git add resolved-file.txt
git commit -m "Resolve merge conflicts"
git push origin main

# Accidentally committed wrong files
git reset --soft HEAD~1       # Undo commit, keep changes
git reset filename.txt        # Unstage specific file
git commit -m "Correct commit"

# Want to start over (CAREFUL!)
git fetch origin
git reset --hard origin/main
```

### Useful Git Aliases

Add these to your `~/.gitconfig` for shortcuts:

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --graph --oneline --all'
```

Then use: `git st` instead of `git status`, etc.

### Best Practices

✅ **Do:**
- Commit often with descriptive messages
- Pull before you push
- Use branches for new features
- Review changes with `git diff` before committing
- Keep commits focused and atomic

❌ **Don't:**
- Commit sensitive data (passwords, API keys)
- Force push to shared branches
- Commit large binary files
- Use vague commit messages like "fix" or "update"

### Need More Help?

- Full guide: [CONTRIBUTING.md](CONTRIBUTING.md)
- Git documentation: https://git-scm.com/doc
- GitHub guides: https://guides.github.com/

### Repository URLs

- **HTTPS:** https://github.com/seyedali/vehicloud.git
- **SSH:** git@github.com:seyedali/vehicloud.git
- **Web:** https://github.com/seyedali/vehicloud
