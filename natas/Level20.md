```
Username: natas20
Password: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw
URL:      http://natas20.natas.labs.overthewire.org
```
- when i log in, the site says i am logged in as a regular user
- i need to log in as an admin to retrieve credentials for the next level

- checking the PHPSESSID cookie using DevTools, I see it is a random string of characters
- to be able to see the credentials, the `$_SESSION` needs to exist, and to contain a key called `admin` with the value `1`
- so how do i get a session value?

- in the source code, i see a function called `session_set_save_handler()`,  which is a session-related function that sets user-level session storage functions
- this function lets the author of the code to specify what they want to happen when certain actions happen in a session
- then `session_start()` is called, which starts or resumes an existing session
- after that, the `print_credentials()` is called, which prints the password for the next level if i am logged in as an admin

- the developer wrote custom functions: `mywrite()` and `myread()` to save session data to a text file
**Any time that developers go out of their way to avoid using the normal behavior of a function or library is an opportunity to find a bug.**
![image](images/natas20.png)
- if i submit something in the input provided on the site, `mywrite()` is called
- first, it check that the input only contains alphanumeric characters, so i cannot do path traversal
- then, the `$data` variable (which contains the serialized version of `$_SESSION`) is cleared
- the `$_SESSION` variable is ksort()‘d, which sorts the keys in ascending order
- each key and value pair in `$_SESSION` are read into the (recently cleared) `$data` variable, and saved in the file.
- session data is written in a specific format: `KEY` + `SPACE` + `VALUE` + `NEWLINE` 

![image](images/natas_20_2.png)
- next, the `myread()` function, which takes a `$sid` value (the random `PHPSESSID`) and makes sure it is not doing any path traversal
- then it looks for the existence of the file that was saved previously in the `mywrite()` call. It gets the contents from that file, reads it line by line, and then writes that into the `$_SESSION` variable.
- `myread()` reads the file written by `mywrite()`
- crucially, it parses the file **line by line**.
- The first part becomes the **Session Key**.
- The second part becomes the **Session Value**.

- `mywrite()` function **does not sanitize** input
- because the "Reader" trusts that every new line is a new separate session variable, I can inject a newline character (`\n`) into the input to trick the reader
- since i want to send `$_SESSION["admin"] = 1`, my input should be: `test\nadmin 1`
- this also needs to be URL encoded, so it should look like this: `test%0aadmin%201`

- **Intercept:** Open Burp Suite and intercept the request when you submit the name "test".
- **Repeater:** Send this request to the "Repeater" tool (allows you to modify and resend raw data).
- **Modify:** In the Body of the request, find `name=test`. Change it to: `name=test%0Aadmin%201`
- **Send:** Submit the request. The server saves the "corrupted" file.
- the site returns the password for the next level

# Password

- **BPhv63cKE1lkQl04cE5CuFTzXe15NfiH**
