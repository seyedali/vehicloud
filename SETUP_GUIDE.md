# Step-by-Step Setup Guide for Vehicloud

This guide walks you through setting up your development environment and pushing your first code to the Vehicloud repository.

## Step 1: Install Git

### Windows
1. Download Git from https://git-scm.com/download/win
2. Run the installer
3. Use default options (recommended)
4. Open "Git Bash" from Start Menu

### macOS
```bash
# Using Homebrew (recommended)
brew install git

# Or download from https://git-scm.com/download/mac
```

### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install git
```

Verify installation:
```bash
git --version
```

## Step 2: Configure Git

Open terminal/Git Bash and run:

```bash
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"
```

Verify configuration:
```bash
git config --list
```

## Step 3: Set Up GitHub Authentication

You **must** set up authentication before you can push code. Choose ONE method:

### Method A: SSH Keys (Recommended for Regular Use)

#### Windows (Git Bash) / macOS / Linux

1. **Generate SSH Key:**
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   ```
   - Press Enter to save in default location
   - Optionally enter a passphrase (recommended for security)

2. **Start SSH Agent:**
   ```bash
   # Start the agent
   eval "$(ssh-agent -s)"
   
   # Add your key
   ssh-add ~/.ssh/id_ed25519
   ```

3. **Copy Your Public Key:**
   
   **On Windows (Git Bash):**
   ```bash
   cat ~/.ssh/id_ed25519.pub | clip
   ```
   
   **On macOS:**
   ```bash
   cat ~/.ssh/id_ed25519.pub | pbcopy
   ```
   
   **On Linux:**
   ```bash
   cat ~/.ssh/id_ed25519.pub
   # Then manually select and copy
   ```

4. **Add to GitHub:**
   - Go to https://github.com/settings/keys
   - Click "New SSH key"
   - Give it a title (e.g., "My Laptop")
   - Paste your public key
   - Click "Add SSH key"

5. **Test Connection:**
   ```bash
   ssh -T git@github.com
   ```
   You should see: "Hi username! You've successfully authenticated..."

### Method B: Personal Access Token (Easier for Beginners)

1. **Generate Token:**
   - Go to https://github.com/settings/tokens
   - Click "Generate new token" → "Generate new token (classic)"
   - Give it a note (e.g., "Vehicloud Development")
   - Select scopes: Check `repo` (this gives full repository access)
   - Click "Generate token"
   - **Copy the token immediately** (you won't see it again!)

2. **Save Token Securely:**
   - Paste it in a password manager or secure note
   - You'll need this token whenever you push code

3. **Optional - Cache Credentials:**
   ```bash
   # Remember credentials for 1 hour
   git config --global credential.helper 'cache --timeout=3600'
   ```

## Step 4: Clone the Repository

Choose the method that matches your authentication setup:

### If Using SSH:
```bash
git clone git@github.com:seyedali/vehicloud.git
cd vehicloud
```

### If Using HTTPS (Personal Access Token):
```bash
git clone https://github.com/seyedali/vehicloud.git
cd vehicloud
```

## Step 5: Add Your Project Files

Now you're inside the vehicloud directory. Add your project files:

```bash
# Copy your project files
# On Windows:
# copy /path/to/your/files/* .

# On macOS/Linux:
# cp -r /path/to/your/files/* .

# Or manually copy files using your file explorer
```

## Step 6: Check What You're About to Commit

```bash
# See what files have changed
git status

# See detailed changes
git diff
```

## Step 7: Stage Your Changes

```bash
# Add all files
git add .

# Or add specific files
git add file1.txt file2.txt folder/

# Check status again
git status
```

## Step 8: Commit Your Changes

```bash
git commit -m "Add initial project files for vehicloud"
```

**Tips for good commit messages:**
- Start with a verb ("Add", "Update", "Fix", "Remove")
- Be specific but concise
- Explain what and why, not how

## Step 9: Push to GitHub

```bash
git push origin main
```

**If using Personal Access Token:**
- Username: your GitHub username
- Password: your personal access token (NOT your GitHub password)

**If using SSH:**
- It should push without prompting for credentials

## Step 10: Verify on GitHub

1. Go to https://github.com/seyedali/vehicloud
2. You should see your files!

## Common First-Time Issues

### "Permission denied (publickey)"
- You're using SSH but the key isn't set up correctly
- Solution: Follow Method A steps again, or switch to Method B

### "Authentication failed"
- You're using HTTPS but token isn't correct
- Solution: Generate a new Personal Access Token and try again

### "fatal: remote origin already exists"
- Trying to clone into an existing directory
- Solution: Delete the directory or clone to a different location

### "Updates were rejected because the remote contains work"
- Remote has changes you don't have locally
- Solution:
  ```bash
  git pull origin main --rebase
  git push origin main
  ```

## Next Steps

### Making Changes Later

```bash
# 1. Pull latest changes
git pull origin main

# 2. Make your changes to files

# 3. Check what changed
git status

# 4. Stage and commit
git add .
git commit -m "Description of changes"

# 5. Push
git push origin main
```

### Working with Branches

```bash
# Create a new feature branch
git checkout -b feature/my-new-feature

# Make changes and commit
git add .
git commit -m "Add new feature"

# Push feature branch
git push origin feature/my-new-feature

# Then create a Pull Request on GitHub
```

## Getting Help

- **Quick reference:** See [GIT_QUICK_REFERENCE.md](GIT_QUICK_REFERENCE.md)
- **Detailed guide:** See [CONTRIBUTING.md](CONTRIBUTING.md)
- **Git basics:** https://git-scm.com/book/en/v2/Getting-Started-Git-Basics
- **GitHub guides:** https://guides.github.com/

## Checklist

Before you start coding:
- [ ] Git is installed
- [ ] Git is configured (name and email)
- [ ] GitHub authentication is set up (SSH or Token)
- [ ] Repository is cloned
- [ ] You can push a test file

Now you're ready to push your vehicloud project! 🚀
