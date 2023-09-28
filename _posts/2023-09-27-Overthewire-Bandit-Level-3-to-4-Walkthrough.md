## Overthewire Bandit Level 3 to 4 Walkthrough
### Provided Instructions
> The password for the next level is stored in a hidden file in the 'inhere' directory.

### Detailed Walkthrough
Let's jump right in our terminal:
```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit3@bandit.labs.overthewire.org -p 2220
>{r3d4ct3d_b4nd1t3_p455w0rd}<
bandit3@bandit:~$
```

We use our trusty SSH command with username to ‘bandit3’, and provide the password found in the [previous level](../../../2023/09/27/Overthewire-Bandit-Level-2-to-3-Walkthrough.html), which you can get by playing it yourself!

As usual we use 'ls' to list the content of the home directory:
```bash
bandit3@bandit:~$ ls
inhere
```

We see the 'inhere' directory mentionned in the instruction.

We can move into this directory using the 'cd' (change directory) command followed by the name of the folder 'inhere'.
```bash
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$
```
Notice that the prompt changes with our new location!

The gist of this level is how to find the hidden file, which we can do using ‘ls’:
```bash
bandit3@bandit:~/inhere$ ls
```

However ‘ls’ does not show hidden files by default, we have to specify the ‘- a’ (for ‘all’) parameter as follows ‘ls -a’:
```bash
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
```

Finally we cat the file:
```bash
bandit3@bandit:~/inhere$ cat .hidden
>{r3d4ct3d_b4nd1t4_p455w0rd}<
```

Remark: moving to the folder is optional, and we can solve the level as follows (type 'cd' to go back to the home directory if needed):
```bash
bandit3@bandit:~$ ls -a inhere/
.  ..  .hidden
bandit3@bandit:~$ cat inhere/.hidden
>{r3d4ct3d_b4nd1t4_p455w0rd}<
```


Congratulations to ourselves for beating the third level! One more step towards our destination!

Thank you for reading and have a great & safe day!

For our navigation convenience: [Previous Post (Level 2)](../../../2023/09/27/Overthewire-Bandit-Level-2-to-3-Walkthrough.html) - [Next Post (Level 4)](../../../2023/09/27/Coming-Soon.html)
