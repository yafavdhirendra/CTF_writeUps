# Bandit Level 12 → Level 13

## 🎯 Goal

The password for the next level is stored in `data.txt`, which is a hexdump of a file that has been compressed multiple times.

The main task was to convert the hexdump back into a binary file and then repeatedly identify and decompress each layer.

## 🔎 Finding the Password

First, I created a temporary working directory:

```bash
mktemp -d
```

This created:

```text
/tmp/tmp.NtmoEIjqGq
```

I copied the original `data.txt` into this directory:

```bash
cp data.txt /tmp/tmp.NtmoEIjqGq
```

Then I entered the directory:

```bash
cd /tmp/tmp.NtmoEIjqGq
```

### 1. Convert the hexdump back to binary

The `data.txt` file was a hexadecimal representation of the original compressed file. I converted it back to binary using:

```bash
xxd -r data.txt dhire
```

Then I checked the file type:

```bash
file dhire
```

It was identified as a **gzip compressed file**.

I renamed it and decompressed it:

```bash
mv dhire data.gz
gunzip data.gz
```

### 2. Identify the next compression layer

I checked the resulting file:

```bash
file data
```

It was **bzip2 compressed data**.

I renamed and decompressed it:

```bash
mv data data.bz2
bunzip2 data.bz2
```

The resulting file was another gzip-compressed file, so I checked it with `file`, renamed it to `.gz`, and decompressed it.

After decompression, the next file was identified as a **POSIX tar archive**.

### 3. Extract the tar archive

I extracted the archive:

```bash
tar -xf data
```

This produced:

```text
data5.bin
```

I checked it:

```bash
file data5.bin
```

It was another **POSIX tar archive**, so I extracted it:

```bash
tar -xf data5.bin
```

This produced:

```text
data6.bin
```

### 4. Continue with the next layers

I checked the file:

```bash
file data6.bin
```

It was **bzip2 compressed data**.

I renamed and decompressed it:

```bash
mv data6.bin data6.bz2
bunzip2 data6.bz2
```

The resulting `data6` file was a **POSIX tar archive**, so I extracted it:

```bash
tar -xf data6
```

This produced:

```text
data8.bin
```

I checked it:

```bash
file data8.bin
```

It was another **gzip compressed file**.

I renamed and decompressed it:

```bash
mv data8.bin data8.gz
gunzip data8.gz
```

Finally, I checked the resulting file:

```bash
file data8
```

It was identified as **ASCII text**.

I displayed the contents:

```bash
cat data8
```

The output was:

```text
The password is qQYQiHOB***********F2uzk
```

Therefore, the password for **Bandit Level 13** was:

```text
qQYQiHO************2uzk
```

## 🧠 What I Learned

This level taught me how to work with a file that has been compressed through multiple layers.

I learned to use:

```bash
xxd -r
```

to convert a hexdump back into binary data.

I also learned to use:

```bash
file
```

to identify the actual type of a file before deciding which decompression command to use.

The main commands I used were:

```bash
gunzip
bunzip2
tar -xf
file
```

The important lesson was to **check the file type after every decompression step** instead of guessing the next format.

##  Compression Chain

The file went through several different formats:

```text
Hexdump
   ↓
GZIP
   ↓
BZIP2
   ↓
GZIP
   ↓
TAR
   ↓
TAR
   ↓
BZIP2
   ↓
TAR
   ↓
GZIP
   ↓
ASCII Text
   ↓
Password
```
