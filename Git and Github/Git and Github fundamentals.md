# Git & GitHub Fundamentals Notes

Git is a **version control system** that tracks changes in your code over time.

GitHub is a **cloud platform** where you store Git repositories, collaborate with others, and manage projects.

Git helps you manage code locally, while GitHub helps you share and collaborate online.

---

## Why Git is used

### 1. Track Changes

Git records every change made to your project.

Without Git:

```text
project-final.zip
project-final-v2.zip
project-final-final.zip
project-final-final-new.zip ❌
```

With Git:

```text
Version 1 ✅
Version 2 ✅
Version 3 ✅
```

Every change is saved in the project's history.

---

### 2. Restore Previous Versions

If you accidentally break your application, you can return to an earlier working version.

Without Git:

> Hope you made a backup. ❌

With Git:

```bash
git checkout <commit-id>
```

Restore your project to a previous state.

---

### 3. Team Collaboration

Multiple developers can work on the same project without overwriting each other's code.

Example:

```text
Developer A
Builds Login Feature

Developer B
Builds Dashboard

Developer C
Fixes Bugs
```

Git combines everyone's work together.

---

### 4. Safe Experimentation

Want to try a new feature?

Create a new branch.

```text
Main Project

↓

New Feature Branch

↓

Test

↓

Merge if successful
```

If it fails, simply delete the branch.

---

### 5. Project Backup

Your code is safely stored online on GitHub.

If your laptop crashes:

```text
Buy a new laptop

↓

git clone repository

↓

Continue working
```

No work is lost if it has been pushed to GitHub.

---

## Why GitHub is used

GitHub is where developers:

* Store projects
* Collaborate with teams
* Review code
* Track issues
* Showcase portfolios
* Automate workflows using GitHub Actions

It is also commonly used by recruiters to review projects and coding practices.

---

## Git Workflow

```text
Write Code

↓

git add

↓

git commit

↓

git push

↓

GitHub Repository
```

When another developer updates the project:

```text
GitHub

↓

git pull

↓

Latest Changes
```

---

## Basic Git Commands

```bash
git init                 # Initialize a Git repository
git status               # Check repository status
git add .                # Stage all changes
git commit -m "message"  # Save changes
git log                  # View commit history
git branch               # List branches
git checkout branch-name # Switch branch
git merge branch-name    # Merge branches
git pull                 # Download latest changes
git push                 # Upload changes to GitHub
git clone <repository>   # Copy a repository
```

---

## Example

Suppose you build a React application.

Without Git:

```text
React App

↓

Make changes

↓

Oops... everything breaks.
```

You have no easy way to recover.

With Git:

```text
Commit 1

↓

Commit 2

↓

Commit 3

↓

Bug introduced

↓

Return to Commit 2
```

Your work is protected.

---

## Git in a Real Company

A typical workflow looks like this:

```text
Developer

↓

Feature Branch

↓

Commit Changes

↓

Push to GitHub

↓

Pull Request

↓

Code Review

↓

Merge into Main

↓

Deploy
```

Every feature is reviewed before becoming part of the main application.

---

## Common Git Commands

```bash
git init
git clone <repository>
git status
git add .
git commit -m "Initial commit"
git push origin main
git pull origin main
git branch
git checkout -b feature/login
git merge feature/login
git log
```

---

## Git vs GitHub

| Git                        | GitHub                                      |
| -------------------------- | ------------------------------------------- |
| Version control system     | Cloud hosting platform for Git repositories |
| Installed on your computer | Accessible through the web                  |
| Tracks code changes        | Stores and shares repositories              |
| Works offline              | Requires internet for syncing               |
| Manages project history    | Enables collaboration and portfolio hosting |

---



## Benefits of Git & GitHub

* Track every code change
* Collaborate with developers
* Restore previous versions
* Work safely using branches
* Backup projects online
* Showcase your portfolio
* Automate testing and deployment using GitHub Actions

---

> **These notes are for educational purposes and study material. To understand better and faster.**
