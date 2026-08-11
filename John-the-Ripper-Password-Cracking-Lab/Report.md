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


**SHA-512crypt / yescrypt**
Perform password cracking
```bash
john --single --format=crypt singlecrack_test.txt
```
![Result](Screenshots/single_crypt.png)

**MD5**
Generated an MD5-crypt hash for each test user's known password using openssl, since Kali's passwd command only produces yescrypt hashes for real system accounts.

```bash
echo "user1:$(openssl passwd -1 -salt saltmd5 user1):1007:1008::/home/user1:/bin/sh" > hash-md5.txt
echo "user2:$(openssl passwd -1 -salt saltmd5 password):1008:1009::/home/user2:/bin/sh" >> hash-md5.txt
echo "user3:$(openssl passwd -1 -salt saltmd5 'Password1!'):1004:1005::/home/user3:/bin/sh" >> hash-md5.txt
echo "user4:$(openssl passwd -1 -salt saltmd5 xk4T9):1005:1006::/home/user4:/bin/sh" >> hash-md5.txt
echo "user5:$(openssl passwd -1 -salt saltmd5 Winter2025):1006:1007::/home/user5:/bin/sh" >> hash-md5.txt
```
Perform password cracking
```bash
john --single --format=md5crypt hash-md5.txt
```
![Result](Screenshots/single_md5.png)

**SHA-256**
```
echo "user1:$(openssl passwd -5 -salt saltsha256 user1):1007:1008::/home/user1:/bin/sh" > hash-sha256.txt
echo "user2:$(openssl passwd -5 -salt saltsha256 password):1008:1009::/home/user2:/bin/sh" >> hash-sha256.txt
echo "user3:$(openssl passwd -5 -salt saltsha256 'Password1!'):1004:1005::/home/user3:/bin/sh" >> hash-sha256.txt
echo "user4:$(openssl passwd -5 -salt saltsha256 xk4T9):1005:1006::/home/user4:/bin/sh" >> hash-sha256.txt
echo "user5:$(openssl passwd -5 -salt saltsha256 Winter2025):1006:1007::/home/user5:/bin/sh" >> hash-sha256.txt
```
Perform password cracking
```bash
john --single --format=sha256crypt hash-sha256.txt
```
![Result](Screenshots/single_256.png)

**Bcrypt**
Check if htpasswd is installed
```
which htpasswd
```
Generate bcrypt hashes for each password
```
echo "user1:$(htpasswd -nbB user1 user1 | cut -d: -f2):1007:1008::/home/user1:/bin/sh" > hash-bcrypt.txt
echo "user2:$(htpasswd -nbB user2 password | cut -d: -f2):1008:1009::/home/user2:/bin/sh" >> hash-bcrypt.txt
echo "user3:$(htpasswd -nbB user3 'Password1!' | cut -d: -f2):1004:1005::/home/user3:/bin/sh" >> hash-bcrypt.txt
echo "user4:$(htpasswd -nbB user4 xk4T9 | cut -d: -f2):1005:1006::/home/user4:/bin/sh" >> hash-bcrypt.txt
echo "user5:$(htpasswd -nbB user5 Winter2025 | cut -d: -f2):1006:1007::/home/user5:/bin/sh" >> hash-bcrypt.txt
```
Perform password cracking
```
john --single --format=bcrypt hash-bcrypt.txt
```
![Result](Screenshots/single_bcrypt.png)

## Wordlist Mode
Executed John the Ripper using Wordlist mode, which compares each hash against passwords from a precompiled wordlist file, making it effective against passwords that are common words or previously leaked credentials.

**SHA-512crypt / yescrypt**
```bash
john --wordlist=file.txt --format=crypt singlecrack_test.txt
```
![Result](Screenshots/wordlist_crypt.jpeg)

**MD5**
```bash
john --wordlist=file.txt --format=md5crypt hash-md5.txt
```
![Result](Screenshots/wordlist_md5.png)

**SHA-256**
```bash
john --wordlist=file.txt --format=sha256crypt hash-sha256.txt
```
![Result](Screenshots/wordlist_256.png)

**Bcrypt**
```bash
john --wordlist=file.txt --format=bcrypt hash-bcrypt.txt
```
![Result](Screenshots/wordlist_bcrypt.png)






