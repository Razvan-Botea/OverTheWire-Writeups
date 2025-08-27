## Bandit Level 14

## Level goal
The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

## Solution
    - use **ssh -i ./sshkey.private bandit14@localhost:2220** to connect to the bandit14 host using the private key 
    - as bandit14, go to the /etc/bandit_pass/bandit14 and rerieve the password for level 14

## Password
    - MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## New concepts learned
    - With public key authentication, the authenticating entity has a public key and a private key. 
    - Each key is a large number with special mathematical properties. The private key is kept on the computer you log in from, while the public key is stored on the **.ssh/authorized_keys** file on all the computers you want to log in to.
    - When you log in to a computer, the SSH server uses the public key to "lock" messages in a way that can only be "unlocked" by your private key
    - SSH can use either "RSA" (Rivest-Shamir-Adleman) or "DSA" ("Digital Signature Algorithm") keys.
