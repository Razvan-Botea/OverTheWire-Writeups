```
Username: natas13
Password: trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC
URL:      http://natas13.natas.labs.overthewire.org
```

- this level is similar to the previous one, but this time i can only upload image files
- to bypass this, i can create a file that has a jpeg header and the body containing the php command used in the last level
- first i create the .php file like i normally would
- then i edit it using hexedit, and add at the beginning the jpeg header: **FF D8 FF E0 00 10 4A 46 49 46 00 01 01 00 00 01 00 01 00 00**
- then i upload the file to the site and follow the same steps as for the previous level to get the password

# Password

-  **z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ**
