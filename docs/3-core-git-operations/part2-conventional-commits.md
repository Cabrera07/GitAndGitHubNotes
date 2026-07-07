# 🏷️ **Conventional Commits**

Imagine every commit message is a **shipping label** on a package. 📦  
If the label just says *"stuff"*, nobody at the warehouse knows what's inside, where it goes, or whether it's fragile. **Conventional Commits** are a standard label format so anyone (including future you) can read a commit message and instantly know **what changed and why**.

---

## 📖 **What Is a Conventional Commit?**

A **Conventional Commit** follows this structure:

```bash
<type>(<scope>): <short description>
```

- **`type`** — what kind of change this is (`feat`, `fix`, `docs`, etc.).
- **`scope`** *(optional)* — the part of the project affected (e.g., `auth`, `api`, `configurations`).
- **`short description`** — a concise summary, written in the present tense (*"add"*, not *"added"*).

```bash
git commit -m "feat(auth): add password reset flow"
```

> 🗃️ **Analogy:**
>
> - `type` = the **category** stamped on the shipping label (fragile, perishable, priority).
> - `scope` = the **department** it's headed to (kitchen, warehouse, front desk).
> - `description` = the **one-line note** explaining what's inside.

---

## 🧩 **Common Types**

| 🏷️ **Type** | 💬 **Meaning** | 🧪 **Example** |
| --- | --- | --- |
| `feat` | A new feature | `feat(cart): add quantity selector` |
| `fix` | A bug fix | `fix(login): correct password validation` |
| `docs` | Documentation only changes | `docs(readme): update installation steps` |
| `style` | Formatting, no logic change (spacing, semicolons) | `style(button): fix indentation` |
| `refactor` | Code change that neither fixes a bug nor adds a feature | `refactor(api): simplify request handler` |
| `test` | Adding or correcting tests | `test(auth): add login unit tests` |
| `chore` | Maintenance tasks (deps, configs, tooling) | `chore(deps): bump react to v18` |

---

## ✏️ **Example 1: A Simple Feature Commit**

You added a search bar to your app:

```bash
git commit -m "feat(search): add search bar to navbar"
```

---

## ✏️ **Example 2: A Bug Fix With Scope**

You fixed a crash when submitting an empty form:

```bash
git commit -m "fix(form): prevent crash on empty submission"
```

---

## ✏️ **Example 3: A Breaking Change**

Sometimes a change **breaks backward compatibility** — for example, renaming a public API endpoint. Mark it with `!` after the type/scope, and explain it in the body:

```bash
git commit -m "feat(api)!: rename /users endpoint to /accounts

BREAKING CHANGE: /users no longer exists, use /accounts instead."
```

> [!IMPORTANT]
>
> - The `!` is a **loud warning label**: *"careful, this box is not compatible with the old shelf."*
> - The `BREAKING CHANGE:` footer explains exactly what broke.

---

## 🍳 **Example Workflow: Building a Recipe App**

1. 🥕 You add the recipe form:

    ```bash
    git commit -m "feat(recipes): add recipe creation form"
    ```

2. 🐛 You notice the form doesn't validate empty titles, so you fix it:

    ```bash
    git commit -m "fix(recipes): require a title before saving"
    ```

3. 📝 You update the docs to mention the new form:

    ```bash
    git commit -m "docs(recipes): document the recipe creation form"
    ```

> 🗃️ **Analogy Recap:**
>
> Each commit is its own labeled package — anyone unpacking your project's history knows exactly which box to open for what.

---

## 🌟 **Why Conventional Commits Matter**

- 📚 **Readable history:** `git log --oneline` reads like a changelog instead of a guessing game.
- 🤖 **Automation-friendly:** tools can auto-generate changelogs or bump version numbers (`fix` → patch, `feat` → minor, `BREAKING CHANGE` → major) based on your commit types.
- 🤝 **Team clarity:** collaborators instantly understand the *intent* behind a change without opening the diff.

---

## 🛠️ **Troubleshooting**

> [!TIP]
>
> - **"I don't know which type to use."** Ask: *does this change what the user experiences (`feat`/`fix`), or just the internals (`refactor`/`chore`/`style`)?*
> - **"My commit touches multiple types of changes."** Split it into separate commits — one label per package keeps the shipment organized.
> - **"I forgot the format on a past commit."** That's fine — Conventional Commits are a convention, not a Git requirement. Start applying it from your next commit onward.

---

## 🌟 **Key Takeaways**

- Format: `type(scope): description`.
- Common types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
- Use `!` and a `BREAKING CHANGE:` footer for backward-incompatible changes.
- The payoff is a commit history that reads like a clear, automatable changelog.

---
