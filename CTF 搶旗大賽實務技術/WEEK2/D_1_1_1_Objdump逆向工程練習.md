#
```


```

```

```

```
objdump -S  -j .text -M intel objd1 --no-show-raw-insn

objd1:     file format elf64-x86-64


Disassembly of section .text:

0000000000001040 <_start>:
    1040:	xor    ebp,ebp
    1042:	mov    r9,rdx
    1045:	pop    rsi
    1046:	mov    rdx,rsp
    1049:	and    rsp,0xfffffffffffffff0
    104d:	push   rax
    104e:	push   rsp
    104f:	lea    r8,[rip+0x13a]        # 1190 <__libc_csu_fini>
    1056:	lea    rcx,[rip+0xd3]        # 1130 <__libc_csu_init>
    105d:	lea    rdi,[rip+0xc1]        # 1125 <main>
    1064:	call   QWORD PTR [rip+0x2f76]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    106a:	hlt    
    106b:	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001070 <deregister_tm_clones>:
    1070:	lea    rdi,[rip+0x2fb1]        # 4028 <__TMC_END__>
    1077:	lea    rax,[rip+0x2faa]        # 4028 <__TMC_END__>
    107e:	cmp    rax,rdi
    1081:	je     1098 <deregister_tm_clones+0x28>
    1083:	mov    rax,QWORD PTR [rip+0x2f4e]        # 3fd8 <_ITM_deregisterTMCloneTable>
    108a:	test   rax,rax
    108d:	je     1098 <deregister_tm_clones+0x28>
    108f:	jmp    rax
    1091:	nop    DWORD PTR [rax+0x0]
    1098:	ret    
    1099:	nop    DWORD PTR [rax+0x0]

00000000000010a0 <register_tm_clones>:
    10a0:	lea    rdi,[rip+0x2f81]        # 4028 <__TMC_END__>
    10a7:	lea    rsi,[rip+0x2f7a]        # 4028 <__TMC_END__>
    10ae:	sub    rsi,rdi
    10b1:	sar    rsi,0x3
    10b5:	mov    rax,rsi
    10b8:	shr    rax,0x3f
    10bc:	add    rsi,rax
    10bf:	sar    rsi,1
    10c2:	je     10d8 <register_tm_clones+0x38>
    10c4:	mov    rax,QWORD PTR [rip+0x2f25]        # 3ff0 <_ITM_registerTMCloneTable>
    10cb:	test   rax,rax
    10ce:	je     10d8 <register_tm_clones+0x38>
    10d0:	jmp    rax
    10d2:	nop    WORD PTR [rax+rax*1+0x0]
    10d8:	ret    
    10d9:	nop    DWORD PTR [rax+0x0]

00000000000010e0 <__do_global_dtors_aux>:
    10e0:	cmp    BYTE PTR [rip+0x2f41],0x0        # 4028 <__TMC_END__>
    10e7:	jne    1118 <__do_global_dtors_aux+0x38>
    10e9:	push   rbp
    10ea:	cmp    QWORD PTR [rip+0x2f06],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    10f2:	mov    rbp,rsp
    10f5:	je     1103 <__do_global_dtors_aux+0x23>
    10f7:	mov    rdi,QWORD PTR [rip+0x2f22]        # 4020 <__dso_handle>
    10fe:	call   1030 <__cxa_finalize@plt>
    1103:	call   1070 <deregister_tm_clones>
    1108:	mov    BYTE PTR [rip+0x2f19],0x1        # 4028 <__TMC_END__>
    110f:	pop    rbp
    1110:	ret    
    1111:	nop    DWORD PTR [rax+0x0]
    1118:	ret    
    1119:	nop    DWORD PTR [rax+0x0]

0000000000001120 <frame_dummy>:
    1120:	jmp    10a0 <register_tm_clones>

0000000000001125 <main>:
// objd1.c
int main()
{
    1125:	push   rbp
    1126:	mov    rbp,rsp
   return 0;
    1129:	mov    eax,0x0
}
    112e:	pop    rbp
    112f:	ret    

0000000000001130 <__libc_csu_init>:
    1130:	push   r15
    1132:	mov    r15,rdx
    1135:	push   r14
    1137:	mov    r14,rsi
    113a:	push   r13
    113c:	mov    r13d,edi
    113f:	push   r12
    1141:	lea    r12,[rip+0x2cd0]        # 3e18 <__frame_dummy_init_array_entry>
    1148:	push   rbp
    1149:	lea    rbp,[rip+0x2cd0]        # 3e20 <__init_array_end>
    1150:	push   rbx
    1151:	sub    rbp,r12
    1154:	sub    rsp,0x8
    1158:	call   1000 <_init>
    115d:	sar    rbp,0x3
    1161:	je     117e <__libc_csu_init+0x4e>
    1163:	xor    ebx,ebx
    1165:	nop    DWORD PTR [rax]
    1168:	mov    rdx,r15
    116b:	mov    rsi,r14
    116e:	mov    edi,r13d
    1171:	call   QWORD PTR [r12+rbx*8]
    1175:	add    rbx,0x1
    1179:	cmp    rbp,rbx
    117c:	jne    1168 <__libc_csu_init+0x38>
    117e:	add    rsp,0x8
    1182:	pop    rbx
    1183:	pop    rbp
    1184:	pop    r12
    1186:	pop    r13
    1188:	pop    r14
    118a:	pop    r15
    118c:	ret    
    118d:	nop    DWORD PTR [rax]

0000000000001190 <__libc_csu_fini>:
    1190:	ret    

```
