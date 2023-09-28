## Overthewire Bandit Level 5 to 6 Walkthrough
### Provided Instructions
> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
>
> human-readable /
> 1033 bytes in size /
> not executable

### Detailed Walkthrough
Let's jump right in our terminal:
```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit5@bandit.labs.overthewire.org -p 2220
>{r3d4ct3d_b4nd1t5_p455w0rd}<
bandit5@bandit:~$
```

We use our trusty SSH command with username to ‘bandit5’, and provide the password found in the [previous level](../../../2023/09/28/Overthewire-Bandit-Level-4-to-5-Walkthrough.html), which you can get by playing it yourself!

We are presented with a hierarchy of subdirectories each containing several files, so instead of our usual 'ls -l', we will use the 'ls -lR', the '-R' parameters does a recursive listing of the folders.
> We could use the 'tree' command that has a much prettier output, but it is not installed on the 'bandit' machine and we do not have the rights to install it.
>

```bash
bandit5@bandit:~$ ls -lR
.:
total 4
drwxr-x--- 22 root bandit5 4096 Apr 23 18:04 inhere

./inhere:
total 80
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere00
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere01
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere02
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere03
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere04
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere05
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere06
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere07
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere08
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere09
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere10
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere11
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere12
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere13
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere14
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere15
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere16
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere17
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere18
drwxr-x--- 2 root bandit5 4096 Apr 23 18:04 maybehere19

./inhere/maybehere00:
total 44
-rwxr-x--- 1 root bandit5 1039 Apr 23 18:04 -file1
-rw-r----- 1 root bandit5 9388 Apr 23 18:04 -file2
-rwxr-x--- 1 root bandit5 7378 Apr 23 18:04 -file3

...
Cutting for readability
...
./inhere/maybehere19:
total 48
-rwxr-x--- 1 root bandit5 6302 Apr 23 18:04 -file1
-rw-r----- 1 root bandit5 5594 Apr 23 18:04 -file2
-rwxr-x--- 1 root bandit5 7965 Apr 23 18:04 -file3
-rwxr-x--- 1 root bandit5 7186 Apr 23 18:04 spaces file1
-rw-r----- 1 root bandit5 8785 Apr 23 18:04 spaces file2
-rwxr-x--- 1 root bandit5 2307 Apr 23 18:04 spaces file3
```

In all of this mess, we want to find the file that meets the following criteria:
1) A size of 1033 bytes

For this we can use the ‘find’ command with argument ‘-size 1033c’, ‘c’ being the unit for bytes.

2) Non-executable

The ‘find’ argument for this is ‘-executable’, preceded by a ‘!’ to negate the result and be non-executable

3) Human Readable

We already know that we can use ‘file’ to see the type of file and look for ASCII text files, here we will use the ‘-exec’ parameter to execute ‘file’ command on the result of our ‘find’ command , we pass the result with ‘{} +’, ‘{}’ represents the output and ‘+’ will execute on all lines of the output. This will return the full list of files with all types, to keep only the text files we ‘pipe’ (with the vertical bar '|') our command to a ‘grep "text"’ that will remove all lines that do not contain text. We will use more piping at a later stage.
> Piping takes the output of a command and uses it as the input of the next command, it has tremendous power and numerous uses that we will look into in further levels.

> The 'grep' command looks for text in each line of the input and only displays the line matching the text provided.
```bash
bandit5@bandit:~$ find inhere -size 1033c ! -executable -exec file {} + | grep "text"
inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```

The level is actually easier than that since only the 1033 bytes argument will give you the right file on its own.
```bash
bandit5@bandit:~$ find inhere -size 1033c
inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```

And as day follows night, we cat the file:
```bash
bandit5@bandit:~$ cat inhere/maybehere07/.file2
>{r3d4ct3d_b4nd1t6_p455w0rd}<
```


Congratulations to ourselves for beating the fifth level! One more step towards our destination!

Thank you for reading and have a great & safe day!

For our navigation convenience: [Previous Post (Level 2)](../../../2023/09/27/Overthewire-Bandit-Level-4-to-5-Walkthrough.html) - [Next Post (Level 4)](../../../2023/09/27/Overthewire-Bandit-Level-6-to-7-Walkthrough.html)
