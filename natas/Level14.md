```
Username: natas14
Password: z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
URL:      http://natas14.natas.labs.overthewire.org
```

- this level has a web page that asks for a username and a password
- looking at the source code, i can see it uses a SQL query to check the database and connect the user
`"SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\""`
- however, the input is not sanitized
- this makes it vulnerable to a SQL injection
- i used `" or 1=1; -- ` to break the query and log in, obtaining the password for the next level

# Password

- **SdqIqBsFcz3yotlNYErZSZwblkm0lrvx**
