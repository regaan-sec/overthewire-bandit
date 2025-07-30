# Bandit Level 4 to Level 5

## Objective
The password for the next level is in the *only human-readable* file located within the `inhere` directory.

## Tools Used
* `ssh`: Secure Shell client.
* `cd`: Change directory.
* `ls`: List directory contents.
* `file`: Determine file type.
* `cat`: Concatenate and display file content.

## Concepts Learned
* Using the `file` command to identify the type of content within a file (e.g., ASCII text, data, executable).
* Applying the `*` wildcard for operations on multiple files.

## My Approach & Thought Process
After logging in and navigating into the `inhere` directory (using `cd inhere`), an `ls` command showed many files (e.g., `file01`, `file02`, etc.). The challenge stated that only *one* of these was human-readable. Manually trying `cat` on each file would be tedious and inefficient.

The `file` command is specifically designed to determine the type of a file. By using `file *`, I could quickly get a summary of all file types in the directory. I looked for output like "ASCII text" or "UTF-8 Unicode text", which indicates human-readable content. Once identified, `cat` was used to view the password.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit4@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:** Connect to the `bandit4` user account.
    * **Input Password (when prompted):** `[PASSWORD_FROM_PREVIOUS_LEVEL]`
    * **Screenshot:** (Optional)

2.  **Change directory into `inhere`:**
    ```bash
    cd inhere
    ```
    * **Explanation:** Navigated into the directory containing the challenge files.
    * **Screenshot:** (Optional)

3.  **List files to see the multitude of files:**
    ```bash
    ls
    ```
    * **Explanation:** Showed numerous files like `file01`, `file02`, etc., making it clear that a specific tool was needed to identify the correct one.
    * **Screenshot:** `Screenshots/level05_ls_multiple_files.png`

4.  **Determine the type of all files in the directory:**
    ```bash
    file *
    ```
    * **Explanation:** The `file` command, combined with the `*` wildcard (which expands to all non-hidden files in the current directory), analyzed each file. The output clearly indicated which file was "ASCII text" (human-readable) versus "data" or "empty".
    * **Screenshot:** `Screenshots/level05_file_star_output.png` 

5.  **Read the human-readable file:**
    ```bash
    cat <human_readable_filename>
    ```
    * **Explanation:** (Replace `<human_readable_filename>` with the actual file name identified in the previous step, e.g., `file07`). This command then displayed the password for the next level.
    * **Screenshot:** `Screenshots/level05_password_output.png`

## Password for Level 5
`koReBOKuIDDepwhWk7jZC0RTdopnAYKh`

---
