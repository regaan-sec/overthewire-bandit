# Bandit Level 0 to Level 1

## Objective
The goal of this level is to log into the Bandit game server using the provided credentials and find the password for the next level.

## Tools Used
* `ssh`: Secure Shell client for remote connection.
* `ls`: List directory contents.
* `cat`: Concatenate and display file content.

## Concepts Learned
* Basic usage of the `ssh` command for remote server access.
* Understanding the `ls` command to view files in a directory.
* Using the `cat` command to read the content of a file.
* The fundamental idea of a "password file" in CTFs.

## My Approach & Thought Process
The challenge instructions were clear: connect to `bandit.labs.overthewire.org` on port `2220` as user `bandit0` with password `bandit0`. My first step was to execute the `ssh` command with these parameters. Once connected, a common CTF practice is to look for obvious files in the current directory, typically named `readme`, `password.txt`, or similar, that might contain the flag (password). I used `ls` to quickly check the directory contents, which revealed a file named `readme`. Finally, `cat` was the natural choice to view its content.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit0@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:**
        * `ssh`: The command-line client for Secure Shell protocol.
        * `bandit0@bandit.labs.overthewire.org`: Specifies the username (`bandit0`) and the hostname of the target server.
        * `-p 2220`: Defines the port number (2220) to connect to, as SSH usually defaults to port 22.
    * **Input Password (when prompted):** `bandit0`
    * **Screenshot:** `Screenshots/level00_login.png`

2.  **List the contents of the current directory:**
    ```bash
    ls
    ```
    * **Explanation:** The `ls` command lists files and directories within the current working directory. This quickly showed a file named `readme`.
    * **Screenshot:** `Screenshots/level01_ls_readme.png`

3.  **Read the content of the `readme` file:**
    ```bash
    cat readme
    ```
    * **Explanation:** The `cat` (concatenate) command is used here to display the entire content of the `readme` file to standard output, revealing the password for the next level.
    * **Screenshot:** `Screenshots/level01_readme_content.png` 

## Password for Level 1
`boJ9jbbUNNfktd78OOpsqOltutMc3MY1`

---
