## Bandit Level 15

## Level goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

## Solution
    - use telnet to submit the password
        - telnet localhost 30000

## Password
    - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

## New concepts learned
    - **localhost** is a hostname that refers to the current computer used to access it. The name _localhost_ is reserved for loopback purposes.-
    - It is used to access the network services that are running on the host via the loopback network interface
    - Using the loopback interface bypasses any local network interface hardware

    - The local loopback mechanism may be used to run a network service on a host without requiring a physical network interface, or without making the service accessible from the networks the computer may be connected to
    - For example, a locally installed website may be accessed from a Web browser by the URL:          _http://localhost_ to display its home page.

    - IPv4 network standards reserve the entire address block 127.0.0.0/8 for loopback purposes
    - in the IPv6 architecture, there is only a single address assigned for loopback: _::1_. The standard precludes the assignment of that address to any physical interface, as well as its use as the source or destination address in any packet sent to remote hosts.
