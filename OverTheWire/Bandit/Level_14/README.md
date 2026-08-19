# Bandit Level 14 → Level 15

## 🎯 Goal

The password for the next level can be obtained by submitting the current Bandit password to a service running on **localhost port 30000**.

##  Logging in with the SSH Private Key

First, I changed the permissions of the private key:

```bash
chmod 600 sshkey.private
```

Then I used the private key to log in as `bandit14`:

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

After successfully logging in, I accessed the directory containing the Bandit passwords:

```bash
cd /etc/bandit_pass
```

I listed the available password files:

```bash
ls
```

Then I read the current `bandit14` password:

```bash
cat bandit14
```

The password was:

```text
aaWecNk**************YS65
```

##  Connecting to the Local Service

The level required me to send the current password to a service running on localhost port `30000`.

I first connected using `telnet`:

```bash
telnet localhost 30000
```

I entered the current password:

```text
aaWecN***Lvl_14_pass***iYS65
```

The service responded:

```text
Correct!
pbLYuZ*************GqM68A7
```

The returned value was the password for **Bandit Level 15**.

##  Using Netcat

I also used `nc` to send the password directly to the service:

```bash
echo 'aaWec***-Lvl_14_pass_bJiYS65' | nc localhost 30000
```

The output was:

```text
Correct!
pbLYu*************GqM68A7
```

This was a faster way to complete the level because `echo` sends the password directly to `nc`.

## 🧠 What I Learned

I learned how to interact with a service running on a specific localhost port.

I also learned:

* `telnet` can establish a connection to a TCP service.
* `nc` (Netcat) can send data directly to a network service.
* `localhost` refers to the same machine.
* Port `30000` was the service port used by this challenge.

The most convenient command was:

```bash
echo 'PASSWORD' | nc localhost 30000
```


