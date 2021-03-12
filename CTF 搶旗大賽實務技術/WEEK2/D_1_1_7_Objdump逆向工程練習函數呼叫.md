# func2.c
```
#include <stdio.h>

/* 函數告宣告 */
int max(int num1, int num2);
 
int main ()
{
   int a = 100;
   int b = 200;
   int ret;
 
   ret = max(a, b); 
   printf( "Max value is : %d\n", ret );
   return 0;
}
 

int max(int num1, int num2) 
{
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```
```
KALI-64

gcc -g func2.c -o func2
```
```
objdump -S  -M intel func2 --no-show-raw-insn


objdump -S  -M intel func2 --no-show-raw-insn

func2:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 <_init>:
    1000:	sub    rsp,0x8
    1004:	mov    rax,QWORD PTR [rip+0x2fdd]        # 3fe8 <__gmon_start__>
    100b:	test   rax,rax
    100e:	je     1012 <_init+0x12>
    1010:	call   rax
    1012:	add    rsp,0x8
    1016:	ret    

Disassembly of section .plt:

0000000000001020 <.plt>:
    1020:	push   QWORD PTR [rip+0x2fe2]        # 4008 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026:	jmp    QWORD PTR [rip+0x2fe4]        # 4010 <_GLOBAL_OFFSET_TABLE_+0x10>
    102c:	nop    DWORD PTR [rax+0x0]

0000000000001030 <printf@plt>:
    1030:	jmp    QWORD PTR [rip+0x2fe2]        # 4018 <printf@GLIBC_2.2.5>
    1036:	push   0x0
    103b:	jmp    1020 <.plt>

Disassembly of section .plt.got:

0000000000001040 <__cxa_finalize@plt>:
    1040:	jmp    QWORD PTR [rip+0x2fb2]        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1046:	xchg   ax,ax

Disassembly of section .text:

0000000000001050 <_start>:
    1050:	xor    ebp,ebp
    1052:	mov    r9,rdx
    1055:	pop    rsi
    1056:	mov    rdx,rsp
    1059:	and    rsp,0xfffffffffffffff0
    105d:	push   rax
    105e:	push   rsp
    105f:	lea    r8,[rip+0x19a]        # 1200 <__libc_csu_fini>
    1066:	lea    rcx,[rip+0x133]        # 11a0 <__libc_csu_init>
    106d:	lea    rdi,[rip+0xc1]        # 1135 <main>
    1074:	call   QWORD PTR [rip+0x2f66]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    107a:	hlt    
    107b:	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001080 <deregister_tm_clones>:
    1080:	lea    rdi,[rip+0x2fa9]        # 4030 <__TMC_END__>
    1087:	lea    rax,[rip+0x2fa2]        # 4030 <__TMC_END__>
    108e:	cmp    rax,rdi
    1091:	je     10a8 <deregister_tm_clones+0x28>
    1093:	mov    rax,QWORD PTR [rip+0x2f3e]        # 3fd8 <_ITM_deregisterTMCloneTable>
    109a:	test   rax,rax
    109d:	je     10a8 <deregister_tm_clones+0x28>
    109f:	jmp    rax
    10a1:	nop    DWORD PTR [rax+0x0]
    10a8:	ret    
    10a9:	nop    DWORD PTR [rax+0x0]

00000000000010b0 <register_tm_clones>:
    10b0:	lea    rdi,[rip+0x2f79]        # 4030 <__TMC_END__>
    10b7:	lea    rsi,[rip+0x2f72]        # 4030 <__TMC_END__>
    10be:	sub    rsi,rdi
    10c1:	sar    rsi,0x3
    10c5:	mov    rax,rsi
    10c8:	shr    rax,0x3f
    10cc:	add    rsi,rax
    10cf:	sar    rsi,1
    10d2:	je     10e8 <register_tm_clones+0x38>
    10d4:	mov    rax,QWORD PTR [rip+0x2f15]        # 3ff0 <_ITM_registerTMCloneTable>
    10db:	test   rax,rax
    10de:	je     10e8 <register_tm_clones+0x38>
    10e0:	jmp    rax
    10e2:	nop    WORD PTR [rax+rax*1+0x0]
    10e8:	ret    
    10e9:	nop    DWORD PTR [rax+0x0]

00000000000010f0 <__do_global_dtors_aux>:
    10f0:	cmp    BYTE PTR [rip+0x2f39],0x0        # 4030 <__TMC_END__>
    10f7:	jne    1128 <__do_global_dtors_aux+0x38>
    10f9:	push   rbp
    10fa:	cmp    QWORD PTR [rip+0x2ef6],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1102:	mov    rbp,rsp
    1105:	je     1113 <__do_global_dtors_aux+0x23>
    1107:	mov    rdi,QWORD PTR [rip+0x2f1a]        # 4028 <__dso_handle>
    110e:	call   1040 <__cxa_finalize@plt>
    1113:	call   1080 <deregister_tm_clones>
    1118:	mov    BYTE PTR [rip+0x2f11],0x1        # 4030 <__TMC_END__>
    111f:	pop    rbp
    1120:	ret    
    1121:	nop    DWORD PTR [rax+0x0]
    1128:	ret    
    1129:	nop    DWORD PTR [rax+0x0]

0000000000001130 <frame_dummy>:
    1130:	jmp    10b0 <register_tm_clones>

0000000000001135 <main>:

/* 函數告宣告 */
int max(int num1, int num2);
 
int main ()
{
    1135:	push   rbp
    1136:	mov    rbp,rsp
    1139:	sub    rsp,0x10
   int a = 100;
    113d:	mov    DWORD PTR [rbp-0x4],0x64
   int b = 200;
    1144:	mov    DWORD PTR [rbp-0x8],0xc8
   int ret;
 
   ret = max(a, b); 
    114b:	mov    edx,DWORD PTR [rbp-0x8]
    114e:	mov    eax,DWORD PTR [rbp-0x4]
    1151:	mov    esi,edx
    1153:	mov    edi,eax
    1155:	call   117a <max>
    115a:	mov    DWORD PTR [rbp-0xc],eax
   printf( "Max value is : %d\n", ret );
    115d:	mov    eax,DWORD PTR [rbp-0xc]
    1160:	mov    esi,eax
    1162:	lea    rdi,[rip+0xe9b]        # 2004 <_IO_stdin_used+0x4>
    1169:	mov    eax,0x0
    116e:	call   1030 <printf@plt>
   return 0;
    1173:	mov    eax,0x0
}
    1178:	leave  
    1179:	ret    

000000000000117a <max>:
 

int max(int num1, int num2) 
{
    117a:	push   rbp
    117b:	mov    rbp,rsp
    117e:	mov    DWORD PTR [rbp-0x14],edi
    1181:	mov    DWORD PTR [rbp-0x18],esi
   int result;
 
   if (num1 > num2)
    1184:	mov    eax,DWORD PTR [rbp-0x14]
    1187:	cmp    eax,DWORD PTR [rbp-0x18]
    118a:	jle    1194 <max+0x1a>
      result = num1;
    118c:	mov    eax,DWORD PTR [rbp-0x14]
    118f:	mov    DWORD PTR [rbp-0x4],eax
    1192:	jmp    119a <max+0x20>
   else
      result = num2;
    1194:	mov    eax,DWORD PTR [rbp-0x18]
    1197:	mov    DWORD PTR [rbp-0x4],eax
 
   return result; 
    119a:	mov    eax,DWORD PTR [rbp-0x4]
}
    119d:	pop    rbp
    119e:	ret    
    119f:	nop

00000000000011a0 <__libc_csu_init>:
    11a0:	push   r15
    11a2:	mov    r15,rdx
    11a5:	push   r14
    11a7:	mov    r14,rsi
    11aa:	push   r13
    11ac:	mov    r13d,edi
    11af:	push   r12
    11b1:	lea    r12,[rip+0x2c30]        # 3de8 <__frame_dummy_init_array_entry>
    11b8:	push   rbp
    11b9:	lea    rbp,[rip+0x2c30]        # 3df0 <__init_array_end>
    11c0:	push   rbx
    11c1:	sub    rbp,r12
    11c4:	sub    rsp,0x8
    11c8:	call   1000 <_init>
    11cd:	sar    rbp,0x3
    11d1:	je     11ee <__libc_csu_init+0x4e>
    11d3:	xor    ebx,ebx
    11d5:	nop    DWORD PTR [rax]
    11d8:	mov    rdx,r15
    11db:	mov    rsi,r14
    11de:	mov    edi,r13d
    11e1:	call   QWORD PTR [r12+rbx*8]
    11e5:	add    rbx,0x1
    11e9:	cmp    rbp,rbx
    11ec:	jne    11d8 <__libc_csu_init+0x38>
    11ee:	add    rsp,0x8
    11f2:	pop    rbx
    11f3:	pop    rbp
    11f4:	pop    r12
    11f6:	pop    r13
    11f8:	pop    r14
    11fa:	pop    r15
    11fc:	ret    
    11fd:	nop    DWORD PTR [rax]

0000000000001200 <__libc_csu_fini>:
    1200:	ret    

Disassembly of section .fini:

0000000000001204 <_fini>:
    1204:	sub    rsp,0x8
    1208:	add    rsp,0x8
    120c:	ret   
```
