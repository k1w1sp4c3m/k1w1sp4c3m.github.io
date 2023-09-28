## Overthewire Bandit Level 4 to 5 Walkthrough
### Provided Instructions
> The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

### Detailed Walkthrough
Let's jump right in our terminal:
```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit4@bandit.labs.overthewire.org -p 2220
>{r3d4ct3d_b4nd1t4_p455w0rd}<
bandit4@bandit:~$
```

We use our trusty SSH command with username to ‘bandit4’, and provide the password found in the [previous level](../../../2023/09/27/Overthewire-Bandit-Level-3-to-4-Walkthrough.html), which you can get by playing it yourself!

As usual we use 'ls' to list the content of the home directory:
```bash
bandit4@bandit:~$ ls
inhere
```
We see the 'inhere' directory mentionned in the instruction.

We are looking for a human readable file in the ‘inhere’ directory.

First let’s list the files with a ‘ls -l inhere’, the ‘-l’ parameter will display a list with line returns and some info such as permission instead of files on a single line.

```bash
bandit4@bandit:~$ ls -l inhere/
total 40
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file00
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file01
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file02
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file03
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file04
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file05
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file06
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file07
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file08
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file09
```

We notice a pattern in the filenames: ‘-file0*’, the ‘*’ character can replace any character in UNIX, it is a wildcard.

We then run the ‘file’ command on this pattern to see all file types in a single command.
```bash
bandit4@bandit:~$ file inhere/-file0*
inhere/-file00: data
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: Non-ISO extended-ASCII text, with no line terminators
```

However ‘ls’ does not show hidden files by default, we have to specify the ‘- a’ (for ‘all’) parameter as follows ‘ls -a’:
```bash
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
```
Only ‘-file07’ is of type ‘ASCII Text’ so we display it with ‘cat’.

> if you chose to go into the ‘inhere’ directory with ‘cd’, do remember to use ‘./-file0*’ and ‘./-file07’ in your ‘file’ and ‘cat’ commands respectively. See level 2 for the explanation.

Finally we cat the file:
```bash
bandit4@bandit:~$ cat inhere/-file07
>{r3d4ct3d_b4nd1t5_p455w0rd}<
```

Remark: if we chose to move to the folder, the level can be solved as followed:
```bash
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls -l
total 40
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file00
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file01
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file02
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file03
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file04
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file05
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file06
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file07
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file08
-rw-r----- 1 bandit5 bandit4 33 Apr 23 18:04 -file09
bandit4@bandit:~/inhere$ file ./-file0*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: Non-ISO extended-ASCII text, with no line terminators
bandit4@bandit:~/inhere$ cat ./-file07
>{r3d4ct3d_b4nd1t5_p455w0rd}<
```


Congratulations to ourselves for beating the fourth level! One more step towards our destination!

Thank you for reading and have a great & safe day!

For our navigation convenience: [Previous Post (Level 2)](../../../2023/09/27/Overthewire-Bandit-Level-3-to-4-Walkthrough.html) - [Next Post (Level 4)](../../../2023/09/27/Coming-Soon.html)
