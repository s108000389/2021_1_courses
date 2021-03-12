#
```
# Program 6.1
# Sum Program - GAS, Clang/LLVM on Linux (32-bit)
# Copyright (c) 2017 Hall & Slonka

.data ===========>初始化的變數
num1: .long 2
num2: .long 4

.text  ===========>程式
.globl _main, _sum
_main:   ===============>程式入口  

mov $10, %eax    ===========> %eax =10
dec %eax         ===========> %eax =9
mov $5, %ebx      ===========> %ebx =5

push num2         函數呼叫  ==>先把最右邊參數值押入stack
push num1                   ==>再把左邊參數值押入stack
push num1                   ==>正式  呼叫函數
call _sum                   
add $8, %esp

add %ebx, %eax
dec %eax

movl $1, %eax
movl $0, %ebx
int $0x80

_sum:   ===================>被呼叫的函數
push %ebp
mov %esp, %ebp
push %ebx

mov 8(%ebp), %ebx
mov 12(%ebp), %eax
add %ebx, %eax ===================>加法運算  %ebx + %eax -->%eax 
pop %ebx
pop %ebp
ret     ===================>回傳值就是 %eax 暫存器的數值

.end
```
