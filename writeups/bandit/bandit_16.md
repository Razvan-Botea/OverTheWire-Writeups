## Bandit Level 16

## Level goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL/TLS encryption.

## Solution
    - used **echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -connect localhost:30001 -quiet**

## Password
    - kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

## New contepts learned
    - openssl s_client = used to connect to servers using SSL/TLS encryption
    - connect localhost:30001 = specifies the connection target
    - SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols that provide secure communication over a computer network. TLS is the modern, more secure version that replaced SSL.
