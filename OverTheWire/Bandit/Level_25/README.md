# Bandit Level 25 → Level 26

## Goal

The password for the next level is available by logging in as `bandit26`. The SSH private key for `bandit26` is available in the home directory of `bandit25`.

## What I Did

First, I logged in as `bandit25` and listed the files:

```bash
ls
```

I found:

```text
bandit26.sshkey
```

I checked the permissions:

```bash
ls -l bandit26.sshkey
```

Then I used the private key to connect to `bandit26` from outside the bandit server:

```bash
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

At first, the connection closed immediately. I learned that this happened because `bandit26` does not use a normal Bash shell. Its login shell runs a program called `showtext`, which opens the `more` pager.

To make `more` stay open, I made my terminal window very small and connected again:

```bash
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

This time I saw:

```text
--More--
```

While `more` was running, I pressed:

```text
v
```

This opened the text in Vim.

## Important Trick

Inside Vim, I changed the shell to Bash:

```vim
:set shell=/bin/bash
```

Then I opened a shell:

```vim
:shell
```

Now I had a normal shell:

```text
bandit26@bandit:~$
```

## What I Learned

The important part of this level was understanding that the SSH connection was not actually failing. The login shell of `bandit26` was starting `more` and then closing.

The small terminal caused `more` to enter paging mode. The `v` key opened Vim, and Vim allowed me to start a Bash shell.

## Commands Used

```bash
ls
ls -l bandit26.sshkey
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

Inside Vim:

```vim
:set shell=/bin/bash
:shell
```
