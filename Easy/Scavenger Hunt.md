# Scavenger Hunt - Category: Web Exploitation
- Platform: PicoCTF
- Level: Easy

## Description

There is some interesting information hidden around this site. Can you find it?

## Tools

- Curl
- Visual Studio Code

## Solution

First I download source files of the website `wget -mkxKE -e robots=off http:/[SITE]`, In html and css files was some part of the flag

HTML

<img width="707" height="142" alt="image" src="https://github.com/user-attachments/assets/ff1b462e-299b-41fa-89d4-37a84772b68a" />

CSS

<img width="1015" height="160" alt="image" src="https://github.com/user-attachments/assets/d319c428-48d2-4e96-8642-4aa6649b1be3" />

Then I checked file `/robots.txt` to see if i can get into antoher website

<img width="938" height="172" alt="image" src="https://github.com/user-attachments/assets/6833062b-b235-45e1-9a9c-e363167ad89f" />

I've got hint that this is Apache Server so i checked `/.htaccess` file

<img width="883" height="148" alt="image" src="https://github.com/user-attachments/assets/0fdc395f-8793-4ef8-b9c5-f3672d14e82e" />

I got another hint that this website was made on MacBook so i checked `/.DS_Store` file

<img width="932" height="128" alt="image" src="https://github.com/user-attachments/assets/4d7e5713-7e72-4b15-817f-04ede8bcae9d" />


## Flag
*picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_9588550}*
