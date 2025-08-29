## Bandit Level 30

## Level goal
There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo` via the port `2220`. The password for the user `bandit29-git` is the same as for the user `bandit29`.
Clone the repository and find the password for the next level.

## Solution
    - we make a temporary file where we can clone the repository **mktemp -d**
    - we go to that directory and we do the following:
	    - git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
    - we use the password we used for bandit29
    - a new directory appears called "repo"
    - in it there is a file "README.md"
    - we use **cat README.md** and find the password to the next level
    - there is no password, but the phrase **<no_passwords in production>** tells us there could be multiple branches
    - we use **git branch -a** to see what other branches are there
    - from the list, the one called "dev" looks the most promising
    - we use **git checkout dev** to change to that branch
    - **git log** reveals a commit called "add data needed for development"
    - we use **git log -p -1** to check it out, and we find the password

## Password
    - qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
