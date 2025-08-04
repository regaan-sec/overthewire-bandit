# OverTheWire Bandit Wargame - My Journey (Levels 0-18)

This repository documents my progress and key learnings while playing the OverTheWire Bandit Wargame. Each level presents a unique challenge designed to teach fundamental Linux command-line and security concepts.

---

## Week 1 - Day 1: Laying the Foundation (Levels 0 - 18)

Today marks the official start of my structured cybersecurity learning plan. As Day 1 of Week 1, I've dived deep into the OverTheWire Bandit Wargame, completing the initial 19 levels to build a strong foundation in Linux command-line essentials and basic security concepts.

### **Level 0 -> 1: First Steps**
* **Problem:** Find the password for the next level in the `readme` file.
* **Solution:** Basic file system navigation and viewing file contents.
* **Commands Used:** `ls`, `cd`, `cat`
* **Skills Learned:** Navigating the Linux file system, listing directory contents, viewing simple text files.

### **Level 1 -> 2: Hidden Files**
* **Problem:** Find the password in a hidden file.
* **Solution:** Hidden files start with a dot (`.`). The `ls -a` command reveals them.
* **Commands Used:** `ls -a`, `cat`
* **Skills Learned:** Understanding hidden files, using command-line flags.

### **Level 2 -> 3: Filenames with Spaces**
* **Problem:** The password file had a space in its name.
* **Solution:** Use quotes or backslashes to escape spaces in filenames.
* **Commands Used:** `cat "spaces in filename"`, `cat spaces\ in\ filename`
* **Skills Learned:** Handling special characters in filenames.

### **Level 3 -> 4: Hidden Directories**
* **Problem:** The password was in a hidden directory.
* **Solution:** Navigate into the hidden directory and then find the file.
* **Commands Used:** `ls -a`, `cd .hidden`, `cat ./.hiddenfile`
* **Skills Learned:** Navigating into hidden directories.

### **Level 4 -> 5: Finding the Right File**
* **Problem:** The password was in a specific file within a large directory.
* **Solution:** Use `ls -l` to get more details about files and identify the correct one based on properties.
* **Commands Used:** `ls -l`, `cat`
* **Skills Learned:** Interpreting `ls -l` output (permissions, ownership, size).

### **Level 5 -> 6: Finding Files by Properties**
* **Problem:** Find a password file with specific properties (human-readable, 1033 bytes, not executable).
* **Solution:** Use the `find` command with various flags to search by size, type, and permissions.
* **Commands Used:** `find . -type f -size 1033c ! -executable`
* **Skills Learned:** Advanced `find` command usage (size, type, permissions, negation).

### **Level 6 -> 7: Finding Files by User/Group**
* **Problem:** Find the password file owned by a specific user and group.
* **Solution:** Used `find` with `-user` and `-group` flags.
* **Commands Used:** `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`
* **Skills Learned:** Searching files by ownership, redirecting standard error to `/dev/null` to suppress "Permission denied" messages.

### **Level 7 -> 8: Grepping for Keywords**
* **Problem:** The password was next to a specific word ("millionth") in `data.txt`.
* **Solution:** Used `grep` to search for the keyword within the file.
* **Commands Used:** `cat data.txt | grep millionth` or `grep millionth data.txt`
* **Skills Learned:** Basic `grep` usage, piping output.

### **Level 8 -> 9: Unique Lines**
* **Problem:** The password was the only line of text that occurred only once in `data.txt`.
* **Solution:** Combined `sort` to group identical lines and `uniq -u` to display only unique lines.
* **Commands Used:** `sort data.txt | uniq -u` (or `sort data.txt | uniq -c` to count occurrences)
* **Skills Learned:** Using `sort` for text ordering, `uniq` for unique lines, and understanding `uniq` flags (`-u`, `-c`).

### **Level 9 -> 10: Extracting Strings from Binary**
* **Problem:** The password was in one of the few human-readable strings within a binary file, preceded by several '=' characters.
* **Solution:** Used `strings` to extract human-readable text, then `grep` to filter for the specific pattern.
* **Commands Used:** `strings data.txt | grep '====='`
* **Skills Learned:** Extracting text from binary files, combining `strings` with `grep` for precise filtering.

### **Level 10 -> 11: Base64 Decoding**
* **Problem:** The password was in a base64 encoded file.
* **Solution:** Used `base64 -d` to decode the file.
* **Commands Used:** `base64 -d data.txt`
* **Skills Learned:** Understanding base64 encoding/decoding, using `base64` command with `-d` flag.

