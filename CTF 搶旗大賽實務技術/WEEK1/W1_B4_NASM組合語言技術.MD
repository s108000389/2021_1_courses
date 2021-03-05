# nasm
```
https://zh.wikipedia.org/wiki/Netwide_Assembler

Netwide Assembler （簡稱 NASM）是一款基於英特爾 x86 架構的彙編與反彙編工具。
它可以用來編寫16位、32位（IA-32）和64位（x86-64）的程序。 
NASM被認為是Linux平台上最受歡迎的彙編工具之一。[1]

NASM 最初是在朱利安·霍爾的協助下由西蒙·泰瑟姆開發的。 
截至2016年，它被一個由H.Peter Anvin領導的小團隊所維護。
它是一款基於簡化版（二句版）BSD許可證的開放原始碼軟體。[3]
```
# 官方網址
```
https://www.nasm.us/


https://www.nasm.us/docs.php

https://www.nasm.us/xdoc/2.15.05/html/nasmdoc0.html
```
# 學習資源
```
Learn Assembly Language ==> NASM x86 assembly language on linux
https://asmtutor.com/
```
# 範例練習 1
```
NASM Tutorial

https://cs.lmu.edu/~ray/notes/nasmtutorial/
```

```
; ----------------------------------------------------------------------------------------
; Writes "Hello, World" to the console using only system calls. Runs on 64-bit Linux only.
; To assemble and run:
;
;     nasm -felf64 hello.asm && ld hello.o && ./a.out
; ----------------------------------------------------------------------------------------

          global    _start

          section   .text
_start:   mov       rax, 1                  ; system call for write
          mov       rdi, 1                  ; file handle 1 is stdout
          mov       rsi, message            ; address of string to output
          mov       rdx, 13                 ; number of bytes
          syscall                           ; invoke operating system to do the write
          mov       rax, 60                 ; system call for exit
          xor       rdi, rdi                ; exit code 0
          syscall                           ; invoke operating system to exit

          section   .data
message:  db        "Hello, World", 10      ; note the newline at the end
```
# 範例練習 2==> 32 位元
```
Learn Assembly Language ==> NASM x86 assembly language on linux
https://asmtutor.com/

https://asmtutor.com/#lesson1
```

```
; Hello World Program - asmtutor.com
; Compile with: nasm -f elf helloworld.asm
; Link with (64 bit systems require elf_i386 option): ld -m elf_i386 helloworld.o -o helloworld
; Run with: ./helloworld
 
SECTION .data
msg     db      'Hello World!', 0Ah     ; assign msg variable with your message string
 
SECTION .text
global  _start
 
_start:
 
    mov     edx, 13     ; number of bytes to write - one for each letter plus 0Ah (line feed character)
    mov     ecx, msg    ; move the memory address of our message string into ecx
    mov     ebx, 1      ; write to the STDOUT file
    mov     eax, 4      ; invoke SYS_WRITE (kernel opcode 4)
    int     80h
```
