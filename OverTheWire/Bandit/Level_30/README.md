# Bandit Level 30 → Level 31

## Goal

The goal of this level is to find the password for the next level using the Git repository.

The repository is accessed through:

```text
ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
```

The password for `bandit30-git` is the same as the password for `bandit30`.

---

## Step 1: Clone the Repository

From my local Kali machine, I cloned the repository:

```bash
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
```

After entering the `bandit30` password, the repository was cloned successfully.

I entered the repository:

```bash
cd repo
```

---

## Step 2: Check the README

I listed the files:

```bash
ls
```

Output:

```text
README.md
```

Then I read the file:

```bash
cat README.md
```

Output:

```text
just an epmty file... muahaha
```

The README did not contain the password.

---

## Step 3: Check Git History

I first tried:


```bash
git log
```

There was only one commit:

```text
initial commit of README.md
```

So the password was not available through the normal commit history.

---

## Step 4: Check Git Branches

I checked all branches:

```bash
git branch -a
```

Output:

```text
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

There were no additional interesting branches.

---

## Step 5: Check Git Tags

Git also has another feature called **tags**.

I checked the tags with:

```bash
git tag
```

Output:

```text
secret
```

This was interesting because there was a tag called:

```text
secret
```

---

## Step 6: Read the Secret Tag

I used:

```bash
git show secret
```

The output was:

```text
82Nkymb_bandit_lvl_31_pass_pfUf
```



---



# What I Learned

The important lesson is that information in a Git repository may be stored in places other than the current files.

