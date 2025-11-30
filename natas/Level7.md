```
Username: natas7
Password: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS
URL:      http://natas7.natas.labs.overthewire.org
```

- for this level, we get a page with two buttons, "Home" and "About"
- pressing on either of them we get to a page that has a query in the URL:
	- http://natas7.natas.labs.overthewire.org/index.php?page=about
- maybe i can use this for path traversal and reach the password for the next level
- in the HTML source code there is a comment:
	- password for webuser natas8 is in /etc/natas_webpass/natas8
- so i need to get to that page
- i used the following URL:
	- http://natas7.natas.labs.overthewire.org/index.php?page=/../../../etc/natas_webpass/natas8
- this gets me to a page with the password

# Password

- **xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q**
