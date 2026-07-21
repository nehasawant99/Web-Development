# 📋 The Complete Commit Shortcut List

| Shortcut | When to Use It | Example Message |
| --- | --- | --- |
| **`feat:`** | Adding a **brand new feature** or piece of functionality. | `git commit -m "feat: add hybrid log parser"` |
| **`fix:`** | **Fixing a bug**, code crash, or logic error. | `git commit -m "fix: resolve page crash on empty files"` |
| **`chore:`** | **Housekeeping tasks** that don't change the app code (tools, settings, `.gitignore`). | `git commit -m "chore: add logs to gitignore"` |
| **`docs:`** | Making changes **only to documentation** files (like `README.md`). | `git commit -m "docs: add setup steps to readme"` |
| **`refactor:`** | Rewriting code to make it cleaner/faster **without changing how it works**. | `git commit -m "refactor: optimise database queries"` |
| **`style:`** | Formatting changes that don't affect code meaning (white-space, semicolons). | `git commit -m "style: fix indentation in app.py"` |
| **`test:`** | Adding new test files or modifying existing testing scripts. | `git commit -m "test: add routing verification test case"` |

---

# 🛠️ How to Use Them (The 3 Golden Rules)

### 1. The Structure

Every commit message must follow this exact pattern:

```text
shortcut: lowercase message describing what you did

```

---

### 2. Keep it in Imperative Tone

Write your message like you are giving a command to the codebase.

* **Do this:** `feat: add network dashboard`
* **Don't do this:** `feat: added network dashboard` or `feat: adding network dashboard`

---

### 3. Example Terminal Workflow

When you are ready to save your changes in the terminal, you type it out like this:

```bash
# 1. Stage your modified files
git add app.py

# 2. Fire off the commit using the shortcut prefix
git commit -m "feat: integrate local memory tracking engine"

```

> **Tip:** Using these prefixes during hackathons or personal projects is a huge plus—reviewers can look at your commit log and see industry-standard practices right away.
