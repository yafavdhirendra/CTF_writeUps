# Bandit Level 03 → Level 04

## 🎯 Goal

The password for the next level is stored in a hidden file inside the `inhere` directory.

## 🔎 Finding the Hidden File

First, I checked the available files:

```bash
ls
```

I found the `inhere` directory, so I entered it:

```bash
cd inhere
```

Running `ls` didn't show the password file. This is because the file is hidden.

To display hidden files, I used:

```bash
ls -la
```

This showed a hidden file named:

```text
.hidden
```

I read it with:

```bash
cat .hidden
```

The output was the password for **Bandit Level 04**.

## 🧠 What I Learned

Linux hides files whose names start with `.` by default. The `-a` option of `ls` displays hidden files, while `-l` provides detailed information.

Useful command:

```bash
ls -la
```
