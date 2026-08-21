# Bandit Level 22 → Level 23

## 🎯 Objective

Find the password for the next level. A cron job runs a script as the `bandit23` user, and the script creates a file in `/tmp` containing the password.

##  Find the Cron Job

First, I checked the cron directory:

```bash
cd /etc/cron.d
ls
```

I found:

```text id="m4xj5q"
cronjob_bandit23
```

I checked the cron job:

```bash
cat cronjob_bandit23
```

It runs the following script every minute as `bandit23`:

```text id="b2yx4v"
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null
```

##  Analyze the Script

I checked the script:

```bash
cat /usr/bin/cronjob_bandit23.sh
```

The important part is:

```bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

Since the cron job runs as `bandit23`, the value of:

```bash
whoami
```

is:

```text
bandit23
```

Therefore, the script calculates the MD5 hash of:

```text
I am user bandit23
```

I calculated it with:

```bash
echo "I am user bandit23" | md5sum
```

This gave:

```text
8ca319486_md5_hash_326349
```

So the password should be stored in:

```text
/tmp/8ca3194_pass_contain_hash_26349
```

##  Read the Password

After the cron job ran, I read the file:

```bash
cat /tmp/8ca3194_pass_contain_hash_26349
```

This returned the password for **Bandit Level 23**.

## 🧠 What I Learned

* How cron jobs execute scripts automatically.
* How `whoami` identifies the current user.
* How `md5sum` can be used to generate a filename.
* How command substitution works with `$()`.
* How a script can construct a file path dynamically.


