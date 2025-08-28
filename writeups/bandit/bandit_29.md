## Bandit Level 29

## Level goal
There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.
Clone the repository and find the password for the next level.

## Solution
    - we make a temporary file where we can clone the repository **mktemp -d**
    - we go to that directory and we do the following:
	    - git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
    - we use the password we used for bandit28
    - a new directory appears called "repo"
    - in it there is a file "README.md"
    - we use **cat README** to read teh contents of the file 
    - we cannot see the password
    - we use **git log** to see the changes made to the repo
    - the one called "fix info leak" sounds interesting
    - we use **git log -p -1** 
	    - git log => shows the commit history
	    - -p => displays the actual changes made to the file
	    - -1 => limits output to the most recent commit 

## Password
    - 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
