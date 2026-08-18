# Bandit Level 10 → Level 11

## 🎯 Goal

The password for the next level is stored in the file **data.txt**, which contains **base64** encoded data



## 🔎 Finding the Encoded Password

First, I checked the files in the current directory:

```bash
ls
```

I found:

```text
data.txt
```

I used `strings` to extract the readable content from the file and then searched for a Base64-looking string:

```bash
strings data.txt | grep -E '^[A-Za-z0-9+/=]{20,}'
```

The command returned:

```text
VGhlIHBh****IGlzIHBZZ*************TdNQ212OHZONVJvCg==
```

This looked like Base64-encoded data because it contained characters commonly used in Base64 encoding.

I then decoded it using `base64 -d`:

```bash
strings data.txt | grep -E '^[A-Za-z0-9+/=]{20,}' | base64 -d
```

The decoded output was:

```text
The password is pYfO**HwU********8vN5Ro
```
This was the password needed to log in to **Bandit Level 11**.
 

## 🧠 What I Learned

I learned how to recognize and decode Base64-encoded data.

The main command was:

```bash
strings data.txt | grep -E '^[A-Za-z0-9+/=]{20,}' | base64 -d
```

The `|` pipe allows the output of one command to be passed directly to the next command.

I also learned that Base64 is an **encoding**, not encryption, so it can be decoded when the encoded data is available.
