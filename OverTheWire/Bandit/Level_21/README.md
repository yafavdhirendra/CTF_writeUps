# Bandit Level 21 → Level 22

## 🎯 Objective

Find the password for the next level. The password is obtained from a script that is executed automatically by a **cron job**.

##  Find the Cron Job

First, I checked the cron jobs:

```bash
crontab -l
```

This returned a permission error:

```text
crontabs/bandit21/: fopen: Permission denied
```

Instead, I checked the system-wide cron directory:

```bash
cd /etc/cron.d
ls
```

I found:

```text
cronjob_bandit22
```

I checked its contents:

```bash
cat cronjob_bandit22
```

The cron job contains:

```text
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

This shows that `cronjob_bandit22.sh` runs every minute as the **bandit22** user.

##  Analyze the Script

I checked the script:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

It contains:

```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9_hash_of_file_name_KF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds_hash_of_file_name_F7fgv
```

The script copies the password for `bandit22` into a temporary file:

```text
/tmp/t7O6lds_hash_file_F7fgv
```

It also changes the file permissions to `644`, which allows me to read the file.

## Read the Password

I read the temporary file:

```bash
cat /tmp/t7O6lds9_file_name_F7fgv
```

The output contains the password for **Bandit Level 22**.

##  What I Learned

* What cron jobs are.
* How to inspect system-wide cron jobs in `/etc/cron.d`.
* How cron can execute scripts automatically.
* How to read and understand a shell script.
* How file permissions such as `644` affect access to files.
