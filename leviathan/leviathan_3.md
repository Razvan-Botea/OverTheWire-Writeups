# Leviathan Level 3

# Solution

- in the home directory there is a setuid executable
- if we run it by itself, we find out that its usage is to print the content of a file given as a parameter
- if we use it on a file we have permission to access, like /etc/passwd, and use ltrace to see what functions it uses, we see that it checks the access permissions for the given file, and then uses "%s" to get the file that is actually opened
- because of this, we can create a file called "file;bash", and because of the ; in the name of the file, the program will use the "file" part to check for permissions, and will run only the second part, which is the bash file
- since the "printifle" runs with leviathan3 premissions, it opens a command prompt with those permissions
- we can now access /etc/leviathan_pass/leviathan3 and retrieve the password

# Password

- f0n8h2iWLP
