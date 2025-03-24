# Git Essentials:

## 1. Version Control Basics
- **What is Git?**: A distributed version control system that tracks changes to files.
- **Why Git?**: Enables collaboration, history tracking, and code recovery.

---

## 2. Installation & Setup
- **Install Git**:
  - Windows: Download from [git-scm.com](https://git-scm.com)
  - macOS: `brew install git`
  - Linux: `sudo apt-get install git`
- **Configure User**:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your@email.com"
  ```

---

## 3. Repository Basics
- **Initialize a Repository**:
  ```bash
  git init
  ```
- **Clone a Repository**:
  ```bash
  git clone https://github.com/user/repo.git
  ```

---

## 4. Staging & Committing
- **Check Status**:
  ```bash
  git status
  ```
- **Add Changes to Staging**:
  ```bash
  git add <file>    # Add specific file
  git add .         # Add all changes
  ```
- **Commit Changes**:
  ```bash
  git commit -m "Descriptive commit message"
  ```

---

## 5. Viewing History
- **Show Commit Log**:
  ```bash
  git log
  git log --oneline  # Compact view
  git log --graph    # Visualize branches
  ```

---

## 6. Branches
- **Create a Branch**:
  ```bash
  git branch <branch-name>
  ```
- **Switch Branches**:
  ```bash
  git checkout <branch-name>
  git switch <branch-name>  # Newer alternative
  ```
- **Merge Branches**:
  ```bash
  git checkout main
  git merge <branch-name>
  ```
- **Delete a Branch**:
  ```bash
  git branch -d <branch-name>
  ```

---

## 7. Remote Repositories
- **Add a Remote**:
  ```bash
  git remote add origin https://github.com/user/repo.git
  ```
- **Push to Remote**:
  ```bash
  git push -u origin main  # First push
  git push                 # Subsequent pushes
  ```
- **Pull Updates**:
  ```bash
  git pull origin main
  ```
- **Fetch Changes**:
  ```bash
  git fetch  # Retrieves updates without merging
  ```

---

## 8. Handling Merge Conflicts
1. **Identify Conflicts**: Git marks conflicting files.
2. **Edit Files**: Manually resolve conflicts.
3. **Add & Commit**:
   ```bash
   git add <resolved-file>
   git commit -m "Resolved merge conflict"
   ```

---

## 9. Common Workflows
1. **Feature Branch Workflow**:
   - Create a branch for new features.
   - Merge to `main` after review.
2. **Pull Request (PR)**: Collaborate via code reviews before merging.

---

## 10. Undoing Changes
- **Discard Unstaged Changes**:
  ```bash
  git restore <file>
  ```
- **Unstage a File**:
  ```bash
  git restore --staged <file>
  ```
- **Amend Last Commit**:
  ```bash
  git commit --amend
  ```
- **Reset to Previous Commit**:
  ```bash
  git reset --hard HEAD~1  # WARNING: Destructive
  ```

---

## 11. Stashing Changes
- **Save Temporary Work**:
  ```bash
  git stash
  ```
- **Restore Stashed Work**:
  ```bash
  git stash pop
  ```

---

## 12. Key Best Practices
1. **Commit Often**: Small, logical commits.
2. **Write Meaningful Messages**: Use imperative tense ("Add feature" not "Added").
3. **Avoid Large Files**: Use `.gitignore` for logs, binaries, etc.
4. **Branch Naming**: Use `feature/`, `bugfix/`, or `hotfix/` prefixes.

---

## 13. Essential Commands Cheat Sheet
| Command                  | Description                          |
|--------------------------|--------------------------------------|
| `git init`               | Initialize a new repo               |
| `git clone <url>`        | Clone a remote repo                 |
| `git add <file>`         | Stage changes                       |
| `git commit -m "msg"`    | Commit staged changes               |
| `git status`             | Check working directory status      |
| `git log`                | View commit history                 |
| `git branch`             | List/create branches                |
| `git checkout <branch>`  | Switch branches                     |
| `git merge <branch>`     | Merge branches                      |
| `git pull`               | Fetch + merge from remote           |
| `git push`               | Push commits to remote              |
| `git diff`               | See unstaged changes                |

---
