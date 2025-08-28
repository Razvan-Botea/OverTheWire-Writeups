## Bandit Level 33

## Level goal
After all this `git` stuff, it’s time for another escape. Good luck!

## Solution
    - from the previous level, we log into a different shell, the UPPERCASE SHELL, in which normal commands do not work
    - Linux does have uppercase elements, that is variables
    - specifically, the $0 variable has a reference to a shell
    - if we introduce it into the UPPERCASE SHELL, we can break out of it, now normal commands work
    - if we use "whoami" we can see we are logged in as bandit33
    - we go to /etc/bandit_pass/bandit33 and retrieve the password

## Password
    - tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

## New concepts learned
    - Variables in Linux are used to store data that can be used by the shell or scripts. They act as placeholders for values that can change.
    - there are 3 kinds of variables:
        - user-defined variables (e.g. name="John")
        - environment variables = predefined, affect the shell behavior (e.g. $HOME = the home directory)
        - special positional parameters
    - $0 is a special positional parameter that stores the name of the script or the shell that is currently running
        - e.g. in a script called myscript.sh, if we do **echo "$0"** we get **./myscript.sh**

