## Bandit Level 10

## Level goal
The password for the next level is stored in the file **data.txt** in one of thefew human-readable strings, preceded by several ‘=’ characters.

## Solution
    - **strings --unicode=invalid data.txt | grep "="** 
	    - "strings --unicode=invalid" removes the non-human-readable characters from the file
    	- we pipe the remaining ASCII characters into the grep function and look for "=" characters

## Password
    - FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## New concepts learned
    - strings = print the sequence of printable characters in files
        - "--unicode" can dctate what kind of characters to print
