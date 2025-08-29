## Bandit Level 21

## Level goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

## Solution
    - **echo -n "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 1234 &**
	    - use netcat (nc) to create a server that listens (-l) on port 1234 (-p) and runs in the background (&) so that we can use the terminal while it runs
    - **./suconnect 1234** 
	    - i run the setuid library with the port of the netcat server previously created so that it connects to that server
	    - it receives the password that i made the netcat server output with echo
	    - it compares it with the previous level password, it checks => i receive the new password

## Password
    - EeoULMCra2q0dSkYj561DX7s1CpBuOBt
