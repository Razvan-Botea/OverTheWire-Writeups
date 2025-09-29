# Leviathan Level 4

# Solution

- the only file in the home directory is a setuid executable, with leviathan4 permissions
- running this executable, we are asked for a password
- if we enter the wrong password we get a message and the script stops
- using "ltrace ./level3", we can see the script compares the input to the word "snlprintf", so that must be the password
- we use it and a shell opens
- using "whoami" we can see we have leviathan4 permissions, so we go to /etc/leviathan_pass/leviathan4 and retrieve the password for the next level

# Password

- WG1egElCvO
