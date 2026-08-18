# Bandit Level 08 → Level 09

## 🎯 Goal

The password for the next level is stored in `data.txt` and is the only line that occurs exactly once.

## 🔎 Finding the Unique Line

First, I checked the files in the current directory:

```bash
ls
```

I found:

```text
data.txt
```

Since the file contains many lines and I needed to find the line that appears only once, I used `strings`, `sort`, and `uniq` together:

```bash
strings data.txt | sort | uniq -u
```

The command returned:

```text
EjmOSvuAu******irRe9T03kxl
```

This was the password for **Bandit Level 09**.

## 🧠 What I Learned

I learned how to combine multiple Linux commands using pipes (`|`).

* `strings` extracts readable text from the file.
* `sort` sorts the lines so duplicate lines are placed together.
* `uniq -u` displays only the lines that occur exactly once.

The complete command was:

```bash
strings data.txt | sort | uniq -u
```

This is useful when a challenge asks me to find a unique line among many repeated lines.
