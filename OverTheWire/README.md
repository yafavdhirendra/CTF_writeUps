# OverTheWire CTF Writeups

A collection of my **OverTheWire CTF write-ups, notes, commands, techniques, and solutions**.

The purpose of this repository is to document my learning while solving OverTheWire wargames and to keep useful Linux, networking, web, cryptography, and security techniques in one place.

> ⚠️ **Spoiler Warning:**
> This repository contains solutions and walkthroughs for OverTheWire challenges. If you are currently solving a challenge yourself, try solving it before reading the write-up.

---

## 🎯 About OverTheWire

[OverTheWire](https://overthewire.org/) provides several wargames designed to help people learn and practice cybersecurity concepts.

The wargames cover topics such as:

* Linux command line
* File permissions
* SSH
* Networking
* Cryptography
* Web security
* Privilege escalation
* Binary exploitation
* Reverse engineering
* Programming and scripting

---

## 🏴 Wargames

### Bandit

**Bandit** is focused mainly on learning the Linux command line and basic security concepts.

| Level   | Topic                | Write-up                       |
| ------- | -------------------- | ------------------------------ |
| 00 → 01 | SSH / Basic commands                 | [Write-up](./Bandit/Level_00/README.md) |
| 01 → 02 | File handling                        | [Write-up](./Bandit/Level_01/README.md) |
| 02 → 03 | Special characters                   | [Write-up](./Bandit/Level_02/README.md) |
| 03 → 04 | Hidden File                          | [Write-up](./Bandit/Level_03/README.md) |
| 04 → 05 | Human_Readable File Discovery        | [Write-up](./Bandit/Level_04/README.md) |
| 05 → 06 | Finding Files by size and permission | [Write-up](./Bandit/Level_05/README.md) |
| 06 → 07 | Finding Files by Owner, Group        | [Write-up](./Bandit/Level_06/README.md) |
| 07 → 08 | Keyword Search with Grep             | [Write-up](./Bandit/Level_07/README.md) |
| 08 → 09 | Unique Line Detection                | [Write-up](./Bandit/Level_08/README.md) |
| 09 → 10 | Pattern Matching in Binary Data      | [Write-up](./Bandit/Level_09/README.md) |
| 10 → 11 | Base64 Decoding                      | [Write-up](./Bandit/Level_10/README.md) |
| 11 → 12 | ROT13 Ciper Decoding                 | [Write-up](./Bandit/Level_11/README.md) |
| 12 → 13 | Compression & Hexdump                | [Write-up](./Bandit/Level_12/README.md) |
| 13 → 14 | SSH Private Key auth                 | [Write-up](./Bandit/Level_13/README.md) |
| 14 → 15 | TCP service with Netcat              | [Write-up](./Bandit/Level_14/README.md) |
| 15 → 16 | SSL/TLS connection with Openssl      | [Write-up](./Bandit/Level_15/README.md) |
| 10 → 11 | Base64 Decoding                      | [Write-up](./Bandit/Level_10/README.md) |
| 02 → 03 | Special characters                   | [Write-up](./Bandit/Level_02/README.md) |
| 03 → 04 | Hidden File                          | [Write-up](./Bandit/Level_03/README.md) |
| ...     | ...                    | ...                            |




---

### Natas

**Natas** focuses on web security and web application vulnerabilities.

| Level   | Topic                    | Write-up                      |
| ------- | ------------------------ | ----------------------------- |
| 00 → 01 | Web basics               | [Write-up](./Natas/Level-00/) |
| 01 → 02 | Client-side restrictions | [Write-up](./Natas/Level-01/) |
| ...     | ...                      | ...                           |

---

### Leviathan

**Leviathan** focuses on Linux binaries, permissions, and basic exploitation techniques.

| Level   | Topic           | Write-up                          |
| ------- | --------------- | --------------------------------- |
| 00 → 01 | Binary analysis | [Write-up](./Leviathan/Level-00/) |
| ...     | ...             | ...                               |

---

## 🧠 Topics Covered

Throughout these wargames, I am documenting techniques related to:

* 🐧 Linux
* 🔐 SSH
* 📁 File permissions
* 🔎 Enumeration
* 🌐 Networking
* 🕸️ Web security
* 🔑 Authentication
* 🔢 Encoding & decoding
* 🔐 Cryptography
* 🐚 Shell scripting
* ⚙️ Privilege escalation
* 💻 Binary exploitation
* 🧩 Reverse engineering
* 🐍 Python scripting

---

## 🛠️ Tools & Commands

Some commonly used tools and commands include:

```bash
ssh
ls
cat
find
grep
file
strings
chmod
scp
nc
curl
wget
python
openssl
base64
xxd
```

> The exact tools used depend on the challenge.

---

## 📚 Write-up Format

Each challenge write-up generally contains:

1. **Challenge / Level**
2. **Objective**
3. **Initial Enumeration**
4. **Commands Used**
5. **What Happened**
6. **Vulnerability / Concept**
7. **Solution**
8. **Important Takeaways**

Example:

```text
Level-XX/
├── README.md
├── commands.txt
└── files/
```

---

## 📈 Progress

| Wargame   |       Progress |
| --------- | -------------: |
| Bandit    | 🚧 In Progress |
| Natas     |  ⏳ Not Started |
| Leviathan |  ⏳ Not Started |
| Krypton   |  ⏳ Not Started |
| Narnia    |  ⏳ Not Started |
| Behemoth  |  ⏳ Not Started |
| Utumno    |  ⏳ Not Started |
| Maze      |  ⏳ Not Started |

I will update this table as I progress.

---

## ⚠️ Disclaimer

These write-ups are created for **educational purposes** and to document my own learning.

If you are working through OverTheWire yourself, I recommend attempting each level independently before checking the solution.

---

## 🔗 Resources

* [OverTheWire](https://overthewire.org/)
* [OverTheWire Wargames](https://overthewire.org/wargames/)
* [Bandit](https://overthewire.org/wargames/bandit/)
* [Natas](https://overthewire.org/wargames/natas/)

---

## 👨‍💻 Goal

> The goal of this repository is not simply to collect flags.

It is to understand **why the solution works**, learn the underlying security concepts, and build practical cybersecurity skills through hands-on challenges.
 