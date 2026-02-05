# Description

Welcome to Krypton! The first level is easy. The following string encodes the password using Base64: `S1JZUFRPTklTR1JFQVQ=`
Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/

# Solution

- i decoded the password:
	- `echo "S1JZUFRPTklTR1JFQVQ=" > encoded.txt`
	- 'base64 -d encoded.txt'
	- password: **KRYPTONISGREAT**
- i connected to the server with the provided credentials: `ssh -p 2231 krypton1@krypton.labs.overthewire.org`
