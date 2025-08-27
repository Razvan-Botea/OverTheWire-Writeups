## Bandit Level 20

## Level goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

## Solution
    - execute the setuid binary: ./bandit20-do id to check what priviledges it has
    - uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
    - executed cat through the setuid binary:
	    - **./bandit20-do cat /etc/bandit_pass/bandit20**

## Password
    - 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

## New concepts learned
    - The access rights flags setuid and setgid (short for _set user identity_ and set group identity) allow users to run an executable with the file system permissions of the executable's owner or group respectively and to change behavior in directories. 
    - The setuid binary runs with **bandit20's privileges** (euid=bandit20)
    - When it executes `cat`, the `cat` command inherits those privileges
    - `cat` can then read `/etc/bandit_pass/bandit20` because it's running as bandit20
