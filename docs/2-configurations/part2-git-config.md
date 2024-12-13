# 🛠 Configurations and Setup (Part II)

## 🔧 Git Configuration Commands (`git config`)

**Git configuration helps you personalize and streamline your workflow. Here are some examples:**

---

### 1️⃣ Tell Git Your Name and Email

- **Set your name and email globally to tag all your commits with this identity:**

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "yourname@example.com"
    ```

    > 💡 **What it does:**
    > - When you make commits (save points in your project), Git will tags them with your name and email so collaborators know who made the changes.

---

### 2️⃣ Choose Your Favorite Text Editor

- **Tell Git which text editor to use for writing commit messages:**

    ```bash
    git config --global core.editor "code --wait"
    ```

    > 💡 **What it does:**
    > - Opens your favorite editor (e.g., VS Code) for commit messages. The `--wait` flag ensures Git pauses until you finish typing.

- **Examples:**
  
  - ***Use Vim:***
  
    ```bash
    git config --global core.editor "vim"
    ```

  - ***Use Notepad (Windows):***
  
    ```bash
      git config --global core.editor "notepad"
    ```

---

### 3️⃣ Handle Line Endings (Windows vs. Linux )

- **Line endings differ between operating systems. Git can automatically handle these differences for you:**

    ```bash
    git config --global core.autocrlf true
    ```

    > 💡 **What it does:**
    > - Ensures that:
    >   - Windows uses \r\n for line endings.
    >   - Linux/Mac uses \n.
    > - Git converts line endings as needed to avoid conflicts.

---

### 4️⃣ See All Your Git Settings

- **Want to review your current Git configuration? Use:**

    ```bash
    git config --list
    ```

    > 💡 **What it does:**
    > - Displays a list of all configured settings, such as your name, email, editor, aliases, etc.

---

### 5️⃣ Set Configurations for Just One Project

- **Sometimes, you want to apply settings only to a specific project:**

    ```bash
    git config user.name "Project Hero"
    git config user.email "projecthero@example.com"
    ```

    > 💡 **What it does:**
    > - Ensures that:
    >   - Overrides global settings for the current project directory only.
    >   - Other projects still use the global configuration.

---

### 6️⃣ Create Aliases (Nicknames for Commands)

- **Shorten frequently used Git commands by setting aliases:**

    ```bash
    git config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    ```

    > 💡 **What it does:**
    > - Instead of typing full commands like `git status`, you can use shortcuts:
    >
    >   ```bash
    >   git st   # Instead of git status
    >   git co   # Instead of git checkout
    >   git br   # Instead of git branch
    >   ```
    >
    > - It’s like giving Git commands a nickname to save time!

---

### 7️⃣ Undo Mistakes (Unset a Configuration)

- **Did you make a mistake in your configuration? Don’t worry, you can unset it:**

    ```bash
    git config --global --unset user.email
    ```

    > 💡 **What it does:**
    > - Removes the specified configuration (in this case, user.email).

---

### 8️⃣ Reset All Configurations

- **To remove all global configurations, you can delete the Git config file:**

    ```bash
    rm ~/.gitconfig
    ```

    > ⚠️ **Warning**  
    > Use this carefully! It will reset all global settings.

---

### 🎁 Bonus: Useful Aliases for Productivity

- **Here are some handy aliases you can add for better productivity:**
  
    ```bash
    git config --global alias.last "log -1 HEAD"        # View the last commit
    git config --global alias.unstage "reset HEAD --"  # Undo staging
    git config --global alias.lg "log --oneline --graph --decorate"  # View log as a graph
    ```

- **Examples:**
  
  - ***View the last commit:***
  
    ```bash
    git last
    ```

  - ***Undo staging:***
  
    ```bash
    git unstage file.txt
    ```

  - ***Undo staging:***
  
    ```bash
    git lg
    ```

---

## 📝 Summary of Key Commands

| **Command**                          | **Description**                                   |
|--------------------------------------|--------------------------------------------------|
| `git config --global user.name`      | 🧑 Set your name globally.                       |
| `git config --global user.email`     | 📧 Set your email globally.                      |
| `git config --global core.editor`    | ✏️ Set your preferred text editor.               |
| `git config --global core.autocrlf`  | 🔄 Handle line endings automatically.            |
| `git config --list`                  | 📜 View all current Git configurations.          |
| `git config user.name`               | 🧑 Set project-specific name.                    |
| `git config user.email`              | 📧 Set project-specific email.                   |
| `git config --global alias.<alias>`  | ⚡ Create a shortcut for a Git command.          |
| `git config --global --unset <key>`  | 🗑️ Remove a specific Git configuration.          |
