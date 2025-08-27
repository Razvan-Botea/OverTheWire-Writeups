## Bandit Level 19

## Level goal
The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

## Solution
    - use **ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh**
    - Instead of letting SSH start the default login shell, you explicitly told it to run `/bin/sh` (the basic Bourne shell)

## Password
    - cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

## New concepts learned
What Normally Happens:
    1. You SSH in
    2. SSH starts a login shell (`bash -l` or equivalent)
    3. Bash reads `/etc/profile` and other profile files
    4. Bash reads `~/.bashrc` for interactive shells
    5. The `exit` command in `.bashrc` immediately terminates your session

Why This Worked:
    1. **`/bin/sh` doesn't read `.bashrc`** - it only reads `.profile` for login shells, and you're not starting a login shell
    2. **You bypassed bash entirely** - no `.bashrc` was executed because you're using `sh`, not `bash`
    3. **The `-t` flag** made the session interactive so you get a prompt
    4. **`sh` is simpler** - it doesn't have all the bash features, but it's enough to run basic commands

