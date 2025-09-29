# Leviathan Level 2

#Solution

- the only file in the home directory is a setuid executable, with leviathan2 permissions
- running this executable, we are asked for a password
- if we enter the wrong password we get a message and the script stops
- using "ltrace ./check", we can see the script compares the first three letters from the input to the word "sex", so that must be the password
- we use it and a shell opens
- using "whoami" we can see we have leviathan2 permissions, so we go to /etc/leviathan_pass/leviathan2 and retrieve the password for the next level

# Password

- NsN1HwFoyN

# New things I learned

- the shell is the actual program that interprets commands entered in the command prompt
- ltrace = a program that intercepts and records the dynamic library calls that are called by an executed process, and the signal received by that process
- strace = traces system calls (direct requests to the linux kernel for services like file operations, process management, etc.)
