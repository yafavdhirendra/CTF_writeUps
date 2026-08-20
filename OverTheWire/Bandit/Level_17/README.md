# Bandit Level 17 → Level 18

## 🎯 Goal

The password for the next level is stored in `passwords.new`.

The challenge provides two files:

```text
passwords.old
passwords.new
```

The password is the line that is different between these two files.

##  Finding the Changed Password

First, I checked the files in the current directory:

```bash id="a7x2nm"
ls
```

I found:

```text id="r0m1qs"
passwords.new
passwords.old
```

Instead of manually comparing the two files, I used the `diff` command:

```bash id="9v8x2p"
diff passwords.old passwords.new
```

The output was:

```text id="c4y6rn"
42c42
< qOg5p_old_line_in 42_yoUB8D
---
> OQxXZj_New_line_in_42_ZITXI
```

This means that **line 42** is different between the two files.




Therefore, the password for **Bandit Level 18** is:

```text id="z4w6hc"
OQxXZj_Lvl_18_pass_ZITXI
```

## 🧠 What I Learned

I learned how to compare two files using the `diff` command.

The main command was:

```bash id="x8q3lm"
diff passwords.old passwords.new
```

The symbols in the output help identify the differences:

* `<` shows the line from the first file (`passwords.old`).
* `>` shows the line from the second file (`passwords.new`).
* `42c42` means line 42 in the first file was changed compared with line 42 in the second file.

This is much faster than manually checking both files line by line.
