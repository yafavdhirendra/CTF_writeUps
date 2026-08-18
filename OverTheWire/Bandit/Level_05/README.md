# Bandit Level 05 → Level 06

## 🎯 Goal

The password for the next level is stored in a file somewhere under the `inhere` directory.

The file has these properties:

* Human-readable
* 1033 bytes in size
* Not executable

## 🔎 Finding the Correct File

First, I checked the current directory:

```bash
ls
```

I found the `inhere` directory, so I entered it:

```bash
cd inhere
```

Then I checked the contents:

```bash
ls
```

There were several directories and files inside `inhere`. Instead of checking every file manually, I used the `find` command to search for a file matching the given conditions.

I used:

```bash
find . -type f -size 1033c ! -executable
```

Here:

* `.` means search from the current directory.
* `-type f` searches only for regular files.
* `-size 1033c` finds files that are exactly 1033 bytes.
* `! -executable` excludes executable files.

The command returned the file containing the password.

I then used `cat` with the returned path:

```bash
cat ./maybehere07/.file2
```

The output was the password for **Bandit Level 06**.

## 🧠 What I Learned

The `find` command is very useful when a challenge gives specific properties such as file size, type, permissions, or location.

A useful command from this level is:

```bash
find . -type f -size 1033c ! -executable
```
