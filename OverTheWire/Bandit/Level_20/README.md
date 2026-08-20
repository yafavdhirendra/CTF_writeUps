# Bandit Level 20 → Level 21

## 🎯 Objective

Find the password for the next level. A Set-UID program called `suconnect` is available. It connects to a port on localhost and expects the current password. If the password is correct, it sends back the password for the next level.

##  Find the Password

First, check the available files:

```bash
ls -al
```

I found the `suconnect` program:

```
-rwsr-x--- 1 bandit21 bandit20 15604 suconnect
```

The `s` in the permissions indicates that `suconnect` is a **Set-UID executable**.

Running it without a port shows how it works:

```bash id="5q2qj4"
./suconnect
```

It shows:

```
Usage: ./suconnect <portnumber>
```

The program connects to the specified localhost TCP port and checks whether the received password is correct.

##  Start a Listener

I opened a second SSH session and started a Netcat listener on port `1234`:

```bash
nc -lnvp 1234
```

The listener waits for a connection from `suconnect`.

In the first terminal, I ran:

```bash
./suconnect 1234
```

The listener received the current Level 20 password:

```
4pIjc_Lvl_20_pass_6pOA
```

I sent that password through the Netcat connection.

`suconnect` verified it:

```text id="v2x4c9"
Read: 4pIjcun_Lvl_20_pass_OA
Password matches, sending next password
```

The listener then received the password for **Bandit Level 21**:

```text
bW9kBv_Lvl_21_pass_ka6hY
```

## 🧠 What I Learned

* How a Set-UID program can run with another user's privileges.
* How to create a TCP listener using `nc`.
* How two terminals can communicate through a localhost TCP connection.
* How `suconnect` verifies a password and returns the next password.