### **Level 11 -> 12: ROT13 Cipher**
* **Problem:** All lowercase and uppercase letters in `data.txt` were rotated by 13 positions (ROT13).
* **Solution:** Used the `tr` command to perform character translation.
* **Commands Used:** `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`
* **Skills Learned:** Understanding ROT13 cipher, advanced `tr` command usage for character translation/substitution.

### **Level 12 -> 13: Multi-Stage Decompression**
* **Problem:** The password was in a file that was a hexdump of a repeatedly compressed file.
* **Solution:** A multi-step process:
    1.  Convert hexdump back to binary: `xxd -r data.txt > data.bin`
    2.  Repeatedly use `file` to identify compression type and then decompress (`gzip -d`, `bzip2 -d`, `tar -xvf`) until the final ASCII text is revealed.
* **Commands Used:** `xxd -r`, `file`, `gzip -d`, `bzip2 -d`, `tar -xvf`, `mv`, `cat`
* **Skills Learned:** Complex multi-stage problem solving, using `xxd` for hex conversion, `file` for type identification, and various decompression tools.

### **Level 13 -> 14: SSH with Private Key**
* **Problem:** The next password required logging in with a provided private SSH key.
* **Solution:** Used the `ssh` command with the `-i` flag to specify the identity file (private key). Also learned to set correct file permissions (`chmod 600`) for the private key.
* **Commands Used:** `chmod 600 <private_key_file>`, `ssh bandit14@localhost -i <private_key_file>`
* **Skills Learned:** SSH key-based authentication, `ssh -i` flag, understanding and setting secure file permissions (`chmod`).

### **Level 14 -> 15: Network Communication with `netcat`**
* **Problem:** Submit the current password to `localhost:30000`.
* **Solution:** Used `netcat` (`nc`) to establish a connection to the specified port and pipe the password into it.
* **Commands Used:** `cat /etc/bandit_pass/bandit14 | nc localhost 30000`
* **Skills Learned:** Basic network communication with `netcat`, piping data to network connections.

### **Level 15 -> 16: Secure Network Communication with `openssl`**
* **Problem:** Submit the current password to `localhost:30001` using SSL/TLS encryption.
* **Solution:** Used `openssl s_client` to establish an encrypted connection and pipe the password.
* **Commands Used:** `cat /etc/bandit_pass/bandit15 | openssl s_client -quiet -connect localhost:30001`
* **Skills Learned:** Handling SSL/TLS connections from the command line, using `openssl s_client`, suppressing verbose output (`-quiet`).

### **Level 16 -> 17: Port Scanning and Protocol Identification**
* **Problem:** Find a server in the port range `31000-32000` on `localhost` and determine its protocol (SSL/TLS or plain-text) to get credentials.
* **Solution:** Used `netcat -zv` to scan the port range for open ports. Then, for each open port, attempted connection with both `openssl s_client` (for SSL) and `nc` (for plain-text) to identify the correct protocol and retrieve the password.
* **Commands Used:** `nc -zv localhost 31000-32000`, `cat /etc/bandit_pass/bandit16 | openssl s_client -quiet -connect localhost:<SSL_port>`, `cat /etc/bandit_pass/bandit16 | nc localhost <plain_text_port>`
* **Skills Learned:** Advanced port scanning with `netcat`, systematic network service identification, combining tools for complex network reconnaissance.

### **Level 17 -> 18: File Comparison with `diff`**
* **Problem:** The password was in a file (`passwords.new`) that was different from an older version (`passwords.old`).
* **Solution:** Used the `diff` command to highlight the differences between the two files. The line prefixed with `<` indicated the new content (the password).
* **Commands Used:** `diff passwords.new passwords.old`
* **Skills Learned:** Using `diff` for file comparison, interpreting `diff` output.

### **Level 18 -> 19: Non-Interactive SSH Command Execution**
* **Problem:** Upon SSH login, the `.bashrc` file immediately logged the user out, preventing access to the `readme` file.
* **Solution:** Executed `cat readme` directly via `ssh` as a non-interactive command, bypassing the `.bashrc` script.
* **Commands Used:** `ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat readme'`
* **Skills Learned:** Bypassing interactive shell startup, executing remote commands directly via `ssh`.
