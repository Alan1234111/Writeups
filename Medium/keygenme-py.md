# keygenme-py - Category: Reverse Engineering
- Platform: PicoCTF
- Level: Medium

## Description

In this CTF i needed to get license from source code

## Tools

- Python
- Visual Studio Code

## Solution

First i checked file keygenme-trial.py and found out that there is a function *check_key(key, username_trial)* that test the key

<img width="663" height="877" alt="image" src="https://github.com/user-attachments/assets/a421ba44-0e9c-48a6-b355-f1d1f94baca1" />

Upon analyzing the validation logic, I discovered that the program computes a SHA-256 hash of the *username_trial* string. It then converts this hash into a hexadecimal string and performs a position-based check. Specifically, it extracts a character at a specific index from the resulting hash and compares it against the character provided in the user's key to determine if it is valid.

Next I wrote my own python program to decrypt this hash

```python
import hashlib

username = b"BENNETT"
expected_key = hashlib.sha256(username).hexdigest()[4] + hashlib.sha256(username).hexdigest()[5] + hashlib.sha256(username).hexdigest()[3] + hashlib.sha256(username).hexdigest()[6] + hashlib.sha256(username).hexdigest()[2] + hashlib.sha256(username).hexdigest()[7] + hashlib.sha256(username).hexdigest()[1] + hashlib.sha256(username).hexdigest()[8]

print("picoCTF{1n_7h3_kk3y_of_" + expected_key + "}") 
```

Then i ran a program and get the full version of the program with the flag

## Flag
*picoCTF{1n_7h3_kk3y_of_08c46aa4}*

## Key Takeaways

- Hashing (SHA-256): This challenge demonstrates that SHA-256 is deterministic. Because the same input always produces the exact same output, we can predict the required key if we know the hashing algorithm and the input string.

- Static Analysis: By carefully reading the source code, I was able to perform a "white-box" analysis. This allowed me to reconstruct the key generation logic and avoid an impossible brute-force attack
