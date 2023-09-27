## Overthewire Bandit Level 2 to 3 Walkthrough
### Provided Instructions
> The password for the next level is stored in a file called 'spaces in this filename' located in the home directory.

### Detailed Walkthrough
Let's jump right in our terminal:
```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit2@bandit.labs.overthewire.org -p 2220
>{r3d4ct3d_b4nd1t2_p455w0rd}<
bandit2@bandit:~$
```

We use our trusty SSH command with username to ‘bandit1’, and provide the password found in the [previous level](../../../2023/09/27/Overthewire-Bandit-Level-1-to-2-Walkthrough.html), which you can get by playing it yourself!

As usual we use 'ls' to list the content of the home directory:
```bash
bandit2@bandit:~$ ls
spaces in this filename
```

We see that there are indeed spaces in the file name that you need to display.

By default spaces in Unix commands separate parameters and arguments, as such if you run ‘cat spaces in this filename’ the command will try and display the content of 4 files successively named ‘spaces’, ‘in’, ‘this’ and ‘filename’, none of which exist.
```bash
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
```

The solution is to use the ‘\’ backslash which is Unix’s escape character. It means that the next character after that will be escaped, and will not have its default behavior. As such the ‘cat spaces\ in\ this\ filename’ command will do the trick.

> This feels like a good time to introduce autocomplete. If you start typing ‘cat sp’ (or even just ‘cat s’) and then press the Tab button your terminal autocompletes the full name of the file including escape characters if needed!

```bash
bandit2@bandit:~$ cat spaces\ in\ this\ filename
>{r3d4ct3d_b4nd1t3_p455w0rd}<
```

Congratulations to ourselves for beating the third level! One more step towards our destination!

Thank you for reading and have a great & safe day!

For our navigation convenience: [Previous Post (Level 1)](../../../2023/09/27/Overthewire-Bandit-Level-1-to-2-Walkthrough.html) - [Next Post (Level 3)](../../../2023/09/27/Coming-Soon.html)
