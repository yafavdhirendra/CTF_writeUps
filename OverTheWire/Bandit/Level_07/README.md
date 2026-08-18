# Bandit Level 07 → Level 08

## 🎯 Goal

The password for the next level is stored in the file `data.txt` next to the word `millionth`.

## 🔎 Finding the Password

First, I checked the files in my home directory:

```bash
ls
```

I found a file named:

```text
data.txt
```

I checked its details with:

```bash
ls -al
```

Then I checked the file type:

```bash
file data.txt
```

The output showed that it was a UTF-8 text file.

Since `data.txt` was a very large file, I did not read the entire file with `cat`. Instead, I used `strings` and `grep` together to search directly for the word `millionth`:

```bash
strings data.txt | grep 'millionth'
```

The command returned:

```text
millionth       VR**jMayciF********6QC9VKtub
```

The value next to `millionth` was the password for **Bandit Level 08**:


## 🧠 What I Learned

I learned how to search for specific text inside a large file without displaying the whole file.

The `grep` command searches for matching text, while `strings` extracts human-readable text from a file.

Useful command:

```bash
strings data.txt | grep 'millionth'
```

The `|` symbol (pipe) sends the output of the first command directly into the second command.
