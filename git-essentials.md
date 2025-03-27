# Git Core Learnings

## 1. What is Git?
- Distributed Version Control System (DVCS)
- Tracks changes in source code during software development
- Allows multiple developers to work together efficiently

## 2. Core Concepts

### Basic Git Workflow
1. Working Directory
2. Staging Area (Index)
3. Repository (Local/Remote)

### Key Terminology
- Repository: Project's entire history
- Commit: Snapshot of project at a specific point
- Branch: Parallel version of repository
- Remote: Version of repository hosted online (e.g., GitHub)

## 3. Essential Git Commands

### Repository Setup
```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone <repository-url>
```

### Basic Workflow
```bash
# Check status of files
git status

# Add files to staging area
git add <filename>    # Specific file
git add .             # All files

# Commit changes
git commit -m "Commit message"

# Push changes to remote repository
git push origin <branch-name>
```

### Branching and Merging
```bash
# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>

# Create and switch to a new branch
git checkout -b <branch-name>

# Merge branches
git merge <branch-name>
```

### Checking History
```bash
# View commit history
git log

# View changes
git diff

# Show details of a specific commit
git show <commit-hash>
```

## 4. Common Scenarios and Solutions

### Undoing Changes
```bash
# Unstage a file
git reset <filename>

# Discard local changes
git checkout -- <filename>

# Revert a commit
git revert <commit-hash>
```

### Handling Conflicts
1. Git marks conflict areas in files
2. Manually edit files to resolve conflicts
3. Stage and commit resolved files

## 5. Best Practices
- Commit frequently
- Write clear, descriptive commit messages
- Use branches for new features
- Pull before pushing
- Never commit sensitive information

## 6. Basic .gitignore
```
# Ignore compiled files
*.class
*.jar

# Ignore build directories
/target/
/build/

# Ignore IDE-specific files
.idea/
.vscode/

# Ignore environment files
.env
```

## 7. Typical Workflow
1. Clone repository
2. Create feature branch
3. Make changes
4. Stage changes
5. Commit with clear message
6. Push to remote
7. Create pull request
8. Code review
9. Merge to main branch

## 8. Key Git Hosting Platforms
- GitHub
- GitLab
- Bitbucket

## 9. Essential Git Configurations
```bash
# Set username
git config --global user.name "Your Name"

# Set email
git config --global user.email "your.email@example.com"
```

## 10. Learning Path
1. Understand basic concepts
2. Practice basic commands
3. Learn branching strategies
4. Explore advanced Git features
5. Use in real projects
6. Learn about Git workflows

## Recommended Tools
- Git CLI
- GitHub Desktop
- GitKraken
- VS Code Git integration

## Quick Reference Cheat Sheet
- `git init`: Start a repository
- `git clone`: Copy a repository
- `git add`: Stage changes
- `git commit`: Save changes
- `git push`: Upload commits
- `git pull`: Download changes
- `git branch`: List/create branches
- `git merge`: Combine branches
- `git log`: View history
