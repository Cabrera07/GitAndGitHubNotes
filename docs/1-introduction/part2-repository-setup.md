# 🏁 Repository Setup

## 📋 Table of Contents

- [🏁 Repository Setup](#-repository-setup)
  - [📋 Table of Contents](#-table-of-contents)
  - [🌎 **Create a New Remote Repository**](#-create-a-new-remote-repository)
  - [🌐 **Using HTTPS**](#-using-https)
  - [🔒 **Using SSH**](#-using-ssh)
  - [🛠️ **Common Pitfalls and Solutions**](#️-common-pitfalls-and-solutions)

---

## 🌎 **Create a New Remote Repository**

1. **On GitHub (or another git hosting service):**
   - Go to the hosting service’s website.
   - Click on the **"New"** repository button.
   - Provide a repository name (e.g., `repository`).
   - Optionally add a description.
   - Choose visibility (Public/Private).
   - Click **"Create repository"**.  

> [!NOTE]
> You will be provided with a remote URL. Keep this URL handy for the next steps.

---

## 🌐 **Using HTTPS**

1. **Initialize the Local Repository:**

    ```bash
    mkdir new-repository
    cd new-repository
    git init
    ```

2. **Add the Remote Repository:**

    ```bash
    git remote add origin https://github.com/username/repository.git
    ```

3. **Add files, commit, and push to the remote repository:**

    ```bash
    git add README.md
    git commit -m "Initial commit"
    git push -u origin main
    ```

> [!NOTE]
> **🌐 When to Use HTTPS:** This method is straightforward and requires no additional setup but may prompt you to enter credentials for each push or pull unless you configure a credential manager.

---

## 🔒 **Using SSH**

1. **Initialize the Local Repository:**

    ```bash
    mkdir new-repository
    cd new-repository
    git init
    ```

2. **Add the Remote Repository:**

    ```bash
    git remote add origin git@github.com:username/repository.git
    ```

3. **Add files, commit, and push to the remote repository:**

    ```bash
    git add README.md
    git commit -m "Initial commit"
    git push -u origin main
    ```

> [!NOTE]
> **🔒 When to Use SSH:** This method is ideal for frequent interactions, as it eliminates the need for repeated credential entry after the initial SSH key setup.

---

## 🛠️ **Common Pitfalls and Solutions**

- **🐛 Problem:** Forgot to add the remote repository.
  - **🔧 Solution:** Add it using the correct remote URL

    ```bash
    git remote add origin <remote-url>
    ```

- **🐛 Problem:** Pushed to the wrong branch.
  - **🔧 Solution:** Switch to the correct branch and push again

    ```bash
    git checkout main
    git push -u origin main
    ```

- **🐛 Problem:** Credentials prompted repeatedly with HTTPS.
  - **🔧 Solution:** Set up a credential helper:

    ```bash
    git config --global credential.helper store
    ```

> [!NOTE]
> These tips ensure a smooth setup and help avoid common mistakes during repository initialization and configuration.

---
