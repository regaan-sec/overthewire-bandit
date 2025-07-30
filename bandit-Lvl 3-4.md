# Bandit Level 3 to Level 4

## Objective
The password for the next level is stored in a hidden file within the `inhere` directory.

## Tools Used
* `ssh`: Secure Shell client.
* `ls`: List directory contents.
* `cd`: Change directory.
* `cat`: Concatenate and display file content.

## Concepts Learned
* Directory navigation using the `cd` command.
* Identifying hidden files in Linux (those starting with a `.`).
* Using the `ls -a` option to display all files, including hidden ones.

## My Approach & Thought Process
The challenge mentioned a "hidden file" and a directory named `inhere`. In Linux, hidden files are conventionally named starting with a dot (`.`). By default, the `ls` command does not show these files. My plan was to first navigate into the `inhere` directory using `cd`, and then use `ls` with the `-a` (all) option to reveal any hidden files. This quickly showed a file named `.hidden`. Once identified, `cat` was used to retrieve its contents.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit3@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:** Connect to the `bandit3` user account.
    * **Input Password (when prompted):** `[PASSWORD_FROM_PREVIOUS_LEVEL]`
    * **Screenshot:** (Optional)

2.  **Change directory into `inhere`:**
    ```bash
    cd inhere
    ```
    * **Explanation:** The `cd` command changes the current working directory to the specified path, which in this case is `inhere`.
    * **Screenshot:** (Optional, showing the `cd` command and the updated prompt like `bandit3@bandit:~/inhere$`)

3.  **List all files, including hidden ones:**
    ```bash
    ls -a
    ```
    * **Explanation:** The `ls` command with the `-a` flag displays all files and directories, including those that start with a `.` (which are conventionally hidden files in Unix-like systems). This revealed `.hidden` along with `.` (current directory) and `..` (parent directory).
    * **Screenshot:** `Screenshots/level04_ls_a_output.png` 

4.  **Read the hidden file:**
    ```bash
    cat .hidden
    ```
    * **Explanation:** Once the hidden file `.hidden` was identified, `cat` was used to display its content, which was the password.
    * **Screenshot:** `Screenshots/level04_password_output.png`

## Password for Level 4
`pIwrPrtPN36QITSp3EQaw936yaFoFgAB`

---
