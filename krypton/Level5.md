# Description
FA can break a known key length as well. Lets try one last polyalphabetic cipher, but this time the key length is unknown. Note: the text is writen in American English

# Solution

- this is similar to the previous level, with the added difficulty of not knowing the length of the key
- this can be found with Kasiski analysis on the intercepted ciphertext messages
**Kasiski Analysis** is a cryptanalysis technique used to break polyalphabetic substitution ciphers.
Step 1: Find Repeated Ciphertext Sequences
- Search for identical sequences of 3+ characters in the ciphertext
- Record the distances between these repetitions
Step 2: Determine Possible Keyword Lengths
- The distance between repetitions is often a multiple of the keyword length
- Calculate the greatest common divisors of these distances
- Common factors suggest possible keyword lengths
Step 3: Confirm Keyword Length
- Use **Friedman Test** (Kappa test) to statistically confirm the most likely keyword length
- This analyzes the **Index of Coincidence** (probability that two randomly selected letters are identical)
Step 4: Break Into Monoalphabetic Ciphers
- Once you know the keyword length (say, `n`), group every `n`th letter together
- Each group was encrypted with the same shift (same keyword letter)
- Apply standard frequency analysis to each group separately

- the site used for the previous level (https://www.dcode.fr/vigenere-cipher) can also do Kasiski analysis
- for this, i enter the intercepted messages in the Ciphertext box, and select the Vigenere Cryptanalysis (Kasiski's Test) option
- this gives me the probability for each key length (between 1 and 25)
- the most probable key length is 4, followed by 3, 6, 5 and 9

- now i need to repeat the process from the previous level
- i will first try a key length of 4, but this does not seem to be working
- i then tried with 3, 6, and 5, none of them working
- in the end, the 9 letter keyword was the right choice
- i found the keyword: **KEYLENGTH**

- with this, i was able to decrypt the ciphertext and get the password for the next level
- i used the "Knowing the key" option
- password: **RANDOM**
