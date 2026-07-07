# ⚙️ Core Git Operations Section Overview

Welcome to the **Core Git Operations** section of the Git and GitHub notes repository! This section covers the everyday commands you'll use constantly once your repository is set up — staging, committing, undoing mistakes, and understanding Git's less obvious states.

***The Core Git Operations section covers the following topics:***

- Staging and committing changes.
- Writing clear, standardized commit messages (Conventional Commits).
- Undoing changes at every stage — unstaged, staged, committed, and even pushed.
- Deleting commits from anywhere in your history.
- Recovering from a detached HEAD state.

---

## 📋 Table of Contents

- [⚙️ Core Git Operations Section Overview](#️-core-git-operations-section-overview)
  - [📋 Table of Contents](#-table-of-contents)
  - [🛠️ How to Use This Section](#️-how-to-use-this-section)
  - [🚀 Staging and Committing Changes](#-staging-and-committing-changes)
  - [🏷️ Conventional Commits](#️-conventional-commits)
  - [⏪ Undoing Changes](#-undoing-changes)
  - [🗑️ Deleting Commits](#️-deleting-commits)
  - [🧭 Handling a Detached HEAD State](#-handling-a-detached-head-state)
  - [🌟 Additional Notes](#-additional-notes)

---

## 🛠️ How to Use This Section

1. Start with **Staging and Committing Changes** to understand the basic save workflow.
2. Move to **Conventional Commits** to write commit messages that are actually useful later.
3. Read **Undoing Changes** before you need it — it covers everything from a single unstaged edit to a commit you already pushed.
4. Use **Deleting Commits** when you need to remove something from further back in your history than a simple undo reaches.
5. Keep **Handling a Detached HEAD State** handy for the moment Git warns you about it — it's not dangerous, but it is confusing the first time.

---

## 🚀 Staging and Committing Changes

- **File**: [Part 1: Staging and Committing Changes](./part1-staging-and-committing-changes.md)
- **Summary**: The foundation of every Git workflow — preparing changes with `git add` and saving them as snapshots with `git commit`.
- **Highlights**:
  - 📚 The "book editor" analogy for staging and committing.
  - 😎 Shortcuts like `git commit -am`.

---

## 🏷️ Conventional Commits

- **File**: [Part 2: Conventional Commits](./part2-conventional-commits.md)
- **Summary**: A standard format for commit messages (`type(scope): description`) that makes your history readable and automation-friendly.
- **Highlights**:
  - 🧩 A table of common commit types (`feat`, `fix`, `docs`, `chore`, etc.).
  - ⚠️ How to flag breaking changes.

---

## ⏪ Undoing Changes

- **File**: [Part 3: Undoing Changes](./part3-undoing-changes.md)
- **Summary**: Covers the full spectrum of "oops" — from `git restore` for uncommitted edits, to `git reset` for committed ones, to `git revert` and force-pushing for changes you already shared.
- **Highlights**:
  - 🚦 A soft/mixed/hard comparison table for `git reset`.
  - 🛟 The safe way to undo a pushed commit vs. the risky way.

---

## 🗑️ Deleting Commits

- **File**: [Part 4: Deleting Commits](./part4-deleting-commits.md)
- **Summary**: What to do when the commit you need gone isn't the most recent one — interactive rebase and dropping commits from the middle of your history.
- **Highlights**:
  - 🥞 The "pancake stack" analogy for rewriting history.
  - ⚠️ How to resolve conflicts mid-rebase, and how to bail out with `git rebase --abort`.

---

## 🧭 Handling a Detached HEAD State

- **File**: [Part 5: Handling a Detached HEAD State](./part5-detached-head-state.md)
- **Summary**: Demystifies the "detached HEAD" warning — what it means, when it's harmless, and how to rescue commits made while detached.
- **Highlights**:
  - 📍 The "sticky note on a notebook page" analogy for `HEAD`.
  - 🛟 How to turn a detached commit into a real branch before it's lost.

---

## 🌟 Additional Notes

- This section is part of a larger repository of Git and GitHub notes. Check the root [README](../../README.md) for the complete structure, and [ROADMAP.md](../../ROADMAP.md) for what's planned next.
- Feedback and contributions are welcome! Feel free to raise an issue or submit a pull request if you spot something to improve.

---
