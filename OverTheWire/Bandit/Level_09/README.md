# Bandit Level 09 → Level 10

## 🎯 Goal

The password for the next level is stored in `data.txt` in one of the few human-readable strings, preceded by several `=` characters.

## 🔎 Finding the Password

First, I checked the files in the current directory:

```bash id="n7h4b1"
ls
```

I found:

```text id="r4j9sc"
data.txt
```

Since the file contains a mixture of readable and unreadable data, I used the `strings` command to extract human-readable text.

Then I searched for lines containing several `=` characters:

```bash id="n8d2lq"
strings data.txt | grep -E '==='
```

The command returned:

```text id="c7j8px"
cL0========== the
========== password
>========== is
R========== B0s2khmb*******ZKhndE3BG
```

The password was at the end of the last line:

```text id="5h2r6w"
B0s*********ndE3BG
```

This was the password for **Bandit Level 10**.

## 🧠 What I Learned

I learned how to use `grep` with a regular expression to search for a specific pattern.

The important command was:

```bash id="r8h1zf"
strings data.txt | grep -E '==='
```

Here:

* `strings` extracts readable text.
* `grep` searches for matching text.
* `-E` enables extended regular expressions.
* `===` searches for text containing three or more consecutive `=` characters.

This helped me quickly identify the line containing the password.
