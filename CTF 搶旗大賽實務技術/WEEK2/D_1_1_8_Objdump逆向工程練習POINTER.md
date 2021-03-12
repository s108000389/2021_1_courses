# POINTER1.C
```
#include <stdio.h>
 
int main ()
{
    int var_CTF = 10;
    int *p;             
    p = &var_CTF;
 
   printf("var_CTF ADDRESS@MEMORY： %p\n", p);
   return 0;
}
```
```
KALI-64

gcc -g objd5.c -o objd5
```
```
objdump -S  -M intel pointer1 --no-show-raw-insn

pointer1:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <main>:
#include <stdio.h>
 
int main ()
{
   0:	push   rbp
   1:	mov    rbp,rsp
   4:	sub    rsp,0x10
    int var_CTF = 10;
   8:	mov    DWORD PTR [rbp-0xc],0xa
    int *p;             
    p = &var_CTF;
   f:	lea    rax,[rbp-0xc]
  13:	mov    QWORD PTR [rbp-0x8],rax
 
   printf("var_CTF ADDRESS@MEMORY： %p\n", p);
  17:	mov    rax,QWORD PTR [rbp-0x8]
  1b:	mov    rsi,rax
  1e:	lea    rdi,[rip+0x0]        # 25 <main+0x25>
  25:	mov    eax,0x0
  2a:	call   2f <main+0x2f>
   return 0;
  2f:	mov    eax,0x0
}
  34:	leave  
  35:	ret  
```
