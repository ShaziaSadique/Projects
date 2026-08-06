# John the Ripper — Password Cracking Lab

## Overview
Hands-on lab exploring password hash cracking using John the Ripper across 
5 attack modes and 5 hash types, run in a Kali Linux environment.

## Objective
To understand how different password hashing algorithms resist cracking, 
and how different JtR attack modes perform against them in terms of speed 
and success rate.

## Tools Used
- Kali Linux
- John the Ripper
- openssl (hash generation)
- rockyou.txt wordlist

## Hash Types Covered
| Hash Type          | Description                          |
|---------------------|---------------------------------------|
| MD5                 | Legacy, fast, weak                   |
| SHA-256             | Faster hashing, still crackable at scale |
| SHA-512crypt/yescrypt | Modern Unix shadow hashing        |
| bcrypt              | Adaptive, slow by design             |
| Salted SHA-512      | Salted variant, resists rainbow tables |

## Attack Modes Covered
1. Single Crack Mode
2. Wordlist Mode
3. Rules-Based Mode
4. Incremental Mode
5. Hybrid/Mask Mode

## Methodology & Results
