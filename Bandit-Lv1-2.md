# Bandit Level 1 to Level 2

## Objective
The password for the next level is located in a file named `-` within the current directory.

## Tools Used
* `ssh`: Secure Shell client.
* `ls`: List directory contents.
* `cat`: Concatenate and display file content.

## Concepts Learned
* How to handle unusual filenames (specifically, filenames that are also command-line options).
* The significance of `.` (current directory) in file paths.
* Understanding `cat`'s behavior when `-` is given as an argument (reading from standard input).

## My Approach & Thought Process
After logging in, I used `ls` to inspect the current directory. To my surprise, the only visible file was named `-`. My immediate thought was to use `cat -`. However, `cat -` typically instructs the `cat` command to read from standard input (the keyboard), not from a file named `-`. This resulted in the command just hanging, waiting for my input.

To resolve this, I realized I needed to explicitly tell the shell that `-` was a filename in the current directory, not an option. Prefixing it with `./` (which means "in the current directory") achieved this, correctly identifying the file.

## Commands Used

1.  **Connect to the Bandit server via SSH:**
    ```bash
    ssh bandit1@bandit.labs.overthewire.org -p 2220
    ```
    * **Explanation:** Connect to the `bandit1` user account using the password from the previous level.
    * **Input Password (when prompted):** `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`
    * **Screenshot:** (Optional, if you want to show successful login again.)

2.  **List the contents of the current directory:**
    ```bash
    ls
    ```
    * **Explanation:** This command revealed a single file named `-`.
    * **Screenshot:** `Screenshots/level02_filename_with_dash.png`

3.  **Attempt to read the file (and observe the issue):**
    ```bash
    cat -
    ```
    * **Explanation:** This attempt resulted in `cat` waiting for input from the terminal because `-` is interpreted as standard input. This served as a learning point about how command-line options are parsed.
    * **Screenshot:** (Optional, to show `cat` hanging, then Ctrl+C to exit).

4.  **Correctly read the file named `-`:**
    ```bash
    cat ./-
    ```
    * **Explanation:** By prepending `./` (representing the current directory), we explicitly define `-` as a file path rather than an option, allowing `cat` to read its contents and display the password. Other valid alternatives would be `cat -- -` (where `--` signifies the end of options) or `cat < -`.
    * **Screenshot:** `Screenshots/level02_password_output.png` 

## Password for Level 2
`CV1DtqXWVFXTvM2F0k099SHz0YwRINYA9`

---
