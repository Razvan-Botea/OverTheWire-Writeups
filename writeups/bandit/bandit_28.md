## Bandit Level 28

## Level goal
There is a git repository at `ssh://bandit27-git@localhost/home/bandit27-git/repo` via the port `2220`. The password for the user `bandit27-git` is the same as for the user `bandit27`.

## Solution
- we make a temporary file where we can clone the repository **mktemp -d**
    - we go to that directory and we do the following:
	    - git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
    - we use the password we used for bandit27
    - a new directory appears called "repo"
    - in it there is a file "README"
    - we use **cat README** and find the password to the next level

## Password
    - Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

## New concepts learned
    - Git is a distributed version control system that helps track changes in your code, collaborate with others, and manage project history.
    - git init = initialize a new git repository in the project folder
    - git clone [url] = copy an existing repo from GitHub to the local machine
    - git add [file] or git add . = add changes to the "ready to commit" area
    - git commit -m "message" = save the staged changes with a descriptive message
    - git push origin [branch] = upload the commits to the remote repo
    - git pull origin [branch] = download changes from a remote repo
    - git branch = list all branches in your repo
    - git checkout [branch] or git switch [branch] = switch to a different branch
    - git merge [branch] = combine another branch into the current branch
    - git log = show the commit history
