# Bandit Level 27 → Level 28

## Goal

There is a Git repository at:

```text
ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

The password for `bandit27-git` is the same as the password for `bandit27`.

The goal is to clone the repository and find the password for the next level.

## What I Did

First, I cloned the Git repository from my local Kali machine:

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

I entered the password of `bandit27` when Git asked for the password.

The repository was successfully cloned.

Then I entered the repository:

```bash
cd repo
```

I checked the files:

```bash
ls
```

Output:

```text
README
```

I read the README file:

```bash
cat README
```

Output:

```text
The password to the next level is: y8Yd2s***Lvl_28_pass_IGIeQ
```



## What I Learned

This level taught me how to clone a Git repository using SSH.

The important part of the Git SSH URL was:

```text
bandit27-git@bandit.labs.overthewire.org:2220
```

Port `2220` is important because OverTheWire's SSH service runs on that port.

---

