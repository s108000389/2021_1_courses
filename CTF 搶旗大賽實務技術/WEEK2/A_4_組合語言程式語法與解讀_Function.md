# 函數
```
產生預設的AT&T 語法的組合語言
    gcc -S func1.c -o func1.s

產生intel 語法的組合語言
    gcc -S -masm=intel func1.c -o func1_intel.s
```
# 範例程式
```
#include <stdio.h>
 
/* 函式宣告 */
int max(int num1, int num2);
 
int main ()
{
   /* 區域變數定義 */
   int a = 100;
   int b = 200;
   int ret;
 
   /* 調用函數來獲取最大值 */
   ret = max(a, b);
 
   printf( "Max value is : %d\n", ret );
 
   return 0;
}
 
/* 函數返回兩個數中較大的那個數 */
int max(int num1, int num2) 
{
   /* 區域變數聲明 */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```
### 產生預設的AT&T 語法的組合語言
```
ksu@KSU-Ubuntu-1604-32:~$ gcc -S func1.c -o func1.s
ksu@KSU-Ubuntu-1604-32:~$ cat func1.s
```

```
	.file	"func1.c"
	.section	.rodata
.LC0:
	.string	"Max value is : %d\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	leal	4(%esp), %ecx
	.cfi_def_cfa 1, 0
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	.cfi_escape 0x10,0x5,0x2,0x75,0
	movl	%esp, %ebp
	pushl	%ecx
	.cfi_escape 0xf,0x3,0x75,0x7c,0x6
	subl	$20, %esp
	movl	$100, -20(%ebp)
	movl	$200, -16(%ebp)
	subl	$8, %esp
	pushl	-16(%ebp)
	pushl	-20(%ebp)
	call	max
	addl	$16, %esp
	movl	%eax, -12(%ebp)
	subl	$8, %esp
	pushl	-12(%ebp)
	pushl	$.LC0
	call	printf
	addl	$16, %esp
	movl	$0, %eax
	movl	-4(%ebp), %ecx
	.cfi_def_cfa 1, 0
	leave
	.cfi_restore 5
	leal	-4(%ecx), %esp
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.globl	max
	.type	max, @function
max:
.LFB1:
	.cfi_startproc
	pushl	%ebp
	.cfi_def_cfa_offset 8
	.cfi_offset 5, -8
	movl	%esp, %ebp
	.cfi_def_cfa_register 5
	subl	$16, %esp
	movl	8(%ebp), %eax
	cmpl	12(%ebp), %eax
	jle	.L4
	movl	8(%ebp), %eax
	movl	%eax, -4(%ebp)
	jmp	.L5
.L4:
	movl	12(%ebp), %eax
	movl	%eax, -4(%ebp)
.L5:
	movl	-4(%ebp), %eax
	leave
	.cfi_restore 5
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE1:
	.size	max, .-max
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```
### 產生intel 語法的組合語言
```
ksu@KSU-Ubuntu-1604-32:~$ gcc -S -masm=intel func1.c -o func1_intel.s
ksu@KSU-Ubuntu-1604-32:~$ cat func1_intel.s 
```
```
.file	"func1.c"
	.intel_syntax noprefix
	.section	.rodata
.LC0:
	.string	"Max value is : %d\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	lea	ecx, [esp+4]
	.cfi_def_cfa 1, 0
	and	esp, -16
	push	DWORD PTR [ecx-4]
	push	ebp
	.cfi_escape 0x10,0x5,0x2,0x75,0
	mov	ebp, esp
	push	ecx
	.cfi_escape 0xf,0x3,0x75,0x7c,0x6
	sub	esp, 20
	mov	DWORD PTR [ebp-20], 100
	mov	DWORD PTR [ebp-16], 200
	sub	esp, 8
	push	DWORD PTR [ebp-16]
	push	DWORD PTR [ebp-20]
	call	max
	add	esp, 16
	mov	DWORD PTR [ebp-12], eax
	sub	esp, 8
	push	DWORD PTR [ebp-12]
	push	OFFSET FLAT:.LC0
	call	printf
	add	esp, 16
	mov	eax, 0
	mov	ecx, DWORD PTR [ebp-4]
	.cfi_def_cfa 1, 0
	leave
	.cfi_restore 5
	lea	esp, [ecx-4]
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.globl	max
	.type	max, @function
max:
.LFB1:
	.cfi_startproc
	push	ebp
	.cfi_def_cfa_offset 8
	.cfi_offset 5, -8
	mov	ebp, esp
	.cfi_def_cfa_register 5
	sub	esp, 16
	mov	eax, DWORD PTR [ebp+8]
	cmp	eax, DWORD PTR [ebp+12]
	jle	.L4
	mov	eax, DWORD PTR [ebp+8]
	mov	DWORD PTR [ebp-4], eax
	jmp	.L5
.L4:
	mov	eax, DWORD PTR [ebp+12]
	mov	DWORD PTR [ebp-4], eax
.L5:
	mov	eax, DWORD PTR [ebp-4]
	leave
	.cfi_restore 5
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE1:
	.size	max, .-max
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits

```
