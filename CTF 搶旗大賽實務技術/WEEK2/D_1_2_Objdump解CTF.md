# D_1_1_Objdump解CTF.md
```
InCTF Junior　blade
https://medium.com/@amustaque97/demystify-reverse-engineering-ctf-challenge-blade-40c45e7933c0
```
```
easyCTF-2018-Adder
https://github.com/asinggih/easyCTF-2018-writeups/blob/master/Reverse_Engineering/Adder.md
```

# InCTF Junior　blade
```
objdump -S -j .text -M intel blade --no-show-raw-insn

blade:     file format elf32-i386

Disassembly of section .text:

08048420 <_start>:
 8048420:	xor    ebp,ebp
 8048422:	pop    esi
 8048423:	mov    ecx,esp
 8048425:	and    esp,0xfffffff0
 8048428:	push   eax
 8048429:	push   esp
 804842a:	push   edx
 804842b:	call   8048453 <_start+0x33>
 8048430:	add    ebx,0x1bd0
 8048436:	lea    eax,[ebx-0x18c0]
 804843c:	push   eax
 804843d:	lea    eax,[ebx-0x1920]
 8048443:	push   eax
 8048444:	push   ecx
 8048445:	push   esi
 8048446:	mov    eax,0x804864d
 804844c:	push   eax
 804844d:	call   80483e0 <__libc_start_main@plt>
 8048452:	hlt    
 8048453:	mov    ebx,DWORD PTR [esp]
 8048456:	ret    
 8048457:	xchg   ax,ax
 8048459:	xchg   ax,ax
 804845b:	xchg   ax,ax
 804845d:	xchg   ax,ax
 804845f:	nop

08048460 <_dl_relocate_static_pie>:
 8048460:	repz ret 
 8048462:	xchg   ax,ax
 8048464:	xchg   ax,ax
 8048466:	xchg   ax,ax
 8048468:	xchg   ax,ax
 804846a:	xchg   ax,ax
 804846c:	xchg   ax,ax
 804846e:	xchg   ax,ax

08048470 <__x86.get_pc_thunk.bx>:
 8048470:	mov    ebx,DWORD PTR [esp]
 8048473:	ret    
 8048474:	xchg   ax,ax
 8048476:	xchg   ax,ax
 8048478:	xchg   ax,ax
 804847a:	xchg   ax,ax
 804847c:	xchg   ax,ax
 804847e:	xchg   ax,ax

08048480 <deregister_tm_clones>:
 8048480:	mov    eax,0x804a02c
 8048485:	cmp    eax,0x804a02c
 804848a:	je     80484b0 <deregister_tm_clones+0x30>
 804848c:	mov    eax,0x0
 8048491:	test   eax,eax
 8048493:	je     80484b0 <deregister_tm_clones+0x30>
 8048495:	push   ebp
 8048496:	mov    ebp,esp
 8048498:	sub    esp,0x14
 804849b:	push   0x804a02c
 80484a0:	call   eax
 80484a2:	add    esp,0x10
 80484a5:	leave  
 80484a6:	ret    
 80484a7:	mov    esi,esi
 80484a9:	lea    edi,[edi+eiz*1+0x0]
 80484b0:	repz ret 
 80484b2:	lea    esi,[esi+eiz*1+0x0]
 80484b9:	lea    edi,[edi+eiz*1+0x0]

080484c0 <register_tm_clones>:
 80484c0:	mov    eax,0x804a02c
 80484c5:	sub    eax,0x804a02c
 80484ca:	sar    eax,0x2
 80484cd:	mov    edx,eax
 80484cf:	shr    edx,0x1f
 80484d2:	add    eax,edx
 80484d4:	sar    eax,1
 80484d6:	je     80484f8 <register_tm_clones+0x38>
 80484d8:	mov    edx,0x0
 80484dd:	test   edx,edx
 80484df:	je     80484f8 <register_tm_clones+0x38>
 80484e1:	push   ebp
 80484e2:	mov    ebp,esp
 80484e4:	sub    esp,0x10
 80484e7:	push   eax
 80484e8:	push   0x804a02c
 80484ed:	call   edx
 80484ef:	add    esp,0x10
 80484f2:	leave  
 80484f3:	ret    
 80484f4:	lea    esi,[esi+eiz*1+0x0]
 80484f8:	repz ret 
 80484fa:	lea    esi,[esi+0x0]

08048500 <__do_global_dtors_aux>:
 8048500:	cmp    BYTE PTR ds:0x804a02c,0x0
 8048507:	jne    8048520 <__do_global_dtors_aux+0x20>
 8048509:	push   ebp
 804850a:	mov    ebp,esp
 804850c:	sub    esp,0x8
 804850f:	call   8048480 <deregister_tm_clones>
 8048514:	mov    BYTE PTR ds:0x804a02c,0x1
 804851b:	leave  
 804851c:	ret    
 804851d:	lea    esi,[esi+0x0]
 8048520:	repz ret 
 8048522:	lea    esi,[esi+eiz*1+0x0]
 8048529:	lea    edi,[edi+eiz*1+0x0]

08048530 <frame_dummy>:
 8048530:	push   ebp
 8048531:	mov    ebp,esp
 8048533:	pop    ebp
 8048534:	jmp    80484c0 <register_tm_clones>

08048536 <print_flag>:
 8048536:	push   ebp
 8048537:	mov    ebp,esp
 8048539:	push   ebx
 804853a:	sub    esp,0x34
 804853d:	call   8048470 <__x86.get_pc_thunk.bx>
 8048542:	add    ebx,0x1abe
 8048548:	mov    eax,gs:0x14
 804854e:	mov    DWORD PTR [ebp-0xc],eax
 8048551:	xor    eax,eax
 8048553:	mov    BYTE PTR [ebp-0x33],0x6f
 8048557:	mov    BYTE PTR [ebp-0x32],0x68
 804855b:	mov    BYTE PTR [ebp-0x31],0x65
 804855f:	mov    BYTE PTR [ebp-0x30],0x72
 8048563:	mov    BYTE PTR [ebp-0x2f],0x60
 8048567:	mov    BYTE PTR [ebp-0x2e],0x6c
 804856b:	mov    BYTE PTR [ebp-0x2d],0x7d
 804856f:	mov    BYTE PTR [ebp-0x2c],0x67
 8048573:	mov    BYTE PTR [ebp-0x2b],0x6a
 8048577:	mov    BYTE PTR [ebp-0x2a],0x6a
 804857b:	mov    BYTE PTR [ebp-0x29],0x59
 804857f:	mov    BYTE PTR [ebp-0x28],0x72
 8048583:	mov    BYTE PTR [ebp-0x27],0x6e
 8048587:	mov    BYTE PTR [ebp-0x26],0x63
 804858b:	mov    BYTE PTR [ebp-0x25],0x75
 804858f:	mov    BYTE PTR [ebp-0x24],0x63
 8048593:	mov    BYTE PTR [ebp-0x23],0x59
 8048597:	mov    BYTE PTR [ebp-0x22],0x6b
 804859b:	mov    BYTE PTR [ebp-0x21],0x69
 804859f:	mov    BYTE PTR [ebp-0x20],0x6b
 80485a3:	mov    BYTE PTR [ebp-0x1f],0x63
 80485a7:	mov    BYTE PTR [ebp-0x1e],0x68
 80485ab:	mov    BYTE PTR [ebp-0x1d],0x72
 80485af:	mov    BYTE PTR [ebp-0x1c],0x75
 80485b3:	mov    BYTE PTR [ebp-0x1b],0x59
 80485b7:	mov    BYTE PTR [ebp-0x1a],0x6a
 80485bb:	mov    BYTE PTR [ebp-0x19],0x69
 80485bf:	mov    BYTE PTR [ebp-0x18],0x75
 80485c3:	mov    BYTE PTR [ebp-0x17],0x72
 80485c7:	mov    BYTE PTR [ebp-0x16],0x59
 80485cb:	mov    BYTE PTR [ebp-0x15],0x6f
 80485cf:	mov    BYTE PTR [ebp-0x14],0x68
 80485d3:	mov    BYTE PTR [ebp-0x13],0x59
 80485d7:	mov    BYTE PTR [ebp-0x12],0x72
 80485db:	mov    BYTE PTR [ebp-0x11],0x6f
 80485df:	mov    BYTE PTR [ebp-0x10],0x6b
 80485e3:	mov    BYTE PTR [ebp-0xf],0x63
 80485e7:	mov    BYTE PTR [ebp-0xe],0x7b
 80485eb:	mov    BYTE PTR [ebp-0xd],0x6
 80485ef:	mov    DWORD PTR [ebp-0x38],0x0
 80485f6:	jmp    8048630 <print_flag+0xfa>
 80485f8:	lea    edx,[ebp-0x33]
 80485fb:	mov    eax,DWORD PTR [ebp-0x38]
 80485fe:	add    eax,edx
 8048600:	movzx  eax,BYTE PTR [eax]
 8048603:	xor    eax,0x6
 8048606:	mov    ecx,eax
 8048608:	lea    edx,[ebp-0x33]
 804860b:	mov    eax,DWORD PTR [ebp-0x38]
 804860e:	add    eax,edx
 8048610:	mov    BYTE PTR [eax],cl
 8048612:	lea    edx,[ebp-0x33]
 8048615:	mov    eax,DWORD PTR [ebp-0x38]
 8048618:	add    eax,edx
 804861a:	movzx  eax,BYTE PTR [eax]
 804861d:	movsx  eax,al
 8048620:	sub    esp,0xc
 8048623:	push   eax
 8048624:	call   80483f0 <putchar@plt>
 8048629:	add    esp,0x10
 804862c:	add    DWORD PTR [ebp-0x38],0x1
 8048630:	cmp    DWORD PTR [ebp-0x38],0x26
 8048634:	jle    80485f8 <print_flag+0xc2>
 8048636:	nop
 8048637:	mov    eax,DWORD PTR [ebp-0xc]
 804863a:	xor    eax,DWORD PTR gs:0x14
 8048641:	je     8048648 <print_flag+0x112>
 8048643:	call   8048750 <__stack_chk_fail_local>
 8048648:	mov    ebx,DWORD PTR [ebp-0x4]
 804864b:	leave  
 804864c:	ret    

0804864d <main>:
 804864d:	lea    ecx,[esp+0x4]
 8048651:	and    esp,0xfffffff0
 8048654:	push   DWORD PTR [ecx-0x4]
 8048657:	push   ebp
 8048658:	mov    ebp,esp
 804865a:	push   ebx
 804865b:	push   ecx
 804865c:	sub    esp,0x60
 804865f:	call   8048470 <__x86.get_pc_thunk.bx>
 8048664:	add    ebx,0x199c
 804866a:	mov    eax,gs:0x14
 8048670:	mov    DWORD PTR [ebp-0xc],eax
 8048673:	xor    eax,eax
 8048675:	sub    esp,0xc
 8048678:	lea    eax,[ebx-0x1880]
 804867e:	push   eax
 804867f:	call   80483c0 <printf@plt>
 8048684:	add    esp,0x10
 8048687:	sub    esp,0x8
 804868a:	lea    eax,[ebp-0x5c]
 804868d:	push   eax
 804868e:	lea    eax,[ebx-0x186a]
 8048694:	push   eax
 8048695:	call   8048400 <__isoc99_scanf@plt>
 804869a:	add    esp,0x10
 804869d:	sub    esp,0x8
 80486a0:	lea    eax,[ebx-0x1867]
 80486a6:	push   eax
 80486a7:	lea    eax,[ebp-0x5c]
 80486aa:	push   eax
 80486ab:	call   80483b0 <strcmp@plt>
 80486b0:	add    esp,0x10
 80486b3:	test   eax,eax
 80486b5:	jne    80486bc <main+0x6f>
 80486b7:	call   8048536 <print_flag>
 80486bc:	mov    eax,0x0
 80486c1:	mov    edx,DWORD PTR [ebp-0xc]
 80486c4:	xor    edx,DWORD PTR gs:0x14
 80486cb:	je     80486d2 <main+0x85>
 80486cd:	call   8048750 <__stack_chk_fail_local>
 80486d2:	lea    esp,[ebp-0x8]
 80486d5:	pop    ecx
 80486d6:	pop    ebx
 80486d7:	pop    ebp
 80486d8:	lea    esp,[ecx-0x4]
 80486db:	ret    
 80486dc:	xchg   ax,ax
 80486de:	xchg   ax,ax

080486e0 <__libc_csu_init>:
 80486e0:	push   ebp
 80486e1:	push   edi
 80486e2:	push   esi
 80486e3:	push   ebx
 80486e4:	call   8048470 <__x86.get_pc_thunk.bx>
 80486e9:	add    ebx,0x1917
 80486ef:	sub    esp,0xc
 80486f2:	mov    ebp,DWORD PTR [esp+0x28]
 80486f6:	lea    esi,[ebx-0xf0]
 80486fc:	call   8048378 <_init>
 8048701:	lea    eax,[ebx-0xf4]
 8048707:	sub    esi,eax
 8048709:	sar    esi,0x2
 804870c:	test   esi,esi
 804870e:	je     8048735 <__libc_csu_init+0x55>
 8048710:	xor    edi,edi
 8048712:	lea    esi,[esi+0x0]
 8048718:	sub    esp,0x4
 804871b:	push   ebp
 804871c:	push   DWORD PTR [esp+0x2c]
 8048720:	push   DWORD PTR [esp+0x2c]
 8048724:	call   DWORD PTR [ebx+edi*4-0xf4]
 804872b:	add    edi,0x1
 804872e:	add    esp,0x10
 8048731:	cmp    esi,edi
 8048733:	jne    8048718 <__libc_csu_init+0x38>
 8048735:	add    esp,0xc
 8048738:	pop    ebx
 8048739:	pop    esi
 804873a:	pop    edi
 804873b:	pop    ebp
 804873c:	ret    
 804873d:	lea    esi,[esi+0x0]

08048740 <__libc_csu_fini>:
 8048740:	repz ret 
 8048742:	xchg   ax,ax
 8048744:	xchg   ax,ax
 8048746:	xchg   ax,ax
 8048748:	xchg   ax,ax
 804874a:	xchg   ax,ax
 804874c:	xchg   ax,ax
 804874e:	xchg   ax,ax

08048750 <__stack_chk_fail_local>:
 8048750:	push   ebx
 8048751:	call   8048470 <__x86.get_pc_thunk.bx>
 8048756:	add    ebx,0x18aa
 804875c:	sub    esp,0x8
 804875f:	call   80483d0 <__stack_chk_fail@plt>
```
```
objdump -S  -M intel blade --no-show-raw-insn

blade:     file format elf32-i386


Disassembly of section .init:

08048378 <_init>:
 8048378:	push   ebx
 8048379:	sub    esp,0x8
 804837c:	call   8048470 <__x86.get_pc_thunk.bx>
 8048381:	add    ebx,0x1c7f
 8048387:	mov    eax,DWORD PTR [ebx-0x4]
 804838d:	test   eax,eax
 804838f:	je     8048396 <_init+0x1e>
 8048391:	call   8048410 <__gmon_start__@plt>
 8048396:	add    esp,0x8
 8048399:	pop    ebx
 804839a:	ret    

Disassembly of section .plt:

080483a0 <.plt>:
 80483a0:	push   DWORD PTR ds:0x804a004
 80483a6:	jmp    DWORD PTR ds:0x804a008
 80483ac:	add    BYTE PTR [eax],al
	...

080483b0 <strcmp@plt>:
 80483b0:	jmp    DWORD PTR ds:0x804a00c
 80483b6:	push   0x0
 80483bb:	jmp    80483a0 <.plt>

080483c0 <printf@plt>:
 80483c0:	jmp    DWORD PTR ds:0x804a010
 80483c6:	push   0x8
 80483cb:	jmp    80483a0 <.plt>

080483d0 <__stack_chk_fail@plt>:
 80483d0:	jmp    DWORD PTR ds:0x804a014
 80483d6:	push   0x10
 80483db:	jmp    80483a0 <.plt>

080483e0 <__libc_start_main@plt>:
 80483e0:	jmp    DWORD PTR ds:0x804a018
 80483e6:	push   0x18
 80483eb:	jmp    80483a0 <.plt>

080483f0 <putchar@plt>:
 80483f0:	jmp    DWORD PTR ds:0x804a01c
 80483f6:	push   0x20
 80483fb:	jmp    80483a0 <.plt>

08048400 <__isoc99_scanf@plt>:
 8048400:	jmp    DWORD PTR ds:0x804a020
 8048406:	push   0x28
 804840b:	jmp    80483a0 <.plt>

Disassembly of section .plt.got:

08048410 <__gmon_start__@plt>:
 8048410:	jmp    DWORD PTR ds:0x8049ffc
 8048416:	xchg   ax,ax

Disassembly of section .text:

08048420 <_start>:
 8048420:	xor    ebp,ebp
 8048422:	pop    esi
 8048423:	mov    ecx,esp
 8048425:	and    esp,0xfffffff0
 8048428:	push   eax
 8048429:	push   esp
 804842a:	push   edx
 804842b:	call   8048453 <_start+0x33>
 8048430:	add    ebx,0x1bd0
 8048436:	lea    eax,[ebx-0x18c0]
 804843c:	push   eax
 804843d:	lea    eax,[ebx-0x1920]
 8048443:	push   eax
 8048444:	push   ecx
 8048445:	push   esi
 8048446:	mov    eax,0x804864d
 804844c:	push   eax
 804844d:	call   80483e0 <__libc_start_main@plt>
 8048452:	hlt    
 8048453:	mov    ebx,DWORD PTR [esp]
 8048456:	ret    
 8048457:	xchg   ax,ax
 8048459:	xchg   ax,ax
 804845b:	xchg   ax,ax
 804845d:	xchg   ax,ax
 804845f:	nop

08048460 <_dl_relocate_static_pie>:
 8048460:	repz ret 
 8048462:	xchg   ax,ax
 8048464:	xchg   ax,ax
 8048466:	xchg   ax,ax
 8048468:	xchg   ax,ax
 804846a:	xchg   ax,ax
 804846c:	xchg   ax,ax
 804846e:	xchg   ax,ax

08048470 <__x86.get_pc_thunk.bx>:
 8048470:	mov    ebx,DWORD PTR [esp]
 8048473:	ret    
 8048474:	xchg   ax,ax
 8048476:	xchg   ax,ax
 8048478:	xchg   ax,ax
 804847a:	xchg   ax,ax
 804847c:	xchg   ax,ax
 804847e:	xchg   ax,ax

08048480 <deregister_tm_clones>:
 8048480:	mov    eax,0x804a02c
 8048485:	cmp    eax,0x804a02c
 804848a:	je     80484b0 <deregister_tm_clones+0x30>
 804848c:	mov    eax,0x0
 8048491:	test   eax,eax
 8048493:	je     80484b0 <deregister_tm_clones+0x30>
 8048495:	push   ebp
 8048496:	mov    ebp,esp
 8048498:	sub    esp,0x14
 804849b:	push   0x804a02c
 80484a0:	call   eax
 80484a2:	add    esp,0x10
 80484a5:	leave  
 80484a6:	ret    
 80484a7:	mov    esi,esi
 80484a9:	lea    edi,[edi+eiz*1+0x0]
 80484b0:	repz ret 
 80484b2:	lea    esi,[esi+eiz*1+0x0]
 80484b9:	lea    edi,[edi+eiz*1+0x0]

080484c0 <register_tm_clones>:
 80484c0:	mov    eax,0x804a02c
 80484c5:	sub    eax,0x804a02c
 80484ca:	sar    eax,0x2
 80484cd:	mov    edx,eax
 80484cf:	shr    edx,0x1f
 80484d2:	add    eax,edx
 80484d4:	sar    eax,1
 80484d6:	je     80484f8 <register_tm_clones+0x38>
 80484d8:	mov    edx,0x0
 80484dd:	test   edx,edx
 80484df:	je     80484f8 <register_tm_clones+0x38>
 80484e1:	push   ebp
 80484e2:	mov    ebp,esp
 80484e4:	sub    esp,0x10
 80484e7:	push   eax
 80484e8:	push   0x804a02c
 80484ed:	call   edx
 80484ef:	add    esp,0x10
 80484f2:	leave  
 80484f3:	ret    
 80484f4:	lea    esi,[esi+eiz*1+0x0]
 80484f8:	repz ret 
 80484fa:	lea    esi,[esi+0x0]

08048500 <__do_global_dtors_aux>:
 8048500:	cmp    BYTE PTR ds:0x804a02c,0x0
 8048507:	jne    8048520 <__do_global_dtors_aux+0x20>
 8048509:	push   ebp
 804850a:	mov    ebp,esp
 804850c:	sub    esp,0x8
 804850f:	call   8048480 <deregister_tm_clones>
 8048514:	mov    BYTE PTR ds:0x804a02c,0x1
 804851b:	leave  
 804851c:	ret    
 804851d:	lea    esi,[esi+0x0]
 8048520:	repz ret 
 8048522:	lea    esi,[esi+eiz*1+0x0]
 8048529:	lea    edi,[edi+eiz*1+0x0]

08048530 <frame_dummy>:
 8048530:	push   ebp
 8048531:	mov    ebp,esp
 8048533:	pop    ebp
 8048534:	jmp    80484c0 <register_tm_clones>

08048536 <print_flag>:
 8048536:	push   ebp
 8048537:	mov    ebp,esp
 8048539:	push   ebx
 804853a:	sub    esp,0x34
 804853d:	call   8048470 <__x86.get_pc_thunk.bx>
 8048542:	add    ebx,0x1abe
 8048548:	mov    eax,gs:0x14
 804854e:	mov    DWORD PTR [ebp-0xc],eax
 8048551:	xor    eax,eax
 8048553:	mov    BYTE PTR [ebp-0x33],0x6f
 8048557:	mov    BYTE PTR [ebp-0x32],0x68
 804855b:	mov    BYTE PTR [ebp-0x31],0x65
 804855f:	mov    BYTE PTR [ebp-0x30],0x72
 8048563:	mov    BYTE PTR [ebp-0x2f],0x60
 8048567:	mov    BYTE PTR [ebp-0x2e],0x6c
 804856b:	mov    BYTE PTR [ebp-0x2d],0x7d
 804856f:	mov    BYTE PTR [ebp-0x2c],0x67
 8048573:	mov    BYTE PTR [ebp-0x2b],0x6a
 8048577:	mov    BYTE PTR [ebp-0x2a],0x6a
 804857b:	mov    BYTE PTR [ebp-0x29],0x59
 804857f:	mov    BYTE PTR [ebp-0x28],0x72
 8048583:	mov    BYTE PTR [ebp-0x27],0x6e
 8048587:	mov    BYTE PTR [ebp-0x26],0x63
 804858b:	mov    BYTE PTR [ebp-0x25],0x75
 804858f:	mov    BYTE PTR [ebp-0x24],0x63
 8048593:	mov    BYTE PTR [ebp-0x23],0x59
 8048597:	mov    BYTE PTR [ebp-0x22],0x6b
 804859b:	mov    BYTE PTR [ebp-0x21],0x69
 804859f:	mov    BYTE PTR [ebp-0x20],0x6b
 80485a3:	mov    BYTE PTR [ebp-0x1f],0x63
 80485a7:	mov    BYTE PTR [ebp-0x1e],0x68
 80485ab:	mov    BYTE PTR [ebp-0x1d],0x72
 80485af:	mov    BYTE PTR [ebp-0x1c],0x75
 80485b3:	mov    BYTE PTR [ebp-0x1b],0x59
 80485b7:	mov    BYTE PTR [ebp-0x1a],0x6a
 80485bb:	mov    BYTE PTR [ebp-0x19],0x69
 80485bf:	mov    BYTE PTR [ebp-0x18],0x75
 80485c3:	mov    BYTE PTR [ebp-0x17],0x72
 80485c7:	mov    BYTE PTR [ebp-0x16],0x59
 80485cb:	mov    BYTE PTR [ebp-0x15],0x6f
 80485cf:	mov    BYTE PTR [ebp-0x14],0x68
 80485d3:	mov    BYTE PTR [ebp-0x13],0x59
 80485d7:	mov    BYTE PTR [ebp-0x12],0x72
 80485db:	mov    BYTE PTR [ebp-0x11],0x6f
 80485df:	mov    BYTE PTR [ebp-0x10],0x6b
 80485e3:	mov    BYTE PTR [ebp-0xf],0x63
 80485e7:	mov    BYTE PTR [ebp-0xe],0x7b
 80485eb:	mov    BYTE PTR [ebp-0xd],0x6
 80485ef:	mov    DWORD PTR [ebp-0x38],0x0
 80485f6:	jmp    8048630 <print_flag+0xfa>
 80485f8:	lea    edx,[ebp-0x33]
 80485fb:	mov    eax,DWORD PTR [ebp-0x38]
 80485fe:	add    eax,edx
 8048600:	movzx  eax,BYTE PTR [eax]
 8048603:	xor    eax,0x6
 8048606:	mov    ecx,eax
 8048608:	lea    edx,[ebp-0x33]
 804860b:	mov    eax,DWORD PTR [ebp-0x38]
 804860e:	add    eax,edx
 8048610:	mov    BYTE PTR [eax],cl
 8048612:	lea    edx,[ebp-0x33]
 8048615:	mov    eax,DWORD PTR [ebp-0x38]
 8048618:	add    eax,edx
 804861a:	movzx  eax,BYTE PTR [eax]
 804861d:	movsx  eax,al
 8048620:	sub    esp,0xc
 8048623:	push   eax
 8048624:	call   80483f0 <putchar@plt>
 8048629:	add    esp,0x10
 804862c:	add    DWORD PTR [ebp-0x38],0x1
 8048630:	cmp    DWORD PTR [ebp-0x38],0x26
 8048634:	jle    80485f8 <print_flag+0xc2>
 8048636:	nop
 8048637:	mov    eax,DWORD PTR [ebp-0xc]
 804863a:	xor    eax,DWORD PTR gs:0x14
 8048641:	je     8048648 <print_flag+0x112>
 8048643:	call   8048750 <__stack_chk_fail_local>
 8048648:	mov    ebx,DWORD PTR [ebp-0x4]
 804864b:	leave  
 804864c:	ret    

0804864d <main>:
 804864d:	lea    ecx,[esp+0x4]
 8048651:	and    esp,0xfffffff0
 8048654:	push   DWORD PTR [ecx-0x4]
 8048657:	push   ebp
 8048658:	mov    ebp,esp
 804865a:	push   ebx
 804865b:	push   ecx
 804865c:	sub    esp,0x60
 804865f:	call   8048470 <__x86.get_pc_thunk.bx>
 8048664:	add    ebx,0x199c
 804866a:	mov    eax,gs:0x14
 8048670:	mov    DWORD PTR [ebp-0xc],eax
 8048673:	xor    eax,eax
 8048675:	sub    esp,0xc
 8048678:	lea    eax,[ebx-0x1880]
 804867e:	push   eax
 804867f:	call   80483c0 <printf@plt>
 8048684:	add    esp,0x10
 8048687:	sub    esp,0x8
 804868a:	lea    eax,[ebp-0x5c]
 804868d:	push   eax
 804868e:	lea    eax,[ebx-0x186a]
 8048694:	push   eax
 8048695:	call   8048400 <__isoc99_scanf@plt>
 804869a:	add    esp,0x10
 804869d:	sub    esp,0x8
 80486a0:	lea    eax,[ebx-0x1867]
 80486a6:	push   eax
 80486a7:	lea    eax,[ebp-0x5c]
 80486aa:	push   eax
 80486ab:	call   80483b0 <strcmp@plt>
 80486b0:	add    esp,0x10
 80486b3:	test   eax,eax
 80486b5:	jne    80486bc <main+0x6f>
 80486b7:	call   8048536 <print_flag>
 80486bc:	mov    eax,0x0
 80486c1:	mov    edx,DWORD PTR [ebp-0xc]
 80486c4:	xor    edx,DWORD PTR gs:0x14
 80486cb:	je     80486d2 <main+0x85>
 80486cd:	call   8048750 <__stack_chk_fail_local>
 80486d2:	lea    esp,[ebp-0x8]
 80486d5:	pop    ecx
 80486d6:	pop    ebx
 80486d7:	pop    ebp
 80486d8:	lea    esp,[ecx-0x4]
 80486db:	ret    
 80486dc:	xchg   ax,ax
 80486de:	xchg   ax,ax

080486e0 <__libc_csu_init>:
 80486e0:	push   ebp
 80486e1:	push   edi
 80486e2:	push   esi
 80486e3:	push   ebx
 80486e4:	call   8048470 <__x86.get_pc_thunk.bx>
 80486e9:	add    ebx,0x1917
 80486ef:	sub    esp,0xc
 80486f2:	mov    ebp,DWORD PTR [esp+0x28]
 80486f6:	lea    esi,[ebx-0xf0]
 80486fc:	call   8048378 <_init>
 8048701:	lea    eax,[ebx-0xf4]
 8048707:	sub    esi,eax
 8048709:	sar    esi,0x2
 804870c:	test   esi,esi
 804870e:	je     8048735 <__libc_csu_init+0x55>
 8048710:	xor    edi,edi
 8048712:	lea    esi,[esi+0x0]
 8048718:	sub    esp,0x4
 804871b:	push   ebp
 804871c:	push   DWORD PTR [esp+0x2c]
 8048720:	push   DWORD PTR [esp+0x2c]
 8048724:	call   DWORD PTR [ebx+edi*4-0xf4]
 804872b:	add    edi,0x1
 804872e:	add    esp,0x10
 8048731:	cmp    esi,edi
 8048733:	jne    8048718 <__libc_csu_init+0x38>
 8048735:	add    esp,0xc
 8048738:	pop    ebx
 8048739:	pop    esi
 804873a:	pop    edi
 804873b:	pop    ebp
 804873c:	ret    
 804873d:	lea    esi,[esi+0x0]

08048740 <__libc_csu_fini>:
 8048740:	repz ret 
 8048742:	xchg   ax,ax
 8048744:	xchg   ax,ax
 8048746:	xchg   ax,ax
 8048748:	xchg   ax,ax
 804874a:	xchg   ax,ax
 804874c:	xchg   ax,ax
 804874e:	xchg   ax,ax

08048750 <__stack_chk_fail_local>:
 8048750:	push   ebx
 8048751:	call   8048470 <__x86.get_pc_thunk.bx>
 8048756:	add    ebx,0x18aa
 804875c:	sub    esp,0x8
 804875f:	call   80483d0 <__stack_chk_fail@plt>

Disassembly of section .fini:

08048764 <_fini>:
 8048764:	push   ebx
 8048765:	sub    esp,0x8
 8048768:	call   8048470 <__x86.get_pc_thunk.bx>
 804876d:	add    ebx,0x1893
 8048773:	add    esp,0x8
 8048776:	pop    ebx
 8048777:	ret 
```

