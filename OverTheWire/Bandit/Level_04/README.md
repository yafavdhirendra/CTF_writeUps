# Bandit Level 04 → Level 05

## 🎯 Goal

The password for the next level is stored in the **only human-readable file** inside the `inhere` directory.

## 🔎 Finding the Human-Readable File

First, I checked the files in the current directory:

```bash
ls
```

I found the `inhere` directory, so I entered it:

```bash
cd inhere
```

Then I listed the files:

```bash
ls
```

There were several files:

```text
-file00 -file01 -file02 -file03 -file04 -file05 -file06 -file07 -file08 -file09
```

The filenames start with `-`, so I used `./` to make sure Linux treats them as filenames rather than command options.

I first checked the files with:

```bash
cat ./-file0*
```

Most of the output looked like binary or unreadable data. To find the file containing readable text, I used the `strings` command:

```bash
strings ./-file0*
```

The output included:

```text
;(1\~5
6C7h9GD5...
93j%A
```

The clearly readable password was:

```text
6C7h9GD5...
```

This was the password needed to log in to **Bandit Level 05**.

## 🧠 What I Learned

The `strings` command is useful for finding human-readable text inside binary or otherwise unreadable files.

When filenames begin with `-`, using `./filename` is a safe way to specify the file explicitly.

Useful command:

```bash
strings ./-file0*
```

The important clue in this level was that only one file contained meaningful human-readable text, while the other files contained mostly binary data.
