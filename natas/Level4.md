```
Username: natas4
Password: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
URL:      http://natas4.natas.labs.overthewire.org
```

- when opening this level, I see the following message:
	- Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
- if i refresh the page it says:
	- Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
- looking at the requests made by the browser using Burp Suite, i can see that the request made when i press the Refresh page button contains a Referer header, which contains the address of the previous web page from which a link to the currently requested page was followed
- it says i came from http://natas4.natas.labs.overthewire.org/
- i can use the repeater tool in Burp to modify this header to http://natas5.natas.labs.overthewire.org/ and send the request this way
- after doing this, i get the password for the next level

# Password

- **0n35PkggAPm2zbEpOU802c0x0Msn1ToK**
