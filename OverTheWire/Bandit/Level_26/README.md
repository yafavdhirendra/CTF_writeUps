# Bandit Level 26 → Level 27

## Goal

The goal is to obtain the password for `bandit27`.

After getting a normal shell as `bandit26`, I needed to find a way to access the password file for the next level.

## What I Did

First, I checked the files in the home directory:

```bash
ls -la
```

I found:

```text
bandit27-do
text.txt
```

I checked the permissions of `bandit27-do`:

```bash
ls -l bandit27-do
```

The file had the **SUID** permission.

SUID means that when the program is executed, it runs with the privileges of the file owner rather than only the privileges of the current user.

I then used `bandit27-do` to run `cat` against the password file:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

This displayed the password for `bandit27`.

## Why It Worked

Normally, `bandit26` cannot directly read:

```text
/etc/bandit_pass/bandit27
```

But `bandit27-do` has SUID permissions. Therefore, when I executed it, the command ran with the required privileges.

The important command was:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

## What I Learned

In this level, I learned about **SUID binaries** and how file permissions can affect the privileges of a program.

I also learned that a SUID program can sometimes be used to execute another command with the privileges of the program owner.

## Commands Used

```bash
ls -la
ls -l bandit27-do
./bandit27-do cat /etc/bandit_pass/bandit27
```
