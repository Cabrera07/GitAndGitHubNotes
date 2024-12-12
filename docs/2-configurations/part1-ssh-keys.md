# 🛠 Configurations and Setup (Part I)

## 🔑 SSH Keys: Generate, Add, and Verify SSH Information

**SSH keys** provide a secure way to authenticate with GitHub without using passwords. They consist of a pair of keys: one public and one private.

---

### 🚀 How Do SSH Keys Work?

**SSH keys function like a pair of digital keys:**

1. **Private Key** (🔒 like your house key):
   - Stays on your computer.
   - Never shared.
   - Acts as your personal key.

2. **Public Key** (🔓 like your house lock):
   - Shared with services like GitHub.
   - Safe to share publicly.
   - Works like giving a copy of your lock.

**Here’s how it works:**

- GitHub holds your **public key (lock)**.
- Your computer uses the **private key (key)**.
- If they match, you’re authenticated securely.

```bash
You: "Hi GitHub, it's me" (using your private key).
GitHub: "Let me verify with your public key... yes, it's you. Welcome!"
```

---

### 🌟 Advantages of SSH Keys

- 🔐 **Secure:** More secure than passwords.
- 🕒 **Convenient:** No need to enter your password every time.
- 🔑 **Flexible:** Revoke access per device, like changing a lock.
- 📱 **Device-Specific:** Each device can have its own key.

---

## ⚙️ Basic Setup

### 1️⃣ ***Check Existing SSH Keys***

- ***Run the following command to see if you already have SSH keys:***

    ```bash
    ls -la ~/.ss
    ```

    > 🔎 **Nota:**
    > - Busca archivos con los nombres: `id_rsa.pub`, `id_ecdsa.pub` o `id_ed25519.pub`.

---

### 2️⃣ Generate a New SSH Key

- **If no keys exist, generate a new one (`Ed25519` is recommended):**

    ```bash
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```

    > 🔎 **Nota:**
    > - ***During the process:***
    >
    >   - Press **Enter** to save it in the default location.
    >   - Set a **passphrase** for added security (optional but recommended).
    >

---

### 3️⃣ Start the SSH Agent

- **Start the SSH agent in the background and add your private key**:

    ```bash
    # Start the agent
    eval "$(ssh-agent -s)"

    # Add the private key
    ssh-add ~/.ssh/id_ed25519
    ```

---

### 4️⃣ Copy the Public Key

- **Depending on your operating system, copy the public key:**
  - ***macOS:***

    ```bash
    pbcopy < ~/.ssh/id_ed25519.pub
    ```

  - ***Linux:***

    ```bash
    cat ~/.ssh/id_ed25519.pub
    # Copy the displayed output manually.
    ```

  - ***Windows (Git Bash):***

    ```bash
    clip < ~/.ssh/id_ed25519.pub
    ```

---

### 5️⃣ Add the Key to GitHub

  1. Go to **GitHub.com → Settings → SSH and GPG keys**.
  2. Click "**New SSH Key**".
  3. Add a descriptive title (e.g., "Personal Laptop").
  4. Paste your **public key** into the key field.
  5. Click "**Add SSH Key**".

---

### 6️⃣ Test the Connection

- **Verify that your key is working with GitHub:**
  
    ```bash
    ssh -T git@github.com
    ```

- **If successful, you’ll see:**

    ```bash
    Hi username! You've successfully authenticated...
    ```

---

### 7️⃣ Usage Example

- **Clone a Repository Using SSH:**

    ```bash
    git clone git@github.com:username/repository.git
    ```

- **Set an Existing Remote to Use SSH:**

    ```bash
    git remote set-url origin git@github.com:username/repository.git
    ```

---

### 🔧 Common Troubleshooting

- If you see **"Permission denied"**, ensure:
  - You’re using the SSH URL **`(git@github.com:username/repo.git)`**
  - Your key is properly added to the **ssh-agent**
  - Your public key is added to your GitHub account.
- If you lose your private key, delete the public key from GitHub and create a new key pair.

---

## ⚙️ SSH Key Configuration for Multiple Machines

### 🔵 Windows Configuration

1. **Open Git Bash and check for existing keys:**

    ```bash
    ls -la ~/.ssh
    ```

2. **Generate a new SSH key for Windows:**

    ```bash
    # Create a key with a descriptive name
    ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/id_ed25519_window
    ```

3. **Add the key to the SSH agent and copy the public key:**

    ```bash
    # Start the ssh-agent
    eval "$(ssh-agent -s)"

    # Add the key
    ssh-add ~/.ssh/id_ed25519_windows

    # Copy the public key
    clip < ~/.ssh/id_ed25519_windows.pub
    ```

---

### 🟢 Linux Configuration

1. **Check for existing keys:**

    ```bash
    ls -la ~/.ssh
    ```

2. **Generate a new SSH key for Linux:**

    ```bash
    # Create a key with a descriptive name
    ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/id_ed25519_linux
    ```

3. **Add the key to the SSH agent and copy the public key:**

    ```bash
    # Start the ssh-agent
    eval "$(ssh-agent -s)"

    # Add the key
    ssh-add ~/.ssh/id_ed25519_linux

    # Copy the public key
    cat ~/.ssh/id_ed25519_linux.pub
    # Manually copy the output
    ```

---

### 🔑 Add Keys to GitHub

