---

## 🧩 Bandit Level 0 → Level 1

### 🎯 Goal:
> The password for the next level is stored in a file called `readme` located in the home directory.

### 🛠️ Tools Used:
- `ssh`
- `ls`, `cat`

### 📜 Steps:
1. Connect to the server using SSH:
   ```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220
   
You'll be prompted for the password: bandit0

2. List files in the home directory:
   ```bash
   ls
3. Read the file named readme:
   ```bash
   cat readme
4. Copy the output that's the password for the next level.
