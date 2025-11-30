```
Username: natas8
Password: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q
URL:      http://natas8.natas.labs.overthewire.org
```

- similar to level 6, i need a secret key to be able to get the password
- looking at the source code, it seems to compare the input with an encoded string
- i get the encoded string and the method of encryption:
	- `bin2hex(strrev(base64_encode($secret)))`
	- `$encodedSecret = "3d3d516343746d4d6d6c315669563362"`
- now all i need to do is apply the steps in reverse order on the encoded string and i will obtain the key
- i do this using CyberChef, and get the key: oubWYf2kBq
- using this i get the password for the next level

# Password

- **ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t**
