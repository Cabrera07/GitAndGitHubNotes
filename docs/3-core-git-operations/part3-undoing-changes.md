# ⏪ **Undoing Changes in Git**

Everyone makes mistakes — Git just gives you a **rewind button** for almost every stage of your work. 🕹️  
Think of your project like a **video game save file**: sometimes you want to reload an old save (`reset`), sometimes you just want to undo the last move on the board without touching your saves (`restore`), and sometimes you already uploaded your progress and need to correct it (`undo a push`).

---

## 🎯 **Step 1: Undo Unstaged/Staged Changes with `git restore`**

`git restore` is for **"I haven't committed yet, just give me back the last saved version of this file."**

---

### ✏️ **Example 1: Discard Changes in the Working Directory**

You edited `index.html` and want to throw those edits away:

```bash
git restore index.html
```

> 🗃️ **Analogy:** it's like **erasing your pencil marks** and going back to the last inked page.

---

### ✏️ **Example 2: Unstage a File (Keep the Edits)**

You ran `git add file.txt` by accident but still want to keep your edits, just not staged:

```bash
git restore --staged file.txt
```

> 💡 **What it does:** takes the file **out of the envelope** (staging area) without deleting your work.

---

## 🎯 **Step 2: Rewind Commits with `git reset`**

`git reset` moves your branch **pointer** to an earlier commit. How much of your work survives depends on the flag you use.

| 🚦 **Mode** | 💻 **Command** | 🧳 **What happens to your changes** |
| --- | --- | --- |
| 🟢 **Soft** | `git reset --soft <commit>` | Commits are undone, but changes stay **staged**. |
| 🟡 **Mixed** *(default)* | `git reset <commit>` | Commits are undone, changes stay in your working directory, **unstaged**. |
| 🔴 **Hard** | `git reset --hard <commit>` | Commits **and** changes are **permanently discarded**. |

> 🗃️ **Analogy:**
>
> - **Soft** = you take the sealed envelopes back out of the mailbox, but they're still packed and ready to reseal.
> - **Mixed** = you unpack the envelopes too — the pages are back on your desk.
> - **Hard** = you shred the pages entirely. 🔥

---

### ✏️ **Example 1: Undo the Last Commit but Keep the Changes Staged**

```bash
git reset --soft HEAD~1
```

Useful when you want to **redo the commit message** or combine it with more changes before recommitting.

---

### ✏️ **Example 2: Undo the Last Commit and Unstage Everything**

```bash
git reset HEAD~1
```

Your files go back to being **modified but unstaged**, as if you'd never run `git add` or `git commit`.

---

### ✏️ **Example 3: Wipe the Last Commit Completely**

```bash
git reset --hard HEAD~1
```

> [!IMPORTANT]
>
> - This **deletes your changes** — there is no staging area or working directory copy left.
> - Only use `--hard` when you are **certain** you don't need those changes. If the commit still exists in Git's history (i.e., you haven't garbage-collected), `git reflog` can sometimes still recover it — see the planned "Recovering Deleted Commits" topic in the project's `ROADMAP.md` for that safety net in more depth.

---

## 🎯 **Step 3: Undo a Commit Message with `git commit --amend`**

Made a typo in your last commit message, or forgot to include a file? `--amend` lets you **edit the last commit** instead of creating a new one.

---

### ✏️ **Example 1: Fix the Last Commit Message**

```bash
git commit --amend -m "fix(login): correct password validation"
```

---

### ✏️ **Example 2: Add a Forgotten File to the Last Commit**

```bash
git add forgotten-file.txt
git commit --amend --no-edit
```

> 💡 **`--no-edit`** keeps the original commit message unchanged — you're only adding the file to the same snapshot.

> [!IMPORTANT]
>
> - `--amend` **rewrites** the last commit (a new commit hash is created). Never amend a commit that's **already been pushed and shared** with others — it rewrites history they may already depend on.

---

## 🎯 **Step 4: Undo a Push**

You already pushed a commit to the remote and need to walk it back. The safe approach depends on whether **others have already pulled** that commit.

---

### ✏️ **Option 1: Revert (Safe for Shared Branches)**

`git revert` creates a **new commit** that undoes the changes of a previous one, instead of erasing history:

```bash
git revert <commit-hash>
git push origin branch-name
```

> 🗃️ **Analogy:** instead of tearing a page out of a shared notebook, you **add a new page** that says *"ignore page 12, here's the correction."* Everyone's copy of the notebook stays intact and in sync.

---

### ✏️ **Option 2: Reset + Force Push (Only on Private/Solo Branches)**

```bash
git reset --hard HEAD~1
git push --force origin branch-name
```

> [!IMPORTANT]
>
> - `--force` **rewrites remote history**. If anyone else has pulled the branch, their local history will conflict with yours.
> - Only do this on a **branch nobody else is using** (e.g., a personal feature branch you haven't shared yet).

---

## 🔄 **Quick Reference**

| 🎯 **Goal** | 💻 **Command** |
| --- | --- |
| Discard uncommitted edits in a file | `git restore <file>` |
| Unstage a file (keep edits) | `git restore --staged <file>` |
| Undo commit, keep changes staged | `git reset --soft HEAD~1` |
| Undo commit, keep changes unstaged | `git reset HEAD~1` |
| Undo commit and discard changes | `git reset --hard HEAD~1` |
| Fix the last commit message/content | `git commit --amend` |
| Undo a pushed commit (shared branch) | `git revert <commit-hash>` |
| Undo a pushed commit (private branch) | `git reset --hard` + `git push --force` |

---

## 🛠️ **Troubleshooting**

> [!TIP]
>
> - **"I ran `--hard` and lost my changes!"** Check `git reflog` — Git keeps a history of where `HEAD` has been, and you can often recover the "lost" commit from there.
> - **"I amended a commit I already pushed and now `git push` is rejected."** That rejection is Git protecting the shared history. Don't force-push over a shared branch — coordinate with your team, or use `git revert` instead.
> - **"Should I use `reset` or `revert`?"** If the commit is only local, `reset` is fine. If it's already pushed and others may have it, use `revert`.

---

## 🌟 **Key Takeaways**

- `git restore` = undo changes that **aren't committed yet**.
- `git reset --soft/--mixed/--hard` = rewind commits, with increasing levels of "no going back."
- `git commit --amend` = fix the **last** commit's message or contents.
- `git revert` = the safe way to undo a **pushed, shared** commit.
- `git reset --hard` + `--force` push = only for commits **nobody else has**.

---
