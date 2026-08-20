## Bandit Level 18 → Level 19
## 🎯 Goal

The password for the next level is stored in the **readme file** in the home directory.

However, the normal **SSH login** is restricted and the connection closes immediately after authentication.

## Trying to Log In

First, I tried to connect normally:
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```
After entering the password, the connection was immediately closed:
```bash
Byebye !
Connection to bandit.labs.overthewire.org closed.
```
This showed that I could not use the normal interactive shell.

## Executing a Command Directly

Instead of opening an interactive shell, I used **SSH to execute** the cat readme command directly on the remote machine:
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```
The command returned:
```
KpsOf_Lvl_19_pass_dxZI
```
This was the password for Bandit Level 19.

## What I Learned

I learned that SSH can execute a specific command directly on a remote machine without opening an interactive shell.

The important command was:
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```
This allowed me to read the readme file even though the normal SSH session was automatically closed.

## Key Concept

**SSH Remote Command Execution** allows commands to be executed directly on a remote system through SSH without starting an interactive shell.