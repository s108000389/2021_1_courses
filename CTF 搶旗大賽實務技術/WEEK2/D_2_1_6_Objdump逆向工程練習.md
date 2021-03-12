#
```

```

```
#include<stdio.h>
 
int main()
{
    int num;
 
    printf("PLEASE INPUT A POSITIVE INTERGER: ");
    scanf("%d",&num);
 
    (num%2==0)?printf("EVEN"):printf("ODD");
}
```
```
KALI-64

gcc -g objd5.c -o objd5
```

```
objdump -S  -M intel objd5 --no-show-raw-insn

objd5:     file format elf64-x86-64


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

0000000000001040 <__isoc99_scanf@plt>:
    1040:	jmp    QWORD PTR [rip+0x2fda]        # 4020 <__isoc99_scanf@GLIBC_2.7>
    1046:	push   0x1
    104b:	jmp    1020 <.plt>

Disassembly of section .plt.got:

0000000000001050 <__cxa_finalize@plt>:
    1050:	jmp    QWORD PTR [rip+0x2fa2]        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1056:	xchg   ax,ax

Disassembly of section .text:

0000000000001060 <_start>:
    1060:	xor    ebp,ebp
    1062:	mov    r9,rdx
    1065:	pop    rsi
    1066:	mov    rdx,rsp
    1069:	and    rsp,0xfffffffffffffff0
    106d:	push   rax
    106e:	push   rsp
    106f:	lea    r8,[rip+0x19a]        # 1210 <__libc_csu_fini>
    1076:	lea    rcx,[rip+0x133]        # 11b0 <__libc_csu_init>
    107d:	lea    rdi,[rip+0xc1]        # 1145 <main>
    1084:	call   QWORD PTR [rip+0x2f56]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    108a:	hlt    
    108b:	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001090 <deregister_tm_clones>:
    1090:	lea    rdi,[rip+0x2fa1]        # 4038 <__TMC_END__>
    1097:	lea    rax,[rip+0x2f9a]        # 4038 <__TMC_END__>
    109e:	cmp    rax,rdi
    10a1:	je     10b8 <deregister_tm_clones+0x28>
    10a3:	mov    rax,QWORD PTR [rip+0x2f2e]        # 3fd8 <_ITM_deregisterTMCloneTable>
    10aa:	test   rax,rax
    10ad:	je     10b8 <deregister_tm_clones+0x28>
    10af:	jmp    rax
    10b1:	nop    DWORD PTR [rax+0x0]
    10b8:	ret    
    10b9:	nop    DWORD PTR [rax+0x0]

00000000000010c0 <register_tm_clones>:
    10c0:	lea    rdi,[rip+0x2f71]        # 4038 <__TMC_END__>
    10c7:	lea    rsi,[rip+0x2f6a]        # 4038 <__TMC_END__>
    10ce:	sub    rsi,rdi
    10d1:	sar    rsi,0x3
    10d5:	mov    rax,rsi
    10d8:	shr    rax,0x3f
    10dc:	add    rsi,rax
    10df:	sar    rsi,1
    10e2:	je     10f8 <register_tm_clones+0x38>
    10e4:	mov    rax,QWORD PTR [rip+0x2f05]        # 3ff0 <_ITM_registerTMCloneTable>
    10eb:	test   rax,rax
    10ee:	je     10f8 <register_tm_clones+0x38>
    10f0:	jmp    rax
    10f2:	nop    WORD PTR [rax+rax*1+0x0]
    10f8:	ret    
    10f9:	nop    DWORD PTR [rax+0x0]

0000000000001100 <__do_global_dtors_aux>:
    1100:	cmp    BYTE PTR [rip+0x2f31],0x0        # 4038 <__TMC_END__>
    1107:	jne    1138 <__do_global_dtors_aux+0x38>
    1109:	push   rbp
    110a:	cmp    QWORD PTR [rip+0x2ee6],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1112:	mov    rbp,rsp
    1115:	je     1123 <__do_global_dtors_aux+0x23>
    1117:	mov    rdi,QWORD PTR [rip+0x2f12]        # 4030 <__dso_handle>
    111e:	call   1050 <__cxa_finalize@plt>
    1123:	call   1090 <deregister_tm_clones>
    1128:	mov    BYTE PTR [rip+0x2f09],0x1        # 4038 <__TMC_END__>
    112f:	pop    rbp
    1130:	ret    
    1131:	nop    DWORD PTR [rax+0x0]
    1138:	ret    
    1139:	nop    DWORD PTR [rax+0x0]

0000000000001140 <frame_dummy>:
    1140:	jmp    10c0 <register_tm_clones>

0000000000001145 <main>:
#include<stdio.h>
 
int main()
{
    1145:	push   rbp
    1146:	mov    rbp,rsp
    1149:	sub    rsp,0x10
    int num;
 
    printf("PLEASE INPUT A POSITIVE INTERGER: ");
    114d:	lea    rdi,[rip+0xeb4]        # 2008 <_IO_stdin_used+0x8>
    1154:	mov    eax,0x0
    1159:	call   1030 <printf@plt>
    scanf("%d",&num);
    115e:	lea    rax,[rbp-0x4]
    1162:	mov    rsi,rax
    1165:	lea    rdi,[rip+0xebf]        # 202b <_IO_stdin_used+0x2b>
    116c:	mov    eax,0x0
    1171:	call   1040 <__isoc99_scanf@plt>
 
    (num%2==0)?printf("EVEN"):printf("ODD");
    1176:	mov    eax,DWORD PTR [rbp-0x4]
    1179:	and    eax,0x1
    117c:	test   eax,eax
    117e:	jne    1193 <main+0x4e>
    1180:	lea    rdi,[rip+0xea7]        # 202e <_IO_stdin_used+0x2e>
    1187:	mov    eax,0x0
    118c:	call   1030 <printf@plt>
    1191:	jmp    11a4 <main+0x5f>
    1193:	lea    rdi,[rip+0xe99]        # 2033 <_IO_stdin_used+0x33>
    119a:	mov    eax,0x0
    119f:	call   1030 <printf@plt>
    11a4:	mov    eax,0x0
}
    11a9:	leave  
    11aa:	ret    
    11ab:	nop    DWORD PTR [rax+rax*1+0x0]

00000000000011b0 <__libc_csu_init>:
    11b0:	push   r15
    11b2:	mov    r15,rdx
    11b5:	push   r14
    11b7:	mov    r14,rsi
    11ba:	push   r13
    11bc:	mov    r13d,edi
    11bf:	push   r12
    11c1:	lea    r12,[rip+0x2c20]        # 3de8 <__frame_dummy_init_array_entry>
    11c8:	push   rbp
    11c9:	lea    rbp,[rip+0x2c20]        # 3df0 <__init_array_end>
    11d0:	push   rbx
    11d1:	sub    rbp,r12
    11d4:	sub    rsp,0x8
    11d8:	call   1000 <_init>
    11dd:	sar    rbp,0x3
    11e1:	je     11fe <__libc_csu_init+0x4e>
    11e3:	xor    ebx,ebx
    11e5:	nop    DWORD PTR [rax]
    11e8:	mov    rdx,r15
    11eb:	mov    rsi,r14
    11ee:	mov    edi,r13d
    11f1:	call   QWORD PTR [r12+rbx*8]
    11f5:	add    rbx,0x1
    11f9:	cmp    rbp,rbx
    11fc:	jne    11e8 <__libc_csu_init+0x38>
    11fe:	add    rsp,0x8
    1202:	pop    rbx
    1203:	pop    rbp
    1204:	pop    r12
    1206:	pop    r13
    1208:	pop    r14
    120a:	pop    r15
    120c:	ret    
    120d:	nop    DWORD PTR [rax]

0000000000001210 <__libc_csu_fini>:
    1210:	ret    

Disassembly of section .fini:

0000000000001214 <_fini>:
    1214:	sub    rsp,0x8
    1218:	add    rsp,0x8
    121c:	ret  
```
