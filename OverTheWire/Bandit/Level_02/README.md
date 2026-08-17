# Bandit Level 02 → Level 03

## 🎯 Goal

The goal is to find the password for the next level. This time, the password is stored in a file whose name contains spaces.

## 🔎 Finding the Password

I listed the files:

```bash
ls
```

I found a file named:

```text
spaces in this filename
```

Because the filename contains spaces, I need to tell the shell that the whole name belongs to one file.

I used:

```bash
cat "spaces in this filename"
```

The file contained the password for **Bandit Level 03**.

## 🧠 What I Learned

Spaces separate arguments in the Linux shell. Quoting the filename makes the shell treat the entire filename as a single argument.

Another way to do the same thing is:

```bash
cat spaces\ in\ this\ filename
```
