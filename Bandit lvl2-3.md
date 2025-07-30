# Bandit Level 2 to Level 3

## Objective
The password for the next level is in a file named `spaces in this filename`.

## Tools Used
* `ssh`: Secure Shell client.
* `ls`: List directory contents.
* `cat`: Concatenate and display file content.

## Concepts Learned
* How to handle filenames that contain spaces in shell commands.
* The importance of quoting or escaping special characters in file paths.

## My Approach & Thought Process
Upon logging into `bandit2` and using `ls`, I found a file named `spaces in this filename`. This is another common challenge in Linux, as spaces are typically used to separate arguments in shell commands. If I were to just type `cat spaces in this filename`, the shell would interpret "spaces", "in", "this", and "filename" as four separate arguments to `cat`, leading to an error.

To treat the entire name as a single entity, I knew I needed to either enclose it in quotes or escape each individual space. I opted for double quotes as it's often cleaner for longer filenames.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit2@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:** Connect to the `bandit2` user account.
    * **Input Password (when prompted):** `[PASSWORD_FROM_PREVIOUS_LEVEL]`
    * **Screenshot:** (Optional)

2.  **List the contents of the current directory:**
    ```bash
    ls
    ```
    * **Explanation:** This command showed the file `spaces in this filename`.
    * **Screenshot:** `Screenshots/level03_filename_with_spaces.png` 

3.  **Read the file named `spaces in this filename` (using quotes):**
    ```bash
    cat "spaces in this filename"
    ```
    * **Explanation:** Double quotes (`"`) around the filename instruct the shell to treat the entire string, including the spaces, as a single argument to the `cat` command. This successfully displayed the password.
    * **Screenshot:** `Screenshots/level03_password_output.png`

    *Alternative (using backslash escaping):*
    ```bash
    cat spaces\ in\ this\ filename
    ```
    * **Explanation:** The backslash (`\`) is an escape character that tells the shell to interpret the character immediately following it literally, rather than as a special shell character (like a space as a separator).

## Password for Level 3
`UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

---
