# Bandit Level 15 → Level 16

## 🎯 Goal

The password for the next level must be obtained by submitting the current password to a service running on **localhost port 30001** using an **SSL/TLS connection**.

##  Connecting to the SSL Service

First, I used the password obtained from the previous level:

```text
pbLYuZt_lvl_15_pass_qM68A7
```

Because the service requires an encrypted SSL/TLS connection, I used `openssl s_client` instead of normal `nc`:

```bash
echo 'pbLYuZ_Lvl_15_pass_GqM68A7' | openssl s_client -connect localhost:30001 -quiet
```

The connection produced some certificate information, including:

```text
depth=0 CN=SnakeOil
verify error:num=18:self-signed certificate
```

The certificate is self-signed, but the connection still continued successfully.

The important part of the output was:

```text
Correct!
kS0H******************GGa0X8V
```

This is the password for next **Bandit Level 16**.



## 🧠 What I Learned

I learned how to connect to a service using **SSL/TLS** with OpenSSL.

The important command was:

```bash
openssl s_client -connect localhost:30001 -quiet
```

I also learned that `nc` is not suitable for this level because the service expects an SSL/TLS connection.

The `echo` command sends the password to the SSL service through the pipe (`|`).

`quiet` use for only see server response data
