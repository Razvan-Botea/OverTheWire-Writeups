# Description

This level contains an old form of cipher called a ‘Caesar Cipher’.
A Caesar cipher shifts the alphabet by a set number. For example:
```
plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...
```
In this example, the letter ‘a’ in plaintext is replaced by a ‘G’ in the ciphertext so, for example, the plaintext ‘bad’ becomes ‘HGJ’ in ciphertext.
The password for level 3 is in the file krypton3. It is in 5 letter group ciphertext. It is encrypted with a Caesar Cipher. Without any further information, this cipher text may be difficult to break. You do not have direct access to the key, however you do have access to a program that will encrypt anything you wish to give it using the key. If you think logically, this is completely easy.

# Solution

- first, i need to make a temporary directory and test the encryption script, to see the degree of the rotation:
```
krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat
```
- if i encrypt the plaintext "abc", i get the cyphertext "MNO", which means the key is 14
- knowing this, i can get the password with the following command:
	- `cat /krypton//krypton2/krypton3 | tr 'A-Za-z' 'O-ZA-No-za-n'`
	- password: **CAESARISEASY**
