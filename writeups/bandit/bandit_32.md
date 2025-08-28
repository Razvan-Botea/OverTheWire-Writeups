## Bandit Level 32

## Level goal
There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.
Clone the repository and find the password for the next level.

## Solution
    - we make a temporary file where we can clone the repository **mktemp -d**
    - we go to that directory and we do the following:
    	- git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
    - we use the password we used for bandit31
    - a new directory appears called "repo"
    - in it there is a file "README.md"
    - we use **cat README.md** and find the message: 

This time your task is to push a file to the remote repository.
Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

    - we create the .txt file as specified
    - we add the file to the staging area **git add -f key.txt"
    - we commit the changes with a message **git commit -m "Message"**
    - we push to the master branch **git push origin master**

## Password
    - 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
