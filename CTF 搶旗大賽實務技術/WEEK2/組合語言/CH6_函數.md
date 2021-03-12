#
```
# Program 6.1
# Sum Program - GAS, Clang/LLVM on Linux (32-bit)
# Copyright (c) 2017 Hall & Slonka

.data ===========>初始化的變數 儲存在此區段   GAS 版本的代碼是以.data 段開頭的
num1: .long 2     其中定義了值為2 的變數numl 以及值為4 的變數num2 。這兩個變數都是32 位元的。
num2: .long 4

.text  ===========>程式 儲存在此區段  包含本程式的可執行指令。
.globl _main, _sum  ========> 聲明了兩個全域函數＿main 與＿sum
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
push %ebp       ====> 函數序言(function prologue,函數開場）:每次呼叫函數時都要從這些入口代碼開始執行
mov %esp, %ebp  ====> 函數序言(function prologue,函數開場）:每次呼叫函數時都要從這些入口代碼開始執行
push %ebx

mov 8(%ebp), %ebx
mov 12(%ebp), %eax
add %ebx, %eax ===================>加法運算  %ebx + %eax -->%eax 
pop %ebx
pop %ebp
ret     

.end
```
