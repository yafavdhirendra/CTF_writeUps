# Bandit Level 16 → Level 17

## 🎯 Goal

The password for the next level is available from one of several services running on localhost ports between `31000` and `32000`.

The correct service requires an **SSL/TLS connection** and, after receiving the current password, returns an **SSH private key**.

## Recon the Port in Target
```bash
nmap -p 31000-32000 localhost
```
That was giving the many port number which all shows that SSL/TLS connection. 
##  Finding the Correct Port

First, I tested the candidate ports that were identified for the challenge:

```bash
for port in 31**6 31**8 31**1 31**0 31**0; do
    echo "===== PORT $port ====="
    timeout 3 openssl s_client -connect localhost:$port </dev/null 2>&1 |
    grep -E "CONNECTED|Protocol|Cipher"
done
```

The results showed that ports `31**8` and `31**0` successfully established TLS connections.

I then tested the current password against the SSL services.

First, I tried port `31**8`:

```bash
echo 'kS0Hf0_Lvl_16_pass_Ga0X8V' | openssl s_client -connect localhost:31518 -quiet
```

The service simply returned the password, so this was not the correct service.

I then tested port `31**0`:

```bash
echo 'kS0Hf0_Lvl_16_pass_a0X8V' | openssl s_client -connect localhost:31790 -quiet
```

This time, the service responded with:

```text
Correct!
-----BEGIN OPENSSH PRIVATE KEY-----
...
-----END OPENSSH PRIVATE KEY-----
```

Therefore, **port 31 *** 0** was the correct port.

##  Obtaining the SSH Private Key

The service returned an OpenSSH private key after I submitted the current password.

I saved this private key to a file on my Kali machine, for example:

```bash
nano sshkey.private
```

I pasted the complete key, including:

```text
-----BEGIN OPENSSH PRIVATE KEY-----
```

and:

```text
-----END OPENSSH PRIVATE KEY-----
```

Then I saved the file.

I changed its permissions so that only my user could read it:

```bash
chmod 600 sshkey.private
```



This allows me to move from **Bandit Level 16 to Level 17** without using a password.

## What I Learned

This level taught me how to:

- Scan multiple TCP ports in given range for SSL/TLS services.
- Use `openssl s_client` to communicate with SSL/TLS services.
- Identify the correct service by submitting the current password.
- Work with an OpenSSH private key.
- Use a private key for SSH authentication.


## Attack Flow

```text
Current password
       ↓
Find SSL/TLS service
       ↓
Test candidate ports
       ↓
Port 31790
       ↓
Submit password
       ↓
Receive SSH private key
       ↓
Save key to Kali
       ↓
chmod 600
       ↓
SSH as bandit17
```
