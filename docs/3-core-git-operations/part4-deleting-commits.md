# 🗑️ **Deleting Commits**

Sometimes rewinding one commit at a time (like in [Undoing Changes](./part3-undoing-changes.md)) isn't enough — you need to **remove specific commits from the middle of your history**, not just the most recent one. Think of your commit history as a **stack of pancakes** 🥞: `reset` only lets you take pancakes off the top, but sometimes the burnt one is in the middle of the stack.

---

## 📖 **Two Ways to Delete Commits**

| 🛠️ **Tool** | 🎯 **Best for** | ⚠️ **Rewrites history?** |
| --- | --- | --- |
| `git reset` | Deleting the **most recent** commit(s) | ✅ Yes |
| `git rebase -i` (interactive rebase) | Deleting a commit **anywhere** in history | ✅ Yes |

Both rewrite commit hashes after the deleted commit, so the same sharing rule applies as in [Undoing a Push](./part3-undoing-changes.md#-step-4-undo-a-push): **safe on private branches, dangerous on shared ones.**

---

## 🎯 **Deleting the Most Recent Commit(s)**

If the commit(s) you want gone are at the **tip** of your branch, `git reset --hard` is the simplest tool:

```bash
git reset --hard HEAD~1
```

> 🗃️ **Analogy:** taking the **top pancake** off the stack — easy, because nothing is stacked on top of it.

For deleting the last 3 commits:

```bash
git reset --hard HEAD~3
```

---

## 🎯 **Deleting a Commit in the Middle of History**

This is where **interactive rebase** comes in — it lets you rewrite a *range* of commits, including dropping specific ones out of the middle.

---

### ✏️ **Example: Drop a Commit Three Commits Back**

```bash
git rebase -i HEAD~3
```

This opens an editor listing the last 3 commits:

```bash
pick a1b2c3d feat(cart): add quantity selector
pick e4f5g6h fix(cart): correct rounding bug
pick i7j8k9l chore(cart): remove debug console.log
```

To **delete** the middle commit, either delete its line entirely or change `pick` to `drop`:

```bash
pick a1b2c3d feat(cart): add quantity selector
drop e4f5g6h fix(cart): correct rounding bug
pick i7j8k9l chore(cart): remove debug console.log
```

Save and close the editor — Git replays the remaining commits **without** the dropped one.

> 🗃️ **Analogy:** you're not taking the top pancake off, you're **carefully sliding the burnt one out of the middle** and restacking the rest on top of each other.

---

## ⚠️ **Watch Out For Conflicts**

If the dropped commit's changes were touched by a **later commit**, Git may pause the rebase with a conflict — it doesn't know how to reapply the later change without the context of the one you removed.

```bash
# Git pauses and shows the conflicting file(s)
git status                 # see what needs resolving
# ...edit the file(s) to resolve the conflict...
git add <resolved-file>
git rebase --continue
```

> [!TIP]
> If it gets too messy, you can always back out safely:
>
> ```bash
> git rebase --abort
> ```
>
> This returns your branch to the exact state it was in before the rebase started.

---

## 🛠️ **Troubleshooting**

> [!TIP]
>
> - **"I don't know which commit hash to target."** Run `git log --oneline` first — it lists commits with their short hashes, newest at the top.
> - **"I dropped a commit by accident."** As long as you haven't run `git gc`, the commit likely still exists — check `git reflog` to find its hash and `git cherry-pick <hash>` it back in.
> - **"The rebase is stuck on a conflict I can't resolve."** Run `git rebase --abort` to cancel safely and try again with a clearer plan (e.g., resolve dependent commits first).
> - **"Can I do this on a branch my team already pulled?"** Avoid it. Rewriting shared history forces everyone else to reconcile their local copy. Prefer `git revert` for shared branches.

---

## 🌟 **Key Takeaways**

- Deleting the **most recent** commit(s): `git reset --hard HEAD~N`.
- Deleting a commit **anywhere else** in history: interactive rebase (`git rebase -i`) and change `pick` to `drop`.
- Both methods rewrite commit hashes — treat them like `--force` push territory: **private branches only**, unless the whole team agrees.
- `git rebase --abort` is your safety exit if a rebase goes wrong mid-way.

---
