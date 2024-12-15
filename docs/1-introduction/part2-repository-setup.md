# 🏁 Repository Setup

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

---
