## Bandit Level 12

## Level goal
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Solution
    - "tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt"
        - use regex to simply replace each character in the file with the letter rotated backwards 13 positions
        - you can also use https://cyberchef.org/ 's ROT13 option

## Password
    - 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## New concepts learned
Regex (Regular Expressions) are patterns used to match, search, and manipulate text based on specific rules
    Patterns: Define rules for matching text
    Metacharacters: Special characters with meaning (e.g., ., *, +, ?)
    Character classes: [a-z], [0-9], \d, \w
    Quantifiers: * (0 or more), + (1 or more), ? (0 or 1)
    Anchors: ^ (start of line), $ (end of line)

