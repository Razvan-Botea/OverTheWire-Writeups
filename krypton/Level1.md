# Description
The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

# Solution

- for this level i go to the specified directory: ~/krypton/krypton1
- there is only one file there, with ROT13 encoded text
- to decode it i used: `cat krypton2 | tr 'A-Za-z' 'N-ZA-Mn-za-m'`
- with this, i got the password for the next level:
	- **ROTTEN**
