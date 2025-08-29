## Bandit Level 31

## Level goal
There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo` via the port `2220`. The password for the user `bandit30-git` is the same as for the user `bandit30`.
Clone the repository and find the password for the next level.

## Solution
   - we make a temporary file where we can clone the repository **mktemp -d**
    - we go to that directory and we do the following:
	    - git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
    - we use the password we used for bandit30
    - a new directory appears called "repo"
    - in it there is a file "README.md"
    - we use **cat README.md** to read the file
    - there is no useful information in there
    - we check the commit history with **git log -a**
    - nothing useful there either
    - we check for other branches with **git branch -a**, still no luck
    - we check the git tag with **git tag**
    - we see a tag called "secret"
    - we check it out using **git show secret** and we find the password 

## Password
    - fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
