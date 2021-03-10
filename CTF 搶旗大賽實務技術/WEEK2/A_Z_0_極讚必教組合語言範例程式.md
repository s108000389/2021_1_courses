# 好書
```
匯編程序設計與電腦體系結構：軟件工程師教程
[美］布萊恩·R. 霍爾（Brian R. Hall） 　凱文·J.斯隆卡（Kevin J. Slonka）　著
匯編程序設計與電腦體系結構：軟件工程師教程
機械工業  2019-04-01
https://github.com/brianrhall/Assembly

https://www.tenlong.com.tw/products/9787111615163

https://github.com/brianrhall/Assembly
```
# 第3章　組合語言及其語法的基礎知識
## x86/Program_3.1_GAS_Linux.s
```
# Program 3.1
# Sample Assembly Program - GAS, Clang/LLVM on Linux (32-bit)
# Copyright (c) 2017 Hall & Slonka

.data
sum: .long 0

.text
.globl _main
_main:
movl $25, %eax
movl $50, %ebx
addl %ebx, %eax
movl %eax, sum

movl $1, %eax
movl $0, %ebx
int $0x80
.end
```
## x86/Program_3.1_NASM.asm
```
; Program 3.1
; Sample Assembly Program - NASM (32-bit)
; Copyright (c) 2017 Hall & Slonka

SECTION .data
sum: DD 0

SECTION .text
global _main
_main:
mov eax, 25
mov ebx, 50
add eax, ebx
mov DWORD [sum], eax

mov eax, 1
mov ebx, 0
int 80h
```
## x86_64/Program_3.1_GAS_Linux.s
```
# Program 3.1
# Sample Assembly Program - GAS, Clang/LLVM on Linux (64-bit)
# Copyright (c) 2020 Hall & Slonka

.data
sum: .quad 0

.text
.global _main
_main:
mov $25, %rax
mov $50, %rbx
add %rbx, %rax
mov %rax, sum(%rip)

mov $60, %rax
xor %rdi, %rdi
syscall
.end
```
## x86_64/Program_3.1_NASM.asm
```
; Program 3.1
; Sample Assembly Program - NASM (64-bit)
; Copyright (c) 2020 Hall & Slonka

SECTION .data 
sum: DQ 0

SECTION .text
global _main
_main:
mov rax, 25
mov rbx, 50 
add rax, rbx
mov QWORD [sum], rax

mov rax, 60
xor rdi, rdi
syscall
```
# 完成底下程式註解說明
## Program 3.2/x86/Program_3.2_GAS_Linux.s
```
# Program 3.2
# Working Example - GAS, Clang/LLVM on Linux (32-bit)
# Copyright (c) 2017 Hall & Slonka

.data                             # Section for variable definitions

decimalLiteral:    .byte 31       # Variable storing 31
hexLiteral:        .long 0xF      # Variable storing F (15 in decimal)
charLiteral:       .byte 'A'      # Variable storing 65 in decimal

# Variable containing a string that has a line break and is null-terminated
stringLiteral:     .ascii "This string has\na line break in it.\0"

# Variable that calculates the value of an expression to determine the
# length, in bytes, of the variable "stringLiteral" by subtracting the
# starting memory address of the variable from the current memory address
.equ lenString, (. - stringLiteral)

.bss                              # Section for uninitialized variables
.lcomm unInitVariable, 4          # Uninitialized, 4-byte variable

.text                             # Section for instructions
.globl _main                      # Make the label "_main"
                                  # available to the linker as an
                                  # entry point for the program
_main:                            # Label for program entry

# Label and instruction on
# the same line below
partOne: movl $10, %eax           # Assign 10 to the eax register
addl hexLiteral, %eax             # Add the value in hexLiteral to
                                  # the contents of the eax register
                                  # and store the result in eax

partTwo:                          # Label on its own line
inc %eax                          # Increment the value in eax

movl $1, %eax                     # Indicate exit system call code (1)
movl $0, %ebx                     # Return value of the program (0)
int $0x80                         # Issue the kernel interrupt
.end                              # End assembling
```

## Program 3.2/x86/Program_3.2_NASM.asm
```
; Program 3.2
; Working Example - NASM (32-bit)
; Copyright (c) 2017 Hall & Slonka

SECTION .data                     ; Section for variable definitions

decimalLiteral:   DB 31           ; Variable storing 31
hexLiteral:       DD 0Fh          ; Variable storing F (15 in decimal)
charLiteral:      DB 'A'          ; Variable storing 65 in decimal

; Variable containing a string that has a line break and is null-terminated
stringLiteral:    DB "This is a string that",0ah
                  DB "has a line break in it.",0

; Variable that calculates the value of an expression to determine the
; length, in bytes, of the variable "stringLiteral" by subtracting the
; starting memory address of the variable from the current memory address
lenString:        EQU ($ - stringLiteral)

SECTION .bss                      ; Section for uninitialized variables
unInitVariable:   RESD 1          ; 4-byte uninitialized variable

SECTION .text                     ; Section for instructions
global _main                      ; Make the label "_main"
                                  ; available to the linker as an
                                  ; entry point for the program
_main:                            ; Label for program entry

; Label and instruction on
; the same line below
partOne: mov eax, 10              ; Assign 10 to the eax register
add eax, hexLiteral               ; Add the value in hexLiteral to
                                  ; the contents of the eax register
                                  ; and store the result in eax

partTwo:                          ; Label on its own line
inc eax                           ; Increment the value in eax

mov eax, 1                        ; Indicate exit system call code (1)
mov ebx, 0                        ; Return value of the program (0)
int 80h                           ; Issue the kernel interrupt
```

##
```

```
