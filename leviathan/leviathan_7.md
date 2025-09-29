# Leviathan Level 7

# Solution

- in the home directory, there is a setuid executable with leviathan7 permissions
- it asks for a 4 digit input code
- if we enter the wrong code, we get the message "Wrong"
- we can do a for loop that goes through all the possible combinations:
	- for i in {0000..9999}l do ./leviathan6 $i; done
- we eventually try the right combination and a command prompt opens, with leviathan7 permissions
- we use "cat /etc/leviathan_pass/leviathan7" in this new command prompt to retreive the password

# Password

- qEs5Io5yM8
