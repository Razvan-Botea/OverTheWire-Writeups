# OverTheWire-Writeups
# OverTheWire Wargame Solutions

This repository contains my personal solutions and scripts for the [OverTheWire](https://overthewire.org/wargames/) wargames. These games are designed to teach security concepts, Linux command-line usage, networking protocols, and web security in a fun, gamified environment.

> **Note:** The folders in this repository contain the solution scripts or flags. Below is an index of the concepts covered in each game and level.

---

## 1. Bandit
**Focus:** Linux Basics, SSH, File Manipulation, Text Processing.

* **Levels 0–4:** Introduction to the shell. Basic navigation (`cd`, `ls`), reading files (`cat`), handling hidden files, and dealing with filenames containing spaces or dashes.
* **Levels 5–6:** Advanced file searching. Using the `find` command to locate files based on specific properties like file size, user ownership, and permissions.
* **Levels 7–9:** Text processing. Extracting specific data using `grep`, `sort`, and `uniq` to filter through large datasets.
* **Levels 10–12:** Data encoding. Decoding strings using `base64`, `rot13` (Caesar cipher), and analyzing hexdumps.
* **Levels 13–15:** SSH and Networking. managing SSH private keys, sending data to local ports using `nc` (netcat), and connecting to SSL-encrypted services using `openssl`.
* **Levels 16–17:** Port scanning. Identifying listening ports and specific service responses.
* **Levels 18–20:** Shell behavior and SUID. dealing with `.bashrc` files, handling restricted shells, and understanding `setuid` binaries.
* **Levels 21–24:** Cron jobs and Scripting. Analyzing automated system tasks (`cron`) to execute custom scripts for privilege escalation.
* **Levels 25–26:** Alternative Shells. Breaking out of restricted text editors (like `vi` or `more`) to spawn a shell.
* **Levels 27–31:** Version Control. Using `git` to investigate repository history, branches, and tags to find hidden passwords.
* **Levels 32–33:** Escape Shells. Breaking out of custom "uppercase shells" using positional parameters.

---

## 2. Leviathan
**Focus:** Basics of Privilege Escalation, Command Injection, Debugging.

* **Level 0:** Reconnaissance. analyzing HTML comments and backup files to find stored credentials.
* **Level 1:** Debugging. Using `ltrace` to intercept library calls and uncover a hardcoded password check.
* **Levels 2–3:** File Permissions & Race Conditions. exploiting binaries that check access permissions (like `access()`) insecurely, allowing for TOCTOU (Time-of-Check to Time-of-Use) attacks.
* **Level 4:** Binary Data. Working with binary representation and converting binary data to ASCII.
* **Level 5:** Symbolic Links. Hijacking file paths using `ln -s` to trick a binary into reading a protected file.
* **Level 6:** Brute Force. Creating a script to brute-force a 4-digit PIN protecting a binary.

---

## 3. Natas
**Focus:** Web Security, Server-Side Vulnerabilities.

* **Levels 0–3:** Information Leaks. Inspecting HTML source code ("View Source"), analyzing `robots.txt`, and finding hidden directories/files.
* **Levels 4–5:** HTTP Headers & Cookies. manipulating request headers (Referer, User-Agent) and modifying cookies to bypass authentication checks.
* **Levels 6–8:** Secrets Management. Identifying exposed secrets in server-side includes, commenting, or encoded source code.
* **Levels 9–10:** Command Injection Basics. Exploiting poorly sanitized inputs (often `grep` wrappers) to execute arbitrary shell commands.
* **Level 11:** Cryptography Flaws. Analyzing XOR encryption logic to forge valid cookies.
* **Levels 12–13:** File Upload Vulnerabilities. Bypassing upload filters (extension checks and magic bytes) to upload a PHP web shell.
* **Levels 14–15:** SQL Injection (SQLi). Bypassing login forms using classic SQL injection and handling Blind SQL injection where no output is returned.
* **Levels 16–18:** Blind Injection & Session Hijacking. exploiting command injection where grep output is suppressed (side-channel attacks) and predicting session IDs.
* **Levels 19–20:** Advanced Session Management. Exploiting predictable session IDs (hex encoding) and session storage injection (newline injection).
* **Levels 21–22:** Co-located Website Logic. Manipulating interactions between two related websites to "poison" the `$_SESSION` variable and redirect flow.
