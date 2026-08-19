# Bandit Level 11 → Level 12

## 🎯 Goal

The password for the next level is stored in `data.txt`. All lowercase and uppercase letters have been rotated by **13 positions**, which means the text is encoded using **ROT13**.

## 🔎 Finding the Password

First, I checked the files in the current directory:

```bash
ls
```

I found:

```text
data.txt
```

I used `strings` to extract the readable text from the file. Then I used `tr` to rotate the alphabet by 13 positions and decode the ROT13 text:

```bash
strings data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

The command returned:

```text
The password is GROozWPO8********xrN
```

Therefore, the password for **Bandit Level 12** was:

```text
GROozW****************xrN
```

## 🧠 What I Learned

I learned about **ROT13**, a simple substitution cipher where each letter is replaced by the letter 13 positions away in the alphabet.

The command I used was:

```bash
strings data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Here:

* `strings` extracts readable text.
* `tr` translates characters from one set to another.
* `A-Z` and `a-z` represent uppercase and lowercase letters.
* `N-ZA-M` and `n-za-m` perform the ROT13 rotation.

ROT13 is not encryption because it can easily be reversed using the same transformation.
