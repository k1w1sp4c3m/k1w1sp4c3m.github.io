## Overthewire Bandit Level 0 to 1 Walkthrough
### Provided Instructions
> The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

> The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### Detailed Walkthrough
The objective of this level is to learn how to use SSH to connect to the OverTheWire system and play the game.

SSH or [Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell) is protocol used to connect remotely (and securely) to another computer and execute commands on it.

To use SSH you need to be in a terminal, follow one of the instructions below depending on your operating system:
- On Windows, press the Windows key and type "powershell" then enter to launch the PowerShell Terminal
- On MacOS, press Cmd + Space and type "terminal" to launch the Terminal
- On Linux, pres Alt + Shift + T to launch the Terminal

You are now ready to type and execute commands, and should see your command prompt (below example is on Linux):
```bash
k1w1sp4c3m@p4r48377um:~$ 
```

We use the command ssh with the following syntax:

```bash
ssh <user>@<host> -p <port>
```

The user is 'bandit0' and will change for each level.

The host & port are provided on the instruction page: bandit.labs.overthewire.org on port 2220 (note that SSH usually runs on Port 22).

Which gives us the following command:

```bash
k1w1sp4c3m@p4r48377um:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password:
```

We press Enter to execute the command, we are greeted with a nice ASCII "bandit" and get prompted to enter the password for user 'bandit0' which is 'bandit0' as provided in the instructions.

```bash
bandit0@bandit.labs.overthewire.org's password: bandit0
...
HUGE INFORMATION BLOCK
...
bandit0@bandit:~$
```

We enter the password and get a HUGE INFORMATION BLOCK which we are encouraged to read.

<details>
  <summary>A small piece on why we post solutions even though it is against the rules.</summary>
  
  To be fair, we have to mention that we do not respect the "DONT POST SPOILERS! This includes writeups of your solution on your blog or website!" while we do not post passwords (they change regularly anyway), we do post solutions for 2 reasons: 1. It allows us to retain the knowledge a lot better and 2. It provides our fellow tinkerers with some insight into what they are doing and can be used as pointers if they are blocked. We really believe that looking at a solution after trying ourselves for a while is beneficial for learning and unblocking the following levels to learn even more!
  
</details>
-

We now have the command prompt for user 'bandit0' on the 'bandit' computer.

Here we can run the 'ls' listing command to see the content of the user's home directory. It is a good practice to use in all further levels to get the lay of the land before starting to solve the level.
```bash
bandit0@bandit:~$ ls
readme
```
Only the ‘readme’ file is present. 

Finally we use the 'cat' printing command to display the content of the ‘readme’ file and get the password.
```bash
bandit0@bandit:~$ cat readme
>{r3d4ct3d_b4nd1t0_p455w0rd}<
```

Congratulations to ourselves for beating the first level!

For our navigation convenience: [Previous Post (Introduction)](../../../2023/09/26/Overthewire-Bandit-Wargame-Walkthrough.html) - [Next Post (Level1)](../../../2023/09/27/Coming-Soon.html)
