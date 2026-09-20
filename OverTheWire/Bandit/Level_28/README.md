
# Bandit Level 28 → Level 29

## Goal

There is another Git repository:

```text
ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```

The goal is to find the password for `bandit29`.

## What I Did

I cloned the repository:

```bash
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```

After entering the correct password, the repository was cloned successfully.

I entered the repository:

```bash
cd repo
```

Then I checked the files:

```bash
ls
```

Output:

```text
README.md
```

I read the file:

```bash
cat README.md
```

The current README contained:

```text
Some notes for level29 of bandit.

username: bandit29
password: xxxxxxxxxx
```

The password was delete so i checked git history.

## Checking Git History

Because this is a Git repository, previous versions of the file may still exist in Git history.

I checked the commit history:

```bash
git log
```

There were three commits:

```text
fix info leak
add missing data
initial commit of README.md
```

I inspected the older commit:

```bash
git show 13bbc4d2414ffe0439b8ee4f5e5c2949780cf4b3
```

The important change was:

```diff
- password: <TBD>
+ password: Em7eGt_Lvl_29_pass_Ocdt0
```

Therefore, the password for **Bandit Level 29** was:

```text
Em7eGt_bandit_lvl_29_pass_Ocdt0
```

## What I Learned

Git stores previous versions of files in its history.

Even if information is removed from the current file, an older commit may still contain it.

Useful commands:

```bash
git log
```

Shows commit history.

```bash
git show <commit>
```

Shows the changes made by a particular commit.

---

