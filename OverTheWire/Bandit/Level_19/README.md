# Bandit Level 19 → Level 20

## 🎯 Objective

Find the password for the next level. A Set-UID program called `bandit20-do` is available in the home directory.

##  Find the Password

First, list the files:

```bash
ls -al
```

I found:

```text
-rwsr-x--- 1 bandit20 bandit19 14880 bandit20-do
```

The `s` in the permissions shows that `bandit20-do` is a **Set-UID executable**.

Running it without a command shows how it works:

```bash
./bandit20-do
```

It says:

```text
Run a command as another user.
Example: ./bandit20-do whoami
```



Instead, I used `cat` to directly read the password file:

```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220 ./bandit20-do cat /etc/bandit_pass/bandit20
```

This returned the password for **Bandit Level 20**.

## 🧠 What I Learned

* What a Set-UID executable is.
* How file permissions can allow a program to run with another user's privileges.

* A privileged executable can be used to run commands such as `cat`.

## 🚩 Flag

The output of the `cat` command is the password for **Bandit Level 20**.
