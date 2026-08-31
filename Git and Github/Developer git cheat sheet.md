# Git & GitHub — Developer Career Cheat Sheet

> **Core workflow:** `clone → branch → code → status → add → commit → push → pull request → merge`

---

## 1. Setup — First Time

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

git config --list
```

---

## 2. Start / Get a Repository

### Create Git repository locally

```bash
git init
```

### Clone existing GitHub repository

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
```

### Check remote

```bash
git remote -v
```

### Add remote

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

---

## 3. Check Your Work

```bash
git status
```

### See commit history

```bash
git log
git log --oneline
```

### See changes

```bash
git diff
```

---

## 4. Daily Development Workflow 

After making code changes:

```bash
git status
git add .
git commit -m "Add product API"
git push
```

### Better practice: add specific files

```bash
git add Program.cs Controllers/ProductController.cs
git commit -m "Add product API"
git push
```

---

## 5. Branches 

### See branches

```bash
git branch
```

### Create branch

```bash
git branch feature/product-api
```

### Switch branch

```bash
git switch feature/product-api
```

### Create + switch

```bash
git switch -c feature/product-api
```

### Delete local branch

```bash
git branch -d feature/product-api
```

### Push new branch

```bash
git push -u origin feature/product-api
```

**Typical professional workflow:**

```text
main
 │
 ├── feature/product-api
 ├── feature/authentication
 └── bugfix/cart-total
```

Branches let you work on features without directly changing the stable `main` branch.

---

## 6. Get Changes from GitHub 

### Download changes without merging

```bash
git fetch
```

### Download + merge changes

```bash
git pull
```

### Pull specific branch

```bash
git pull origin main
```

`git pull` combines fetching remote changes with merging them into your current branch.

---

## 7. Merge

```bash
git switch main
git pull origin main
git merge feature/product-api
```

Then:

```bash
git push origin main
```

### Recommended team workflow

Instead of directly merging locally:

```text
feature branch
      ↓
    push
      ↓
Pull Request
      ↓
Code Review
      ↓
Merge
      ↓
main
```

Pull requests allow changes to be reviewed before they are merged into the main branch.

---

## 8. Undo / Fix Mistakes 

### Unstage a file

```bash
git restore --staged filename
```

### Discard local changes

```bash
git restore filename
```

⚠️ This can permanently discard uncommitted changes.

### Change last commit message

```bash
git commit --amend -m "Better commit message"
```

### Undo last commit but keep changes

```bash
git reset --soft HEAD~1
```

### Temporarily save unfinished work

```bash
git stash
```

### Bring stashed work back

```bash
git stash pop
```

### View stashes

```bash
git stash list
```

---

## 9. Remove Files

```bash
git rm filename
git commit -m "Remove unused file"
```

For a directory:

```bash
git rm -r folder-name
```

---

## 10. Remote Repository Commands

```bash
git remote -v
git remote add origin URL
git remote remove origin
git remote set-url origin URL
```

---

## 11. Tags / Releases

### Create tag

```bash
git tag v1.0.0
```

### Push tag

```bash
git push origin v1.0.0
```

### Push all tags

```bash
git push --tags
```

Useful for marking releases:

```text
v1.0.0
v1.1.0
v2.0.0
```

---

## 12. Useful Investigation Commands

### Who changed a line?

```bash
git blame filename
```

### Search commit history

```bash
git log --oneline --all
```

### Show a commit

```bash
git show COMMIT_ID
```

### Compare branches

```bash
git diff main..feature/product-api
```

---

# 13. GitHub CLI — Useful Career Commands

If GitHub CLI (`gh`) is installed:

### Login

```bash
gh auth login
```

### Check authentication

```bash
gh auth status
```

### View repository

```bash
gh repo view
```

### Create repository

```bash
gh repo create
```

### Clone repository

```bash
gh repo clone USERNAME/REPOSITORY
```

### Create Pull Request

```bash
gh pr create
```

### View Pull Requests

```bash
gh pr list
```

### View issues

```bash
gh issue list
```

GitHub CLI lets you perform GitHub operations such as repositories, pull requests, and issues from the terminal.

---

# 14. .gitignore 

Create:

```text
.gitignore
```

Example for development:

```gitignore
.env
.venv/
bin/
obj/
node_modules/
*.log
.DS_Store
```

**Never commit:**

```text
passwords
API keys
database credentials
.env files
private certificates
secrets
```

---

# 15. Commit Message Examples

Good:

```bash
git commit -m "Add product API"
git commit -m "Fix cart total calculation"
git commit -m "Add JWT authentication"
git commit -m "Update database schema"
git commit -m "Handle payment validation error"
```

Avoid:

```bash
git commit -m "changes"
git commit -m "update"
git commit -m "final"
git commit -m "stuff"
```

A commit should describe **what changed**.

---

# 16. Most Important Commands to Memorise 

If you remember only these:

```bash
git status
git add .
git commit -m "message"
git push
git pull
git clone URL
git switch -c feature/name
git switch main
git branch
git merge branch-name
git log --oneline
git diff
git stash
```

---

# 17. Real Developer Workflow

### Starting work

```bash
git switch main
git pull origin main
git switch -c feature/payment-api
```

### Develop

```text
Write code
↓
Test
↓
Fix bugs
```

### Save work

```bash
git status
git add .
git commit -m "Add payment API"
```

### Upload branch

```bash
git push -u origin feature/payment-api
```

### GitHub

```text
Create Pull Request
        ↓
Code Review
        ↓
Fix requested changes
        ↓
git add .
git commit -m "Fix payment validation"
git push
        ↓
Merge PR
```

### Update local main

```bash
git switch main
git pull origin main
```

---

# 18. Mental Model

```text
WORKING DIRECTORY
       │
       │ git add
       ▼
STAGING AREA
       │
       │ git commit
       ▼
LOCAL REPOSITORY
       │
       │ git push
       ▼
GITHUB / REMOTE
```

To get other people's changes:

```text
GITHUB / REMOTE
       │
       │ git pull
       ▼
LOCAL REPOSITORY
```

---

# 19. Git vs GitHub

### Git

Version-control system running on your computer.

```text
Git
→ tracks changes
→ creates commits
→ manages branches
→ merges code
```

### GitHub

Online platform built around Git.

```text
GitHub
→ hosts repositories
→ Pull Requests
→ Issues
→ Code Reviews
→ Actions
→ collaboration
```

GitHub itself is built around Git, while GitHub provides the collaboration and hosting layer.

---

# 20. Career Priority

### MUST KNOW 
```bash
git init
git clone
git status
git add
git commit
git push
git pull
git branch
git switch
git merge
git log
git diff
git stash
```

### SHOULD KNOW 

```bash
git fetch
git restore
git reset
git remote
git tag
git blame
```

### Professional workflow

```text
Branch
 ↓
Code
 ↓
Commit
 ↓
Push
 ↓
Pull Request
 ↓
Review
 ↓
Merge
```

**Don't try to memorize 100 Git commands. Master the workflow.**
