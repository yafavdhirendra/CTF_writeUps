# Bandit Level 29 → Level 30

## Goal

There is another Git repository:

```text
ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

The goal is to find the password for `bandit30`.

## What I Did

I cloned the repository:

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

I entered the password obtained from Level 29.

Then I entered the repository:

```bash
cd repo
```

I checked the files:

```bash
ls
```

Output:

```text
README.md
```

I read the README:

```bash
cat README.md
```

Output:

```text
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

The current `master` branch did not contain the password.

## Check Available Branches

I checked all branches:

```bash
git branch -a
```

Output included:

```text
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

There was an interesting branch called:

```text
origin/dev
```

## Switch to the Dev Branch

I switched to the `dev` branch:

```bash
git checkout dev
```

Output:

```text
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
```

I checked the files:

```bash
ls -al
```

The branch contained:

```text
code
README.md
.git
```

Then I read the README:

```bash
cat README.md
```

The password was revealed:

```text
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: jq9Df_bandit_lvl_30_pass_gX
```

Therefore, the password for **Bandit Level 30** was:

```text
jq9Dfg__bandit_lvl_30_pass_USgX
```

## What I Learned

This level taught me about Git branches.

A Git repository can have multiple branches containing different versions of files.

Useful commands:

```bash
git branch
```

Shows local branches.

```bash
git branch -a
```

Shows local and remote branches.

```bash
git checkout dev
```

Switches to the `dev` branch.

The important idea was:

```text
master
   │
   └── README → password hidden

dev
   │
   └── README → password revealed
```

---



