# 組合語言CTF實戰.md
```

PicoCTF2018-assembly-0
1-4.林思辰_read-asm
1-5.林思辰_run-asm
```

## PicoCTF2018-assembly-0
```
Reversing 150: assembly-0
Challenge

What does asm0(0xd8,0x7a) return? Submit the flag as a hexadecimal value (starting with 0x).

NOTE: Your submission for this question will NOT be in the normal flag format. 
Source located in the directory at /problems/assembly-0_1_fc43dbf0079fd5aab87236bf3bf4ac63.
```
```
.intel_syntax noprefix
.bits 32
	
.global asm0

asm0:
	push	ebp
	mov	ebp,esp
	mov	eax,DWORD PTR [ebp+0x8]
	mov	ebx,DWORD PTR [ebp+0xc]
	mov	eax,ebx
	mov	esp,ebp
	pop	ebp	
	ret
```

### Solution
```
.intel_syntax noprefix
.bits 32

.global asm0

asm0:
	push	ebp
	mov	ebp,esp
	mov	eax,DWORD PTR [ebp+0x8] ==>asm0(0xd8,0x7a)  
                                  DWORD PTR [ebp+0x8]==>0xd8  
                                  DWORD PTR [ebp+0xc]==>0x7a
	mov	ebx,DWORD PTR [ebp+0xc] ==>把DWORD PTR [ebp+0xc] 複製到 ebx
	mov	eax,ebx   ==>把ebx 複製到 eax
	mov	esp,ebp
	pop	ebp
	ret           ==> 回傳eax所存的值
  
we can deduce the output manually. ret will return the value of eax, 
which was set to the value of ebx (mov eax ebx), 
and ebx was set do the second argument we passed to the program (mov ebx,DWORD PTR [ebp+0xc]), 
which in this case was 0x7a

Flag ==> 0x7a
```


## 
```


```


## 
```


```



