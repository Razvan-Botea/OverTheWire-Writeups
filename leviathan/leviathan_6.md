# Leviathan Level 6

# Solution

- in the home directory, there is a setuid executable with leviathan6 permissions
- if we run it, we get the following message:
	- "Cannot find /tmp/file.log"
- if we create the file and run the executable, it just opens the file and then closes it
- using "ln -s" we create a simbolic link with the name "file.log" that links to the /etc/leviathan_pass/leviathan6"
- now if we run the executable, it will access the leviathan6 password file and print its contents

# Password

- szo7HDB88w
