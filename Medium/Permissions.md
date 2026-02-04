# Permissions - Category: General Skills
- Platform: PicoCTF
- Level: Medium

## Description

The task is to try to find a way to read root files

## Tools

- VIM

## Solution

First i check what kind of commands i can use

<img width="2480" height="261" alt="image" src="https://github.com/user-attachments/assets/adc8859c-d9a8-4e19-b42a-2f6d55581b5c" />

I noticed that i can use /usr/bin/vi as a root, so i checked a folder to see what kind of folders are inside 

`sudo /usr/bin/vi /challenge`

<img width="2483" height="906" alt="image" src="https://github.com/user-attachments/assets/2af8cb46-a15c-45b2-a03b-de28a8db3abf" />


Next i checked what is inside that file `metadata.json` and it contains a flag

`sudo /usr/bin/vi /challenge/metadata.json`

<img width="2119" height="215" alt="image" src="https://github.com/user-attachments/assets/325ca6bb-e572-4aef-8a3a-c3f285927213" />


## Flag
*picoCTF{uS1ng_v1m_3dit0r_55878b51}*
