# Bandit Level 06 → Level 07

## 🎯 Goal

The password for the next level is stored **somewhere on the server** and has these properties:

* Owned by user `bandit7`
* Owned by group `bandit6`
* Exactly 33 bytes in size

## 🔎 Finding the Password File

First, I checked the files in my home directory:

```bash
ls -al
```

I saw files such as `.bashrc`, `.profile`, and `.bash_logout`, but these were not the target file.


Since the challenge says the password can be **anywhere on the server**, I needed to search from the root directory `/`.

I first tried searching from root directory:

```bash
cat $(find / -user bandit7 -group bandit6 -size 33c 2>/dev/null)
```

The `find` command searched from `/` and looked for files matching all three conditions:

* `-user bandit7` → owned by `bandit7`
* `-group bandit6` → owned by group `bandit6`
* `-size 33c` → exactly 33 bytes
* `2>/dev/null` → hides permission-denied error messages

The command directly displayed the password:

```text
Bmnnvf82**Qlfxg*******1u9pr3E3
```

This was the password for **Bandit Level 07**.

## 🧠 What I Learned

I learned how to use `find` with multiple conditions to locate a specific file anywhere on a Linux system.

I also learned that `/` represents the root of the filesystem, so using:

```bash
find /
```

allows me to search across the entire filesystem.

The `2>/dev/null` technique is useful for hiding permission-denied errors when searching directories that I cannot access.

