# Bandit Level 5 to Level 6

## Objective
The password for the next level is in a file that meets three specific criteria: it is human-readable, exactly 1033 bytes in size, and not executable. This file is located in the `inhere` directory.

## Tools Used
* `ssh`: Secure Shell client.
* `cd`: Change directory.
* `find`: Search for files in a directory hierarchy.
* `cat`: Concatenate and display file content.

## Concepts Learned
* Advanced usage of the `find` command to filter files based on multiple criteria.
* Understanding `find`'s options for file type (`-type`), size (`-size`), and permissions (`-executable`, `! -executable`).
* Using the `c` suffix with `-size` to specify exact byte count.

## My Approach & Thought Process
This level presented a multi-criteria search problem. Instead of checking each file manually for its size and permissions, the `find` command is the ideal tool for searching a directory tree based on various attributes. I needed to combine three conditions:
1.  It must be a regular file (`-type f`).
2.  It must be exactly 1033 bytes (`-size 1033c`).
3.  It must NOT be executable (`! -executable`).

I navigated to the `inhere` directory, and then constructed a `find` command incorporating all these flags.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit5@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:** Connect to the `bandit5` user account.
    * **Input Password (when prompted):** `[PASSWORD_FROM_PREVIOUS_LEVEL]`
    * **Screenshot:** (Optional)

2.  **Change directory into `inhere`:**
    ```bash
    cd inhere
    ```
    * **Explanation:** Changed the working directory to `inhere`, where the target file is located.
    * **Screenshot:** (Optional)

3.  **Find the file matching all criteria:**
    ```bash
    find . -type f -size 1033c ! -executable
    ```
    * **Explanation:**
        * `find .`: Starts the search from the current directory (`.`).
        * `-type f`: Specifies that we are only looking for regular files (excluding directories, links, etc.).
        * `-size 1033c`: Filters for files that are exactly 1033 bytes in size. The `c` suffix ensures the size is interpreted in bytes.
        * `! -executable`: The exclamation mark (`!`) negates the `-executable` test, meaning it looks for files that are *not* executable by any user. This command efficiently returned the single filename that met all specified criteria.
    * **Screenshot:** `Screenshots/level06_find_output.png`

4.  **Read the identified file:**
    ```bash
    cat <identified_filename>
    ```
    * **Explanation:** (Replace `<identified_filename>` with the actual file path found by `find`). This command displayed the password.
    * **Screenshot:** `Screenshots/level06_password_output.png`

## Password for Level 6
`DXjZPULLxYr17uwoI01bNLQbtFemEgo7`

---
