## Overthewire Bandit Level 1 to 2 Walkthrough
### Provided Instructions
> The password for the next level is stored in a file called - located in the home directory.

### Detailed Walkthrough
Let's jump right in our terminal:
```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit1@bandit.labs.overthewire.org -p 2220
>{r3d4ct3d_b4nd1t1_p455w0rd}<
bandit1@bandit:~$
```

We use the same ssh command as in the [previous level](../../../2023/09/27/Overthewire-Bandit-Level-0-to-1-Walkthrough.html), changing the username to ‘bandit1’, and we provide the password found in the previous level, which you can get by playing it yourself!

As usual we use 'ls' to list the content of the home directory:
```bash
bandit1@bandit:~$ ls
-
```

This confirms the instructions, mentionning that the password is in a file called ‘-‘, if we try the ‘cat -‘ command, it will stall and we will need to kill it with Ctrl+C. This is because the ‘-‘ symbol is reserved for parameters in any Unix command (such as the -p that we used for our SSH port).
```bash
bandit1@bandit:~$ cat -
^C // I pressed Ctrl+C
bandit1@bandit:~$
```
The solution is to use the ‘cat ./-‘ command, ‘.’ Represents the current directory in Unix (Linux is based on [Unix](https://en.wikipedia.org/wiki/Unix)), so ‘./-‘ tells the system that we want to display the ‘-‘ file in the current directory and not specify a parameter.

```bash
bandit1@bandit:~$ cat ./-
>{r3d4ct3d_b4nd1t2_p455w0rd}<
```

Congratulations to ourselves for beating the second level! One more step towards our destination!

Thank you for reading and have a great & safe day!

For our navigation convenience: [Previous Post (Level 0)](../../../2023/09/27/Overthewire-Bandit-Level-0-to-1-Walkthrough.html) - [Next Post (Level 2)](../../../2023/09/27/Overthewire-Bandit-Level-2-to-3-Walkthrough.html)
