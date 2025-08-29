## Bandit Level 6

## Level goal
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
    - human-readable
	- 1033 bytes in size
	- not executable

## Solution
    - used "cd" to go to the **inhere** directory
    - used "find ! -executable -size 1033c"
        - "! -executable" negates the executable option and looks for non-executable files
        - the "c" added to the size option tells it to look for the specified number of bytes
    - used **cat ".file2"** to dispaly the contents of the file we fonud using the command above

## Password
    - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## New concepts learned
    - find = searches for files in a directory hierarchy
    - "!" before an option reverses the effect of that option
