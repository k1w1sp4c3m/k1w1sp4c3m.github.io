## Overthewire Bandit Level 0 to 1 Walkthrough

### Provided Instructions

> The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.
> The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
### Detailed Walkthrough

The objective of this level is to learn how to use SSH to connect to the OverTheWire system and play the game.

SSH or [Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell) is protocol used to connect remotely (and securely) to another computer and execute commands on it.

> To use SSH you need to be in a terminal, follow one of the instructions below depending on your operating system:
> On Windows, press the Windows key and type "powershell" then enter to launch PowerShell
> On MacOS, press Cmd + Space and type "terminal" to launch the Terminal
> On Linux, pres Alt + Shift + T to launch the Terminal
> You are now ready to type and execute commands!

We use the command ssh with the following syntax:

```bash
ssh <user>@<host> -p <port>
```

The user is ‘bandit0’ and will change for each level.

The host & port are provided on the instruction page: 

![Bandit SSH information](../../../img/bandit_ssh.png)

Which gives us the following command:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220

```

We press ‘Enter’ to execute the command and get prompted to enter the password for user ‘bandit0’ which is ‘bandit0’ as provided in the instructions.

```bash
bandit0
```

> Optionally we can run the ‘ls’ command to see the content of the directory, here only the ‘readme’ file. It is a good practice to use in all further levels to get the lay of the land before starting to solve the level.

Finally we use the cat command to display the content of the ‘readme’ file and get the password. Congratulations to ourselves for beating the first level!
