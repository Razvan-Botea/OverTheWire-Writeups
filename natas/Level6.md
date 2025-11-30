```
Username: natas6
Password: 0RoJwHdSKWFTYR5WuiAewauSuNaBXned
URL:      http://natas6.natas.labs.overthewire.org
```

- for this level, I need to input a "key" to get access to the password
- in the source code of the page there is a bit of C code that checks is the input is the same as the key and grants access to the password based on that
- i see it uses a library found at "includes/secret.inc"
- if i go to that location on the server i find the secret key: "FOEIUWGHFEEUHOFUOIU"
- using this i can obtain the password

# Password

- "bmg8SvU1LizuWjx3y7xkNERkHxGre0GS"

