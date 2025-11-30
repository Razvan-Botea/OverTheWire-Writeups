```
Username: natas9
Password: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t
URL:      http://natas9.natas.labs.overthewire.org
```

- for this level we get a page where we can input a string and it will find words containing that string
- the source code reveals that this is done with the following function:
	- `passthru("grep -i $key dictionary.txt");`
- this is a PHP command that tells the server's operating system to run a program (e.g. grep)
- if i use ";" in the input, followed by another command like "ls", i can make the program run multiple commands
- using this, i input "; ls" on the web page and get the list of files in the current directory
- now i can use this to print the contents of the file containing the password for the next level
- i know the passwords for the next level are stored in /natas_webpass/natasX on each level
	- ";cat /etc/natas_webpass/natas10"
	- and i get the password

# Password

- **t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu**
