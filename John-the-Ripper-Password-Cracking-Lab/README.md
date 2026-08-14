# John the Ripper — Password Cracking Lab

## Overview
Hands-on lab testing 5 John the Ripper attack modes against 5 password hash types on Kali Linux, comparing cracking speed and success rate across each combination.

## Objective
To demonstrate how password hashing algorithm choice affects real-world crackability, independent of the attack mode used.

## Tools Used
- Kali Linux
- John the Ripper
- openssl / htpasswd (hash generation)
- Downloaded wordlist

## Hash Types Covered
| Hash Type | Description |
|---|---|
| MD5 | Legacy, fast, weak |
| SHA-256 | Faster hashing, still crackable at scale |
| SHA-512crypt/yescrypt | Modern Unix default, memory-hard |
| bcrypt | Adaptive cost factor, slow by design |

## Attack Modes Covered
1. Single Crack
2. Wordlist
3. Rules-Based
4. Incremental
5. Hybrid/Mask
