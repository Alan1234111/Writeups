# PW Crack 5 - Category: Python
- Platform: PicoCTF
- Level: Easy

## Description

Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too. Here's a dictionary with all possible passwords based on the password conventions we've seen so far.


## Tools

- Python
- Visual Studio Code

## Solution

First I check file level5.py and found out that i can write new function that uses dictonary to crack the hash

<img width="967" height="850" alt="image" src="https://github.com/user-attachments/assets/aa72e53e-63ba-4c8f-821c-b2ceca48111f" />

---
Function i wrote: 
---
<img width="890" height="402" alt="image" src="https://github.com/user-attachments/assets/b27cd66d-94e9-4461-bfa4-63ffd01e6597" />

Then i ran a Python3.py with correct password and obtained the flag

<img width="573" height="80" alt="image" src="https://github.com/user-attachments/assets/e9121400-b0eb-4952-a993-d6189d4fb02b" />

## Flag
*picoCTF{h45h_sl1ng1ng_36e992a6}*
