## Bandit Level 7

## Level goal
The password for the next level is stored **somewhere on the server** and has all of the following properties:
	- owned by user bandit7
	- owned by group bandit6
	- 33 bytes in size

## Solution
    - used "cd" to go to the root directory "/"
    - used "find -group bandit6 -user bandit7 -size 33c 2>/dev/null"
        - 2>/dev/null redirects the permission denied (stderr) files to the null directory, so we only see the files we can access
        - we find "./var/lib/dpkg/info/bandit7.password"
    - used "cd" to go to the directory we found
    - used "cat" to diplay the contents of the file

## Password
    - morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## New concepts learned
    - the 2 in "2>/dev/null" represents the file descriptor stderr
    -file descriptors are integers that represent I/O resources, used by processes to interact with files, devices, or other I/O streams
    - there are three types:
        0 = stdin
        1 = stdout
        2 = stderr
