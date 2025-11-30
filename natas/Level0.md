# OverTheWire: Natas

Natas teaches the basics of serverside web-security.
Each level of natas consists of its own website located at **http://natasX.natas.labs.overthewire.org**, where X is the level number. There is **no SSH login**. To access a level, enter the username for that level (e.g. natas0 for level 0) and its password.
Each level has access to the password of the next level. Your job is to somehow obtain that next password and level up. **All passwords are also stored in /etc/natas_webpass/**. E.g. the password for natas5 is stored in the file /etc/natas_webpass/natas5 and only readable by natas4 and natas5.

```
Username: natas0
Password: natas0
URL:      http://natas0.natas.labs.overthewire.org
```
# Solution

- i connect to the website via browser
- it opens a blank page, with only one line of text, and nothing else
- i right click and choose the Inspect option from the menu to look at the HTML source code
- there i see a comment with the password for the next level

# Password

**0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq**
