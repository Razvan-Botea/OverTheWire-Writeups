## Bandit Level 13

## Level goal
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Solution
- create a temporary directory in the /tmp directory, with a random name
	- **TEMP_DIR=$(mktemp -d)**
	- **cd "$TEMP_DIR"**
- copy the contents of the data.txt hex dump in the newly created temporary file
	- **cp ~/data.txt file1.txt** 
- use **xxd -r file1.txt > compressed_data.bin** to extract binary text from the hex dump
- use the **file compressed_data.bin** command to find the type of  compression used => gzip archive
- use **mv compressed_data.bin compressed_data.gz** to change the file type and **gunzip compressed_data.gz** to decompress the file
- results a file called "compressed_data"
- use **file compressed_data** => bzip2 compressed

- **mv compressed_data compressed_data.bz2**
- **bunzip2 compressed_data.bz2**
- **file compressed_data** => gzip compressed data

-  **mv compressed_data compressed_data.gz**
- **gunzip compressed_data.gz**
- **file compressed_data** => POSIX tar archive

- **tar -xf compressed_data** => data5.bin
- **file data5.bin** => POSIX tar archive

- **tar -xf data5.bin** => data6.bin
- **file data6.bin** => bzip2

- **mv data6.bin data6.bz2** 
- **bunzip2 data6.bz2** => data6
- **file data6** => POSIX tar archive

- **tar -xf data6** => data8.bin
- **file data8.bin** => gzip

- **mv data8.bin data8.gz**
- **gunzip data8.gz** => data8
- **file data8** => ASCII text
- cat data8

- cd ~
- rm -rf "$TEMP_DIR"

## Password
    - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## New concepts learned
- hex dump = a textual representation of binary data, where the contents of a file (or a section of memory) are displayed as a sequence of hexadecimal numbers
- the hex dump translates the binary data from the memory into base-16 format

**e.g.** 00000000:          f8b 0808 0933 9f68 0203 6461 7461 322e            .....3.h..data2.
- the left column represents the offset, the memory address where this line of data starts
- the middle column are the hexadecimal bytes, the actual data; each 2 character pair represents a single byte of the original binary file
- the right column is the ASCII representation of the data, the dots replace non-human-readable characters

- "mktemp -d" creates a temporary directory
- /tmp is a directory where any user or application can store temporary data
