# Description

The main weakness of a simple substitution cipher is repeated use of a simple key. In the previous exercise you were able to introduce arbitrary plaintext to expose the key. In this example, the cipher mechanism is not available to you, the attacker.
However, you have been lucky. You have intercepted more than one message. The password to the next level is found in the file ‘krypton4’. You have also found 3 other files. (found1, found2, found3)
You know the following important details:
- The message plaintexts are in American English (*** very important) 
- They were produced from the same key (*** even better!)

# Solution

- because I have more than one intercepted message containing ciphertext, i can break the cipher using frequency analysis 
- for this, i need to count the number of appearances for each letter in the ciphertext, and then compare the resulting ordered list to the frequency of letters in plain English
- to create the list, i used the following command:
```bash
for i in {A..Z}; do cat found1 found2 found3 | tr -cd $i | wc -c | tr -d '\n'; printf " $i \n"; done | sort -nr
```
- with this, i got the following list: **SQJUBNGCDZVWMYTXKELAFIORHP**
- in plain English, this is the order: **ETAOINSRHDLUCMFYWGPBVKXQJZ**
- now all i need to do is replace the letters in the ciphertext with their equivalent frequency letters in English
```bash
cat krypton4 | tr 'SQJUBNGCDZVWMYTXKELAFIORHP' 'ETAOINSRHDLUCMFYWGPBVKXQJZ'
```
- this does not give me an English text, but this just means that the order from the frequency analysis does not fit perfectly with the plain English order
- this can be solved by slightly changing the order
- first of all, the first words form the word "WELL"
- this could only be followed by the word "DONE"
- if i change the letters accordingly, and then change the few others that don't make sense, more and more of the text starts looking like english
- in the end, i get: **WELLD ONETH ELEVE LFOUR PASSW ORDIS BRUTE**
- so the password for the next level is: **BRUTE**