- **For each machine, go to GitHub → Settings → SSH and GPG keys and:**
  - Add the Windows key with a descriptive title like "Windows - [PC Name]".
  - Add the Linux key with a title like "Linux - [PC Name]".

---

### 🔗 Test Connection

- ***Windows Configuration:***

  ```bash
    ssh -T git@github.com
    ```  

- ***Linux Configuration:***

  ```bash
    ssh -T git@github.com
    ```

---

### 🔧 Configuring the SSH config File (Optional)

- **To simplify using multiple keys, configure your `~/.ssh/config file`:**

  - ***Windows Configuration:***

  ```bash
    Host github.com-windows
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_windows
    ```  

  - ***Linux Configuration:***

  ```bash
    # Linux Configuration
    Host github.com-linux
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_linux
    ```
  
---

### 📆 Daily Usage

```bash
# Clone repositories using SSH
git clone git@github.com:username/repository.git

# Change an existing remote to SSH
git remote set-url origin git@github.com:username/repository.git
```

---

### 🔐 Security Tips

- Use different keys for each machine.
- Keep private keys secure and never share them.
- Use unique passphrases for each key.
- If a machine is compromised, you only need to revoke the specific key.

---

## 🔑 Configuring Multiple GitHub Accounts (Personal and Work)

Managing multiple GitHub accounts (e.g., personal and work) requires setting up separate SSH keys and configuring Git to use them seamlessly. Follow these steps:

---

### 1️⃣ **Create Different SSH Keys**

- **Generate separate SSH keys for personal and work accounts:**

    ```bash
    # Generate key for personal account
    ssh-keygen -t ed25519 -C "personal@email.com" -f ~/.ssh/id_ed25519_personal

    # Generate key for work account
    ssh-keygen -t ed25519 -C "work@company.com" -f ~/.ssh/id_ed25519_work
    ```

---

### 2️⃣ Add the Keys to the SSH Agent

- **Start the SSH agent and add both keys:**

    ```bash
    # Start ssh-agent
    eval "$(ssh-agent -s)"

    # Add personal key
    ssh-add ~/.ssh/id_ed25519_personal

    # Add work key
    ssh-add ~/.ssh/id_ed25519_work
    ```

---

### 3️⃣ Configure the `~/.ssh/config` File

- **Set up a configuration file to manage keys for each account:**

    ```bash
    # Personal Account
    Host github.com-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_personal

    # Work Account
    Host github.com-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_work
    ```

---

### 4️⃣ Add Public Keys to GitHub

#### 🔵 **For Personal Account:**

  1. Copy the personal key:

      ```bash
      cat ~/.ssh/id_ed25519_personal.pub
      ```

  2. Go to ***GitHub → Settings → SSH Keys***.
  3. Click "***New SSH Key***".
  4. Add the key with a title like "***Personal Machine***".

#### 🟢 **For Work Account:**

  1. Copy the personal key:

      ```bash
      cat ~/.ssh/id_ed25519_work.pub
      ```

  2. Go to ***GitHub → Settings → SSH Keys***.
  3. Click "***New SSH Key***".
  4. Add the key with a title like "***Work Machine***".

---

### 5️⃣ Configure Git for Each Repository

#### 🔵 **For Personal:**

- ***Set the global configuration for your personal account (optional):***

    ```bash
    git config --global user.name "Personal Name"
    git config --global user.email "personal@email.com"
    ```

- ***Clone or update repositories to use the personal account:***

    ```bash
    # Clone a personal repository
    git clone git@github.com-personal:personal-username/repo.git

    # Update an existing repository
    git remote set-url origin git@github.com-personal:personal-username/repo.git
    ```

#### 🟢 **For Work:**

- ***Configure each work repository locally::***

    ```bash
    # Set repository-specific configuration
    cd /path/to/work/repo
    git config user.name "Work Name"
    git config user.email "work@company.com"
    ```

- ***Clone or update repositories to use the work account::***

    ```bash
    # Clone a work repository
    git clone git@github.com-work:work-username/repo.git

    # Update an existing repository
    git remote set-url origin git@github.com-work:work-username/repo.git
    ```

---

### 6️⃣ Verify Connections

- ***Test each connection to ensure they are properly configured:***

    ```bash
    # Test personal connection
    ssh -T git@github.com-personal

    # Test work connection
    ssh -T git@github.com-work
    ```

---

### 🗂 Recommended Directory Structure

```javascript
~/Projects/
    ├── personal/
    │   ├── repo1/
    │   └── repo2/
    └── work/
        ├── repo1/
        └── repo2/
```

---

### 💡 Tips and Best Practices

1. **Check Repository Configuration**

    ```bash
    # Inside each repository, check the configuration
    git config --list
    ```

2. **Useful Aliases for .bashrc or .zshrc**

    ```bash
    alias git-personal='git config user.name "Personal Name" && git config user.email "personal@email.com"'
    alias git-work='git config user.name "Work Name" && git config user.email "work@company.com"'
    ```

3. **Verify Remote URL**

    ```bash
    git remote -v
    ```

4. **Troubleshooting**

   - If you see "**Permission denied**", ensure:
     - You're using the correct host (`github.com-personal` or `github.com-work`).
     - Your keys are added to the SSH agent: `ssh-add -l`.
     - File permissions are correct: `ls -la ~/.ssh/`.
   - If a key is compromised, delete it from GitHub and create a new one.
