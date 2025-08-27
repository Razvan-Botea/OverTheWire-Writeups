## Bandit Level 9

## Level goal
The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Solution
    - "sort -d data.txt | uniq -u"
	    - "sort -d" sorts the data in alphabetical order => all identical lines are next to each other
	    - pipe the result into the next function
	    - "uniq -u" only print unique lines (checks adjacent lines only)

## Password
    - 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## New concepts learrned
    - sort = sort lines of text
        "-d" orders the output alphabetically
    - pipes = connect the output of one command directly to the input of another command, allowing us to chain commands together efficiently
    - uniq = report or omit repeated lines
        - "-u" only prints unique lines
