# Bandit Level 31 → Level 32

## Goal

The goal of this level is to **push a specific file to the remote Git repository**.



---

## Step 1: Clone the Repository

I cloned the repository from my local Kali machine:

```bash
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
```

After entering the `bandit31` password, the repository was successfully cloned.

I entered the repository:

```bash
cd repo
```

---

## Step 2: Check the Remote Repository

I checked the remote URL:

```bash
git remote -v
```

Output:

```text
origin  ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo (fetch)
origin  ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo (push)
```

This confirmed that my local repository was connected to the correct remote repository.

---

## Step 3: Read the README

I checked the files:

```bash
ls
```

There was a:

```text
README.md
```

I read it:

```bash
cat README.md
```

It said:

```text
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

This told me exactly what file I needed to create and push.

---

## Step 4: Check `.gitignore`

I checked the hidden files:

```bash
ls -la
```

There was a file called:

```text
.gitignore
```

I checked its contents:

```bash
cat ./.gitignore
```

Output:

```text
*.txt
```

This means Git was configured to **ignore all `.txt` files**.

Since the required file was:

```text
key.txt
```

Git would normally ignore it.

I therefore modified `.gitignore` so that `key.txt` could be added to Git.

---

## Step 5: Create `key.txt`

I created the required file:

```bash
nano key.txt
```

Inside the file, I entered:

```text
May I come in?
```

Then I checked the files:

```bash
ls
```

Output included:

```text
key.txt
README.md
```

---

## Step 6: Add the File to Git

I added `key.txt`:

```bash
git add key.txt
```

Then I checked the Git status:

```bash
git status
```

Git showed:

```text
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
        new file:   key.txt

Changes not staged for commit:
        modified:   .gitignore
```

The important part is:

```text
new file: key.txt
```

This means `key.txt` was successfully staged for the next commit.

---

## Step 7: Commit the File

I created a commit:

```bash
git commit -m 'Added key.txt'
```

Git responded:

```text
[master 4670875] Added key.txt
1 file changed, 1 insertion(+)
create mode 100644 key.txt
```

The file was now committed on the `master` branch.

---

## Step 8: Push the Commit

I pushed the changes:

```bash
git push
```

After entering the `bandit31-git` password, the remote server processed my push.

The server returned:

```text
remote: ### Attempting to validate files... ####
```

Then it gave me:

```text
remote: Well done! Here is the password for the next level:
remote: pWuj_bandit_lvl_32_pass_vbT
```

Therefore, the password for **Bandit Level 32** is:

```text
pWuj5jB_bandit_lvl_32_pass_vbT
```

---

# What I Learned

In this level I learned:

1. How to read instructions from a Git repository.
2. How `.gitignore` can prevent files from being tracked.
3. How to add a file to Git.
4. How to commit a file.
5. How to push a commit to a remote repository.


