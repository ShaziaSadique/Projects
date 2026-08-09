## LAB REPORT
# Project
John The Ripper Password Cracking Lab

# Author
Shazia Sadique

# Date
09-08-2026

# Subject
5 Attack Modes across 5 Hash Types

# Overview
This report documents hands-on password cracking lab using John the Ripper on Kali linux. 
Five different attack modes were tested: 
a) Single crack mode
b) Wordlist mode
c) Rules based mode
d) Incremental mode
e) Hybrid/Mask mode 
against five different target hash types 
a) MD5
b) SHA-256
c) SHA-512crypt/yescrypt
d) bcrypt
e) Salted SHA-512

# Tools and Equipments
- Kali Linux
- John the Ripper
- unshadow (jtr utility)
- wordlist file (downloaded)

# Setup
Created test users and generated password hashes for each of the hashes above. Each attack mode was tested against all hash types.

## Single Crack Mode
Executed John the Ripper using this mode, which guesses password based on the username and GECOS field data.

### Step 1: 
Combine `/etc/passwd` and `/etc/shadow` into a single file using `unshadow`.

```bash
sudo unshadow /etc/passwd /etc/shadow > all_users.txt
grep -E '^user[1-5]:' all_users.txt > singlefile.txt
```
### Step 2:
Run John the Ripper against all hash types

**MD5**
```bash
john --single singlefile.txt
```
**SHA-256**

```bash
john --single --format=sha256crypt singlecrack_test.txt
```

**SHA-512crypt / yescrypt**

```bash
john --single --format=crypt singlecrack_test.txt
```

**bcrypt**

```bash
john --single --format=bcrypt singlecrack_test.txt
```
















