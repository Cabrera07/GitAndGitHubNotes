# 🗺️ Roadmap

This is the original plan for the full **Git and GitHub Notes** project, kept here as-is so the structure and intent aren't lost. Sections 1–3 are done; sections 4–13 are documented backlog, not active work.

> 📌 **Status note:** this project is intentionally paused while other priorities take precedence. It's not abandoned — just parked.

---

## ✅ 1. Introduction — Complete

- What is Git and GitHub
- Git Workflow Overview
- Initialize Repository & Git Clone
- Understanding the difference between Git and GitHub

📂 [`docs/1-introduction/`](./docs/1-introduction/README.md)

---

## ✅ 2. Configurations and Setup — Complete

- SSH Keys: Generate, Add, and Verify SSH Information
- Setting up a License for a Repository
- Git Configuration Commands (`git config`)

📂 [`docs/2-configurations/`](./docs/2-configurations/)

---

## ✅ 3. Core Git Operations — Complete

- Staging and Committing Changes
  - `git add`
  - `git commit`
  - Conventional Commits
- Undoing Changes
  - `git reset`
  - `git restore`
  - Undo a Git Push
  - `git commit --amend`
- Deleting Commits
- Handling a Detached HEAD State

📂 [`docs/3-core-git-operations/`](./docs/3-core-git-operations/README.md)

---

## 📋 4. Branching and Collaboration — Planned

- Git Branch
  - Creating, Deleting, and Switching Branches
  - `git switch` vs. `git checkout` (Switching branches more efficiently)
  - Merging Branches
- Forking and Cloning
- Pull, Push, and Fetch
  - Types of Pull (`--rebase`, fast-forward, etc.)
  - `git pull` vs. `git fetch`
- Rebase
  - `git rebase` vs. `git merge`
  - Squashing Commits
- Handling Merge Conflicts
- Collaboration Best Practices
  - Review Processes
  - Branch Naming Conventions

## 📋 5. Advanced Git Commands — Planned

- Cherry Picking Commits
- Stashing Changes (`git stash`)
- Tagging and Versioning
- Deleting Files from History (`git rm`)
- `.gitattributes`
  - Configuring end-of-line normalization
  - Setting file attributes
- `.gitignore`
  - Excluding files and directories from version control
- `.gitmodules`
  - Managing repositories within repositories (Submodules)

---

## 📋 6. Backup and Recovery — Planned

- Recovering Deleted Commits (`git reflog`)
- Recovering Deleted Files
- Techniques to Avoid Accidental Data Loss

## 📋 7. Logs and History — Planned

- Viewing Logs with `git log`
- Filtering History (`git log`, `git reflog`)

---

## 📋 8. Workflows — Planned

- Gitflow Workflow Overview
- Trunk-Based Development
- Pull Request Workflow

## 📋 9. Git Security Best Practices — Planned

- Managing Secrets (e.g., `.env` files)
- Avoiding Sensitive Data in Commits
- Cleaning History of Sensitive Data (e.g., using `git filter-repo`)

---

## 📋 10. Cheat Sheets — Planned

- Markdown Cheat Sheet
- Git Command Cheat Sheet

## 📋 11. Performance Optimization — Planned

- Large File Handling (`git lfs`)
- Optimizing Repository Size (`git gc`, `.gitattributes`)

---

## 📋 12. Automation — Planned

- Git Hooks
  - Automating tasks with hooks (e.g., pre-commit hooks)

## 📋 13. Troubleshooting and Best Practices — Planned

- Resolving Merge Conflicts
- Verifying SSH Information
- Cleaning Up Commit History (Squash, Rebase)
- Common Errors and Solutions

---
