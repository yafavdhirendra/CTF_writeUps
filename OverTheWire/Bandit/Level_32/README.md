# Bandit Level 32 → Level 33

## Goal

The goal of this level is to escape from the **UPPERCASE SHELL** and obtain the password for the next level.

---

## Step 1: Log in as `bandit32`

I connected to the Bandit server using SSH:

```bash
ssh -p 2220 bandit32@bandit.labs.overthewire.org
```

After entering the password from Level 31, I successfully logged in.

The server displayed:

```text
WELCOME TO THE UPPERCASE SHELL
>>
```

This tells us that we are placed inside a restricted shell that changes our commands to uppercase.

---

## Step 2: Test Normal Commands

I tried:

```bash
ls
```

But the shell changed it to:

```text
LS
```

and returned:

```text
sh: 1: LS: Permission denied
```

I also tried:

```bash
man
```

which became:

```text
MAN
```

and failed.

I tried:

```bash
sh
```

which became:

```text
SH
```

and also failed.



## Step 3: Use `$0`

Instead of entering a normal command, I entered:

```bash
$0
```

The restricted shell executed it and gave me another shell:

```text
$ sh
```

Now I was no longer inside the uppercase command restriction.

---

## Step 4: Check the Current User

I ran:

```bash
whoami
```

The output was:

```text
bandit33
```

This was the important result.

I had escaped the uppercase shell and was now operating as the `bandit33` user.

---

## Step 5: Read the Password

I read the password file:

```bash
cat /etc/bandit_pass/bandit33
```

The server returned:

```text
u4P2_bandit_lvl_pass_33_FswM
```

---


# What I Learned

This level taught me:

1. Shell commands are **case-sensitive**.
2. A restricted shell can modify or restrict commands.
3. `$0` has a special meaning in a shell.
4. Understanding shell behavior can help identify weaknesses in a restricted environment.
5. After escaping the restricted shell, I could use normal commands again.

