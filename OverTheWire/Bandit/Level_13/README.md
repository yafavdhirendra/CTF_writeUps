# Bandit Level 13 → Level 14

## 🎯 Goal

The password for the next level is not directly given. Instead, the `sshkey.private` file in the home directory can be used to log in to **Bandit Level 14**.

## 🔎 Finding the SSH Private Key

First, I checked the files in the current directory:

```bash
ls
```

I found:

```text
HINT
sshkey.private
```

The `sshkey.private` file contains an **OpenSSH private key**.

I also checked the `HINT` file:

```bash
cat HINT
```

The hint explained that logging directly from one Bandit level to another through localhost is blocked. Therefore, I needed to log out and use the private key from my own Kali machine.

##  Copying the Private Key to Kali

I first exited the Bandit server:

```bash
exit
```

After returning to my Kali terminal, I copied the private key from the Bandit server using `scp`:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```



The private key was successfully copied to my current Kali directory`(.)`.

##  Using the Private Key

I can now use the private key to authenticate as `bandit14`:

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

The `-i` option specifies the private SSH key, while `-p 2220` specifies the OverTheWire SSH port.

After successfully logging in as `bandit14`, I reached the next level.

## 🧠 What I Learned

This level taught me how SSH public/private key authentication works and how to use `scp` to copy files between a remote server and my local Kali machine.

Important commands:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```
`.` was used for saved current directory. This process doing outside from the bandit lvl. 
```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

I also learned that the OverTheWire server blocks attempts to connect from one level to another through localhost, so the private key needs to be copied to my local machine and then used from there.
