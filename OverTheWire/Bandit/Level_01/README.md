# Bandit Level 01 → Level 02

## 🎯 Goal

The goal is to find the password for the next level. After logging in, there is a file called `-`.

## 🔎 Finding the Password

I first listed the files:

```bash
ls
```

The file `-` was present.

Normally, using:

```bash
cat -
```

doesn't work as expected because `-` is commonly interpreted as standard input.

So I specified the file path explicitly:

```bash
cat ./-
```

This displayed the password for **Bandit Level 02**.

## 🧠 What I Learned

A filename beginning with `-` can be interpreted as an option or special input by some commands. Using `./` tells the command that it is a file in the current directory.
