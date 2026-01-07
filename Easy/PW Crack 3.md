# PW Crack 3 - Category: Python
- Platform: PicoCTF
- Level: Easy

## Description

Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Tools

- Binary Visual Editor (bvi)
- nano (text editor)

## Solution

First I check file level3.py and found out there are listed 7 password whith one being the correct one, also i found out that this program uses md5 hashes

<img width="941" height="919" alt="image" src="https://github.com/user-attachments/assets/9526612a-95a3-4355-9f6a-5abf2c19bb9a" />

Then I checked file *level3.hash.bin* with *bvi* and saw that there is MD5 type hash

<img width="1250" height="644" alt="image" src="https://github.com/user-attachments/assets/8c17fb71-ec33-4ff8-99e1-24ab5ec03557" />

Next i pasted this stored hash into a decryption website (https://md5decrypt.net/en/) and found out that this hash contains a correct password (87ab)

<img width="1452" height="607" alt="image" src="https://github.com/user-attachments/assets/3b3817ca-9f09-45fe-9b93-df4a8baeee45" />

Then i ran a Python3.py with correct password and obtained the flag

## Flag
*picoCTF{m45h_fl1ng1ng_cd6ed2eb}*