# easyCTF-2018-Adder
```
objdump -S -j .text -M intel adder --no-show-raw-insn

adder:     file format elf64-x86-64


Disassembly of section .text:

0000000000400860 <_start>:
  400860:	xor    ebp,ebp
  400862:	mov    r9,rdx
  400865:	pop    rsi
  400866:	mov    rdx,rsp
  400869:	and    rsp,0xfffffffffffffff0
  40086d:	push   rax
  40086e:	push   rsp
  40086f:	mov    r8,0x400cb0
  400876:	mov    rcx,0x400c40
  40087d:	mov    rdi,0x400b1e
  400884:	call   400800 <__libc_start_main@plt>
  400889:	hlt    
  40088a:	nop    WORD PTR [rax+rax*1+0x0]

0000000000400890 <deregister_tm_clones>:
  400890:	mov    eax,0x60207f
  400895:	push   rbp
  400896:	sub    rax,0x602078
  40089c:	cmp    rax,0xe
  4008a0:	mov    rbp,rsp
  4008a3:	ja     4008a7 <deregister_tm_clones+0x17>
  4008a5:	pop    rbp
  4008a6:	ret    
  4008a7:	mov    eax,0x0
  4008ac:	test   rax,rax
  4008af:	je     4008a5 <deregister_tm_clones+0x15>
  4008b1:	pop    rbp
  4008b2:	mov    edi,0x602078
  4008b7:	jmp    rax
  4008b9:	nop    DWORD PTR [rax+0x0]

00000000004008c0 <register_tm_clones>:
  4008c0:	mov    eax,0x602078
  4008c5:	push   rbp
  4008c6:	sub    rax,0x602078
  4008cc:	sar    rax,0x3
  4008d0:	mov    rbp,rsp
  4008d3:	mov    rdx,rax
  4008d6:	shr    rdx,0x3f
  4008da:	add    rax,rdx
  4008dd:	sar    rax,1
  4008e0:	jne    4008e4 <register_tm_clones+0x24>
  4008e2:	pop    rbp
  4008e3:	ret    
  4008e4:	mov    edx,0x0
  4008e9:	test   rdx,rdx
  4008ec:	je     4008e2 <register_tm_clones+0x22>
  4008ee:	pop    rbp
  4008ef:	mov    rsi,rax
  4008f2:	mov    edi,0x602078
  4008f7:	jmp    rdx
  4008f9:	nop    DWORD PTR [rax+0x0]

0000000000400900 <__do_global_dtors_aux>:
  400900:	cmp    BYTE PTR [rip+0x2019a9],0x0        # 6022b0 <completed.6345>
  400907:	jne    40091a <__do_global_dtors_aux+0x1a>
  400909:	push   rbp
  40090a:	mov    rbp,rsp
  40090d:	call   400890 <deregister_tm_clones>
  400912:	pop    rbp
  400913:	mov    BYTE PTR [rip+0x201996],0x1        # 6022b0 <completed.6345>
  40091a:	repz ret 
  40091c:	nop    DWORD PTR [rax+0x0]

0000000000400920 <frame_dummy>:
  400920:	cmp    QWORD PTR [rip+0x2014c8],0x0        # 601df0 <__JCR_END__>
  400928:	je     400948 <frame_dummy+0x28>
  40092a:	mov    eax,0x0
  40092f:	test   rax,rax
  400932:	je     400948 <frame_dummy+0x28>
  400934:	push   rbp
  400935:	mov    edi,0x601df0
  40093a:	mov    rbp,rsp
  40093d:	call   rax
  40093f:	pop    rbp
  400940:	jmp    4008c0 <register_tm_clones>
  400945:	nop    DWORD PTR [rax]
  400948:	jmp    4008c0 <register_tm_clones>

000000000040094d <_Z3geni>:
  40094d:	push   rbp
  40094e:	mov    rbp,rsp
  400951:	sub    rsp,0x20
  400955:	mov    DWORD PTR [rbp-0x14],edi
  400958:	mov    eax,0x16
  40095d:	mov    rdi,rax
  400960:	call   4007f0 <malloc@plt>
  400965:	mov    QWORD PTR [rbp-0x8],rax
  400969:	mov    rax,QWORD PTR [rbp-0x8]
  40096d:	mov    BYTE PTR [rax],0x79
  400970:	mov    rax,QWORD PTR [rbp-0x8]
  400974:	lea    rsi,[rax+0x1]
  400978:	mov    ecx,DWORD PTR [rbp-0x14]
  40097b:	mov    edx,0x92492493
  400980:	mov    eax,ecx
  400982:	imul   edx
  400984:	lea    eax,[rdx+rcx*1]
  400987:	sar    eax,0x2
  40098a:	mov    edx,eax
  40098c:	mov    eax,ecx
  40098e:	sar    eax,0x1f
  400991:	sub    edx,eax
  400993:	mov    eax,edx
  400995:	shl    eax,0x3
  400998:	sub    eax,edx
  40099a:	sub    ecx,eax
  40099c:	mov    edx,ecx
  40099e:	mov    eax,edx
  4009a0:	add    eax,0x30
  4009a3:	mov    BYTE PTR [rsi],al
  4009a5:	mov    rax,QWORD PTR [rbp-0x8]
  4009a9:	lea    rdx,[rax+0x2]
  4009ad:	mov    eax,DWORD PTR [rbp-0x14]
  4009b0:	add    eax,0x3c
  4009b3:	mov    BYTE PTR [rdx],al
  4009b5:	mov    rax,QWORD PTR [rbp-0x8]
  4009b9:	add    rax,0x3
  4009bd:	mov    BYTE PTR [rax],0x5f
  4009c0:	mov    rax,QWORD PTR [rbp-0x8]
  4009c4:	lea    rdx,[rax+0x4]
  4009c8:	mov    rax,QWORD PTR [rbp-0x8]
  4009cc:	add    rax,0x2
  4009d0:	movzx  eax,BYTE PTR [rax]
  4009d3:	sub    eax,0x14
  4009d6:	mov    BYTE PTR [rdx],al
  4009d8:	mov    rax,QWORD PTR [rbp-0x8]
  4009dc:	lea    rdx,[rax+0x5]
  4009e0:	mov    rax,QWORD PTR [rbp-0x8]
  4009e4:	add    rax,0x4
  4009e8:	movzx  eax,BYTE PTR [rax]
  4009eb:	add    eax,0x3
  4009ee:	mov    BYTE PTR [rdx],al
  4009f0:	mov    rax,QWORD PTR [rbp-0x8]
  4009f4:	lea    rdx,[rax+0x6]
  4009f8:	mov    rax,QWORD PTR [rbp-0x8]
  4009fc:	movzx  eax,BYTE PTR [rax+0x5]
  400a00:	mov    BYTE PTR [rdx],al
  400a02:	mov    rax,QWORD PTR [rbp-0x8]
  400a06:	add    rax,0x7
  400a0a:	mov    BYTE PTR [rax],0x65
  400a0d:	mov    rax,QWORD PTR [rbp-0x8]
  400a11:	lea    rdx,[rax+0x8]
  400a15:	mov    rax,QWORD PTR [rbp-0x8]
  400a19:	movzx  eax,BYTE PTR [rax+0x6]
  400a1d:	mov    BYTE PTR [rdx],al
  400a1f:	mov    rax,QWORD PTR [rbp-0x8]
  400a23:	lea    rdx,[rax+0x9]
  400a27:	mov    rax,QWORD PTR [rbp-0x8]
  400a2b:	movzx  eax,BYTE PTR [rax+0x3]
  400a2f:	mov    BYTE PTR [rdx],al
  400a31:	mov    rax,QWORD PTR [rbp-0x8]
  400a35:	add    rax,0xa
  400a39:	mov    BYTE PTR [rax],0x74
  400a3c:	mov    rax,QWORD PTR [rbp-0x8]
  400a40:	lea    rdx,[rax+0xb]
  400a44:	mov    rax,QWORD PTR [rbp-0x8]
  400a48:	add    rax,0xa
  400a4c:	movzx  eax,BYTE PTR [rax]
  400a4f:	sub    eax,0xc
  400a52:	mov    BYTE PTR [rdx],al
  400a54:	mov    rax,QWORD PTR [rbp-0x8]
  400a58:	add    rax,0xc
  400a5c:	mov    BYTE PTR [rax],0x72
  400a5f:	mov    rax,QWORD PTR [rbp-0x8]
  400a63:	add    rax,0xd
  400a67:	mov    BYTE PTR [rax],0x33
  400a6a:	mov    rax,QWORD PTR [rbp-0x8]
  400a6e:	add    rax,0xe
  400a72:	mov    BYTE PTR [rax],0x33
  400a75:	mov    rax,QWORD PTR [rbp-0x8]
  400a79:	lea    rdx,[rax+0xf]
  400a7d:	mov    rax,QWORD PTR [rbp-0x8]
  400a81:	movzx  eax,BYTE PTR [rax+0x3]
  400a85:	mov    BYTE PTR [rdx],al
  400a87:	mov    rax,QWORD PTR [rbp-0x8]
  400a8b:	add    rax,0x10
  400a8f:	mov    BYTE PTR [rax],0x6e
  400a92:	mov    rax,QWORD PTR [rbp-0x8]
  400a96:	lea    rdx,[rax+0x11]
  400a9a:	mov    rax,QWORD PTR [rbp-0x8]
  400a9e:	movzx  eax,BYTE PTR [rax+0x2]
  400aa2:	mov    BYTE PTR [rdx],al
  400aa4:	mov    rax,QWORD PTR [rbp-0x8]
  400aa8:	lea    rdx,[rax+0x12]
  400aac:	mov    rax,QWORD PTR [rbp-0x8]
  400ab0:	add    rax,0x10
  400ab4:	movzx  eax,BYTE PTR [rax]
  400ab7:	sub    eax,0x1
  400aba:	mov    BYTE PTR [rdx],al
  400abc:	mov    rax,QWORD PTR [rbp-0x8]
  400ac0:	add    rax,0x13
  400ac4:	mov    BYTE PTR [rax],0x73
  400ac7:	mov    rax,QWORD PTR [rbp-0x8]
  400acb:	add    rax,0x14
  400acf:	mov    BYTE PTR [rax],0x21
  400ad2:	mov    rax,QWORD PTR [rbp-0x8]
  400ad6:	add    rax,0x15
  400ada:	mov    BYTE PTR [rax],0xa
  400add:	mov    rax,QWORD PTR [rbp-0x8]
  400ae1:	leave  
  400ae2:	ret    

0000000000400ae3 <_Z9print_ptrPc>:
  400ae3:	push   rbp
  400ae4:	mov    rbp,rsp
  400ae7:	sub    rsp,0x20
  400aeb:	mov    QWORD PTR [rbp-0x18],rdi
  400aef:	mov    DWORD PTR [rbp-0x4],0x0
  400af6:	jmp    400b16 <_Z9print_ptrPc+0x33>
  400af8:	mov    eax,DWORD PTR [rbp-0x4]
  400afb:	movsxd rdx,eax
  400afe:	mov    rax,QWORD PTR [rbp-0x18]
  400b02:	add    rax,rdx
  400b05:	movzx  eax,BYTE PTR [rax]
  400b08:	movsx  eax,al
  400b0b:	mov    edi,eax
  400b0d:	call   4007d0 <putchar@plt>
  400b12:	add    DWORD PTR [rbp-0x4],0x1
  400b16:	cmp    DWORD PTR [rbp-0x4],0x14
  400b1a:	jle    400af8 <_Z9print_ptrPc+0x15>
  400b1c:	leave  
  400b1d:	ret    

0000000000400b1e <main>:
  400b1e:	push   rbp
  400b1f:	mov    rbp,rsp
  400b22:	sub    rsp,0x20
  400b26:	mov    DWORD PTR [rbp-0xc],0x0
  400b2d:	mov    DWORD PTR [rbp-0x10],0x0
  400b34:	mov    DWORD PTR [rbp-0x14],0x0
  400b3b:	mov    esi,0x400cd0
  400b40:	mov    edi,0x6021a0
  400b45:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400b4a:	lea    rax,[rbp-0xc]
  400b4e:	mov    rsi,rax
  400b51:	mov    edi,0x602080
  400b56:	call   400850 <_ZNSirsERi@plt>
  400b5b:	lea    rdx,[rbp-0x10]
  400b5f:	mov    rsi,rdx
  400b62:	mov    rdi,rax
  400b65:	call   400850 <_ZNSirsERi@plt>
  400b6a:	lea    rdx,[rbp-0x14]
  400b6e:	mov    rsi,rdx
  400b71:	mov    rdi,rax
  400b74:	call   400850 <_ZNSirsERi@plt>
  400b79:	mov    edx,DWORD PTR [rbp-0xc]
  400b7c:	mov    eax,DWORD PTR [rbp-0x10]
  400b7f:	add    edx,eax
  400b81:	mov    eax,DWORD PTR [rbp-0x14]
  400b84:	add    eax,edx
  400b86:	mov    edi,eax
  400b88:	call   40094d <_Z3geni>
  400b8d:	mov    QWORD PTR [rbp-0x8],rax
  400b91:	mov    edx,DWORD PTR [rbp-0xc]
  400b94:	mov    eax,DWORD PTR [rbp-0x10]
  400b97:	add    edx,eax
  400b99:	mov    eax,DWORD PTR [rbp-0x14]
  400b9c:	add    eax,edx
  400b9e:	cmp    eax,0x539
  400ba3:	jne    400bcc <main+0xae>
  400ba5:	mov    esi,0x400ce6
  400baa:	mov    edi,0x6021a0
  400baf:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bb4:	mov    rax,QWORD PTR [rbp-0x8]
  400bb8:	mov    rdi,rax
  400bbb:	call   400ae3 <_Z9print_ptrPc>
  400bc0:	mov    edi,0x400cef
  400bc5:	call   4007c0 <puts@plt>
  400bca:	jmp    400bdb <main+0xbd>
  400bcc:	mov    esi,0x400cf1
  400bd1:	mov    edi,0x6021a0
  400bd6:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bdb:	mov    rax,QWORD PTR [rbp-0x8]
  400bdf:	mov    rdi,rax
  400be2:	call   400840 <free@plt>
  400be7:	mov    eax,0x0
  400bec:	leave  
  400bed:	ret    

0000000000400bee <_Z41__static_initialization_and_destruction_0ii>:
  400bee:	push   rbp
  400bef:	mov    rbp,rsp
  400bf2:	sub    rsp,0x10
  400bf6:	mov    DWORD PTR [rbp-0x4],edi
  400bf9:	mov    DWORD PTR [rbp-0x8],esi
  400bfc:	cmp    DWORD PTR [rbp-0x4],0x1
  400c00:	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c02:	cmp    DWORD PTR [rbp-0x8],0xffff
  400c09:	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c0b:	mov    edi,0x6022b1
  400c10:	call   4007e0 <_ZNSt8ios_base4InitC1Ev@plt>
  400c15:	mov    edx,0x400cc8
  400c1a:	mov    esi,0x6022b1
  400c1f:	mov    edi,0x400820
  400c24:	call   400810 <__cxa_atexit@plt>
  400c29:	leave  
  400c2a:	ret    

0000000000400c2b <_GLOBAL__sub_I__Z3geni>:
  400c2b:	push   rbp
  400c2c:	mov    rbp,rsp
  400c2f:	mov    esi,0xffff
  400c34:	mov    edi,0x1
  400c39:	call   400bee <_Z41__static_initialization_and_destruction_0ii>
  400c3e:	pop    rbp
  400c3f:	ret    

0000000000400c40 <__libc_csu_init>:
  400c40:	push   r15
  400c42:	mov    r15d,edi
  400c45:	push   r14
  400c47:	mov    r14,rsi
  400c4a:	push   r13
  400c4c:	mov    r13,rdx
  400c4f:	push   r12
  400c51:	lea    r12,[rip+0x201180]        # 601dd8 <__frame_dummy_init_array_entry>
  400c58:	push   rbp
  400c59:	lea    rbp,[rip+0x201188]        # 601de8 <__init_array_end>
  400c60:	push   rbx
  400c61:	sub    rbp,r12
  400c64:	xor    ebx,ebx
  400c66:	sar    rbp,0x3
  400c6a:	sub    rsp,0x8
  400c6e:	call   400778 <_init>
  400c73:	test   rbp,rbp
  400c76:	je     400c96 <__libc_csu_init+0x56>
  400c78:	nop    DWORD PTR [rax+rax*1+0x0]
  400c80:	mov    rdx,r13
  400c83:	mov    rsi,r14
  400c86:	mov    edi,r15d
  400c89:	call   QWORD PTR [r12+rbx*8]
  400c8d:	add    rbx,0x1
  400c91:	cmp    rbx,rbp
  400c94:	jne    400c80 <__libc_csu_init+0x40>
  400c96:	add    rsp,0x8
  400c9a:	pop    rbx
  400c9b:	pop    rbp
  400c9c:	pop    r12
  400c9e:	pop    r13
  400ca0:	pop    r14
  400ca2:	pop    r15
  400ca4:	ret    
  400ca5:	nop
  400ca6:	nop    WORD PTR cs:[rax+rax*1+0x0]

0000000000400cb0 <__libc_csu_fini>:
  400cb0:	repz ret 
```
