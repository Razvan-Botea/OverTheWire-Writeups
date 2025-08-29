## Bandit Level 23

## Level goal
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

## Solution
    - cd /etc/cron.d/ => ls => cat cronjob_bandit23
    - cat /usr/bin/cronjob_bandit23.sh

    ```
    #!/bin/bash
    myname=$(whoami)
    mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
    echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
    cat /etc/bandit_pass/$myname > /tmp/$mytarget
    ```
    - i do not have permission to go to bandit_pass/bandit23
    - changed the script in the following way:
        myname=bandit23
    - ran **echo I am user $myname | md5sum | cut -d ' ' -f 1**
    - we get the file called "8ca319486bfbbc3663ea0fbe81326349"
    - cat /tmp/8ca319486bfbbc3663ea0fbe81326349

## Password
    - 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
