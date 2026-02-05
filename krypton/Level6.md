# Description
A feature of good crypto is random ciphertext. A good cipher must not reveal any clues about the plaintext. Since natural language plaintext (in this case, English) contains patterns, it is left up to the encryption key or the encryption algorithm to add the ‘randomness’.
Modern ciphers are similar to older plain substitution ciphers, but improve the ‘random’ nature of the key.
An example of an older cipher using a complex, random, large key is a vigniere using a key of the same size of the plaintext. For example, imagine you and your confident have agreed on a key using the book ‘A Tale of Two Cities’ as your key, in 256 byte blocks.
The cipher works as such:
Each plaintext message is broken into 256 byte blocks. For each block of plaintext, a corresponding 256 byte block from the book is used as the key, starting from the first chapter, and progressing. No part of the book is ever re-used as key. The use of a key of the same length as the plaintext, and only using it once is called a “One Time Pad”.
Look in the krypton6 directory. You will find a file called ‘plain1’, a 256 byte block. You will also see a file ‘key1’, the first 256 bytes of ‘A Tale of Two Cities’. The file ‘cipher1’ is the cipher text of plain1. As you can see (and try) it is very difficult to break the cipher without the key knowledge.
If the encryption is truly random letters, and only used once, then it is impossible to break. A truly random “One Time Pad” key cannot be broken. Consider intercepting a ciphertext message of 1000 bytes. One could brute force for the key, but due to the random key nature, you would produce every single valid 1000 letter plaintext as well. Who is to know which is the real plaintext?!?
Choosing keys that are the same size as the plaintext is impractical. Therefore, other methods must be used to obscure ciphertext against frequency analysis in a simple substitution cipher. The impracticality of an ‘infinite’ key means that the randomness, or entropy, of the encryption is introduced via the method.
We have seen the method of ‘substitution’. Even in modern crypto, substitution is a valid technique. Another technique is ‘transposition’, or swapping of bytes.
Modern ciphers break into two types; symmetric and asymmetric.
Symmetric ciphers come in two flavours: block and stream.
Until now, we have been playing with classical ciphers, approximating ‘block’ ciphers. A block cipher is done in fixed size blocks (suprise!). For example, in the previous paragraphs we discussed breaking text and keys into 256 byte blocks, and working on those blocks. Block ciphers use a fixed key to perform substituion and transposition ciphers on each block discretely.
Its time to employ a stream cipher. A stream cipher attempts to create an on-the-fly ‘random’ keystream to encrypt the incoming plaintext one byte at a time. Typically, the ‘random’ key byte is xor’d with the plaintext to produce the ciphertext. If the random keystream can be replicated at the recieving end, then a further xor will produce the plaintext once again.
From this example forward, we will be working with bytes, not ASCII text, so a hex editor/dumper like hexdump is a necessity. Now is the right time to start to learn to use tools like [cryptool.](http://www.cryptool.com/)
In this example, the keyfile is in your directory, however it is not readable by you. The binary ‘encrypt6’ is also available. It will read the keyfile and encrypt any message you desire, using the key AND a ‘random’ number. You get to perform a ‘known ciphertext’ attack by introducing plaintext of your choice. The challenge here is not simple, but the ‘random’ number generator is weak.
As stated, it is now that we suggest you begin to use public tools, like cryptool, to help in your analysis. You will most likely need a hint to get going. See ‘HINT1’ if you need a kicktstart.
If you have further difficulty, there is a hint in ‘HINT2’.
The password for level 7 (krypton7) is encrypted with ‘encrypt6’.

# Solution

- for this level, i will do a known plaintext attack against a stream cipher
- by making the system encrypt a known plaintext, i can deduce the keystream and use it to decrypt other messages
- `encrypt6`: This is the encryption program. It is **SUID** (Set User ID), meaning when I run it, it runs with the permissions of `krypton7`. This allows it to read the `keyfile.dat` which I (`krypton6`) cannot read.
- `keyfile.dat`: The secret key used by the encryption algorithm.

- first, i create a workspace in /tmp, to be able to create new files:
	- mktemp -d
	- cd /tmp/tmp.DIR
- then i create a symbolic link to the binary in /krypton6, to be able to run it from my workspace:
	- ln -s /krypton/krypton6/encrypt6 encrypt6
- next, i create a symbolic link to the keyfile so that the binary can read it:
	- ln -s /krypton/krypton6/keyfile.dat keyfile.dat
- i also need to give writing permissions to this workspace:
	- chmod 777 .

- The hint mentions an **8-bit LFSR** (Linear Feedback Shift Register). This is a way computers generate pseudo-random numbers. However, the critical flaw here isn't the math of the LFSR, but the nature of the Cipher.

Most simple stream ciphers operate like this (conceptually modulo 26 for letters):
Ciphertext=(Plaintext+Keystream)(mod26)

If we want to find the **Keystream**, we can rearrange the equation:
Keystream=(Ciphertext−Plaintext)(mod26)

If we choose our Plaintext to be all **'A's** (which is `0` in 0-indexed substitution), the math becomes:
Keystream=(Ciphertext−0)=Ciphertext

**The Plan:** If we encrypt a long string of 'A's, the resulting "ciphertext" is actually the raw **Keystream** itself.

- now i need to generate a file containing enough A's to cover the length of the password i want to decrypt:
	- **`python3 -c "print('A'*100)" > plain_a.txt`**
- when i run the binary on this file, the result will be the keystream
	- `EICTDGYIYZKTHNSIRFXYCPFUEOCKRN`

- all i need to do now is to reverse the encryption process, using a simple python script:
```python
ciphertext = 'PNUKLYLWRQKGKBE'  # The secret password
key = 'EICTDGYIYZKTHNS...'      # The 'A' encryption result

# Loop through both strings simultaneously
for c, k in zip(ciphertext, key):
    # 1. Convert letters to 0-25 range (A=0, B=1, etc)
    c_val = ord(c) - ord('A')
    k_val = ord(k) - ord('A')

    # 2. Subtract Key from Cipher to get Plain
    p_val = (c_val - k_val) % 26

    # 3. Convert back to ASCII
    print(chr(p_val + ord('A')), end='')
```

- this gives me the password for the next level: **`LFSRISNOTRANDOM`**
