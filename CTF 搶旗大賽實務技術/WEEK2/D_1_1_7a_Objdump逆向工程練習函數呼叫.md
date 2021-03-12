#
```
#include <stdio.h>
 
void printme()
{
    printf("Hello CTFer");
}
 
int main ()
{
   printme();
   return 0;
}
```

```
gcc -g func1.c -o func1
```

```
objdump -S  -M intel func1 --no-show-raw-insn

func1:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 &lt;_init&gt;:
    1000:	sub    rsp,0x8
    1004:	mov    rax,QWORD PTR [rip+0x2fdd]        # 3fe8 &lt;__gmon_start__&gt;
    100b:	test   rax,rax
    100e:	je     1012 &lt;_init+0x12&gt;
    1010:	call   rax
    1012:	add    rsp,0x8
    1016:	ret    

Disassembly of section .plt:

0000000000001020 &lt;.plt&gt;:
    1020:	push   QWORD PTR [rip+0x2fe2]        # 4008 &lt;_GLOBAL_OFFSET_TABLE_+0x8&gt;
    1026:	jmp    QWORD PTR [rip+0x2fe4]        # 4010 &lt;_GLOBAL_OFFSET_TABLE_+0x10&gt;
    102c:	nop    DWORD PTR [rax+0x0]

0000000000001030 &lt;printf@plt&gt;:
    1030:	jmp    QWORD PTR [rip+0x2fe2]        # 4018 &lt;printf@GLIBC_2.2.5&gt;
    1036:	push   0x0
    103b:	jmp    1020 &lt;.plt&gt;

Disassembly of section .plt.got:

0000000000001040 &lt;__cxa_finalize@plt&gt;:
    1040:	jmp    QWORD PTR [rip+0x2fb2]        # 3ff8 &lt;__cxa_finalize@GLIBC_2.2.5&gt;
    1046:	xchg   ax,ax

Disassembly of section .text:

0000000000001050 &lt;_start&gt;:
    1050:	xor    ebp,ebp
    1052:	mov    r9,rdx
    1055:	pop    rsi
    1056:	mov    rdx,rsp
    1059:	and    rsp,0xfffffffffffffff0
    105d:	push   rax
    105e:	push   rsp
    105f:	lea    r8,[rip+0x16a]        # 11d0 &lt;__libc_csu_fini&gt;
    1066:	lea    rcx,[rip+0x103]        # 1170 &lt;__libc_csu_init&gt;
    106d:	lea    rdi,[rip+0xd9]        # 114d &lt;main&gt;
    1074:	call   QWORD PTR [rip+0x2f66]        # 3fe0 &lt;__libc_start_main@GLIBC_2.2.5&gt;
    107a:	hlt    
    107b:	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001080 &lt;deregister_tm_clones&gt;:
    1080:	lea    rdi,[rip+0x2fa9]        # 4030 &lt;__TMC_END__&gt;
    1087:	lea    rax,[rip+0x2fa2]        # 4030 &lt;__TMC_END__&gt;
    108e:	cmp    rax,rdi
    1091:	je     10a8 &lt;deregister_tm_clones+0x28&gt;
    1093:	mov    rax,QWORD PTR [rip+0x2f3e]        # 3fd8 &lt;_ITM_deregisterTMCloneTable&gt;
    109a:	test   rax,rax
    109d:	je     10a8 &lt;deregister_tm_clones+0x28&gt;
    109f:	jmp    rax
    10a1:	nop    DWORD PTR [rax+0x0]
    10a8:	ret    
    10a9:	nop    DWORD PTR [rax+0x0]

00000000000010b0 &lt;register_tm_clones&gt;:
    10b0:	lea    rdi,[rip+0x2f79]        # 4030 &lt;__TMC_END__&gt;
    10b7:	lea    rsi,[rip+0x2f72]        # 4030 &lt;__TMC_END__&gt;
    10be:	sub    rsi,rdi
    10c1:	sar    rsi,0x3
    10c5:	mov    rax,rsi
    10c8:	shr    rax,0x3f
    10cc:	add    rsi,rax
    10cf:	sar    rsi,1
    10d2:	je     10e8 &lt;register_tm_clones+0x38&gt;
    10d4:	mov    rax,QWORD PTR [rip+0x2f15]        # 3ff0 &lt;_ITM_registerTMCloneTable&gt;
    10db:	test   rax,rax
    10de:	je     10e8 &lt;register_tm_clones+0x38&gt;
    10e0:	jmp    rax
    10e2:	nop    WORD PTR [rax+rax*1+0x0]
    10e8:	ret    
    10e9:	nop    DWORD PTR [rax+0x0]

00000000000010f0 &lt;__do_global_dtors_aux&gt;:
    10f0:	cmp    BYTE PTR [rip+0x2f39],0x0        # 4030 &lt;__TMC_END__&gt;
    10f7:	jne    1128 &lt;__do_global_dtors_aux+0x38&gt;
    10f9:	push   rbp
    10fa:	cmp    QWORD PTR [rip+0x2ef6],0x0        # 3ff8 &lt;__cxa_finalize@GLIBC_2.2.5&gt;
    1102:	mov    rbp,rsp
    1105:	je     1113 &lt;__do_global_dtors_aux+0x23&gt;
    1107:	mov    rdi,QWORD PTR [rip+0x2f1a]        # 4028 &lt;__dso_handle&gt;
    110e:	call   1040 &lt;__cxa_finalize@plt&gt;
    1113:	call   1080 &lt;deregister_tm_clones&gt;
    1118:	mov    BYTE PTR [rip+0x2f11],0x1        # 4030 &lt;__TMC_END__&gt;
    111f:	pop    rbp
    1120:	ret    
    1121:	nop    DWORD PTR [rax+0x0]
    1128:	ret    
    1129:	nop    DWORD PTR [rax+0x0]

0000000000001130 &lt;frame_dummy&gt;:
    1130:	jmp    10b0 &lt;register_tm_clones&gt;

0000000000001135 &lt;printme&gt;:
#include &lt;stdio.h&gt;
 
void printme()
{
    1135:	push   rbp
    1136:	mov    rbp,rsp
    printf(&quot;Hello CTFer&quot;);
    1139:	lea    rdi,[rip+0xec4]        # 2004 &lt;_IO_stdin_used+0x4&gt;
    1140:	mov    eax,0x0
    1145:	call   1030 &lt;printf@plt&gt;
}
    114a:	nop
    114b:	pop    rbp
    114c:	ret    

000000000000114d &lt;main&gt;:
 
int main ()
{
    114d:	push   rbp
    114e:	mov    rbp,rsp
   printme();
    1151:	mov    eax,0x0
    1156:	call   1135 &lt;printme&gt;
   return 0;
    115b:	mov    eax,0x0
}
    1160:	pop    rbp
    1161:	ret    
    1162:	nop    WORD PTR cs:[rax+rax*1+0x0]
    116c:	nop    DWORD PTR [rax+0x0]

0000000000001170 &lt;__libc_csu_init&gt;:
    1170:	push   r15
    1172:	mov    r15,rdx
    1175:	push   r14
    1177:	mov    r14,rsi
    117a:	push   r13
    117c:	mov    r13d,edi
    117f:	push   r12
    1181:	lea    r12,[rip+0x2c60]        # 3de8 &lt;__frame_dummy_init_array_entry&gt;
    1188:	push   rbp
    1189:	lea    rbp,[rip+0x2c60]        # 3df0 &lt;__init_array_end&gt;
    1190:	push   rbx
    1191:	sub    rbp,r12
    1194:	sub    rsp,0x8
    1198:	call   1000 &lt;_init&gt;
    119d:	sar    rbp,0x3
    11a1:	je     11be &lt;__libc_csu_init+0x4e&gt;
    11a3:	xor    ebx,ebx
    11a5:	nop    DWORD PTR [rax]
    11a8:	mov    rdx,r15
    11ab:	mov    rsi,r14
    11ae:	mov    edi,r13d
    11b1:	call   QWORD PTR [r12+rbx*8]
    11b5:	add    rbx,0x1
    11b9:	cmp    rbp,rbx
    11bc:	jne    11a8 &lt;__libc_csu_init+0x38&gt;
    11be:	add    rsp,0x8
    11c2:	pop    rbx
    11c3:	pop    rbp
    11c4:	pop    r12
    11c6:	pop    r13
    11c8:	pop    r14
    11ca:	pop    r15
    11cc:	ret    
    11cd:	nop    DWORD PTR [rax]

00000000000011d0 &lt;__libc_csu_fini&gt;:
    11d0:	ret    

Disassembly of section .fini:

00000000000011d4 &lt;_fini&gt;:
    11d4:	sub    rsp,0x8
    11d8:	add    rsp,0x8
    11dc:	ret  </pre>

```
