# Bandit Level 00 → Level 01

## 🎯 Objective

Connect to the Bandit server using SSH and find the password for the next level.

## 🔐 SSH Connection

The challenge provides:

* **Host:** `bandit.labs.overthewire.org`
* **Port:** `2220`
* **Username:** `bandit0`
* **Password:** `bandit0`

Connect using:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Enter the password:

```text
bandit0
```

## 🔎 Find the Password

After logging in, list the files:

```bash
ls
```

A file named `readme` is present.

Read it:

```bash
cat readme
```

The output contains the password for **Bandit Level 01**.

## 🧠 What I Learned

* How to connect to a remote Linux machine using SSH.
* How to specify a custom SSH port using `-p`.
* How to list files with `ls`.
* How to read a file using `cat`.

## 🚩 Flag

The password obtained from `readme` is used to log in to **Bandit Level 01**.
