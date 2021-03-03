# NASM組合語言實戰範例
```


```
# How To Install nasm on kali
```
sudo apt-get install nasm

https://installlion.com/kali/kali/main/n/nasm/install/index.html

How to install NASM and compile Assembly program in kali linux.
- July 22, 2018
http://mycodingpage.blogspot.com/2018/07/how-to-install-and-compile-assembly.html
```
# 檢查linux 是否為64位元
```
cat /proc/version


Linux version 4.19.0-kali4-amd64 (devel@kali.org) 
(gcc version 8.3.0 (Debian 8.3.0-2)) #1 SMP Debian 4.19.28-2kali1 (2019-03-18)
```
# 範例程式1: 
## hello.asm
```
section .text
 global _start
  _start:
 mov edx,len
 mov ecx,msg
 mov ebx,1
 mov eax,4
 int 0x80
 
 mov eax,1
 int 0x80

  section .data
  msg db 'hello World!' , 0xa
  len equ $ -msg
```
## 組譯與執行 ==> 64 位元執行檔(binary)
```
nasm -f elf64 hello.asm     # assemble the program  64位元

ld hello.o -o hello

./hello
```
### binary 簡單分析
```
file hello

hello: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, not stripped
```
```
strings hello


hello World!
hello.asm
__bss_start
_edata
_end
.symtab
.strtab
.shstrtab
.note.gnu.property
.text
.data
```

## 組譯與執行 ==> 32 位元執行檔(binary)
```
nasm -f elf32 hello.asm -o hello2.o

ld -m elf_i386  hello2.o -o hello

./hello
```

### binary 簡單分析
```
file hello

hello: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, not stripped
```
```
strings hello


hello World!
hello.asm
__bss_start
_edata
_end
.symtab
.strtab
.shstrtab
.note.gnu.property
.text
.data
```

```
hexdump hello


0000000 457f 464c 0101 0001 0000 0000 0000 0000
0000010 0002 0003 0001 0000 9000 0804 0034 0000
0000020 2128 0000 0000 0000 0034 0020 0004 0028
0000030 0007 0006 0001 0000 0000 0000 8000 0804
0000040 8000 0804 00d0 0000 00d0 0000 0004 0000
0000050 1000 0000 0001 0000 1000 0000 9000 0804
0000060 9000 0804 001d 0000 001d 0000 0005 0000
0000070 1000 0000 0001 0000 2000 0000 a000 0804

```
# ld
```
ld -V
GNU ld (GNU Binutils for Debian) 2.31.1
  Supported emulations:
   elf_x86_64
   elf32_x86_64
   elf_i386
   elf_iamcu
   elf_l1om
   elf_k1om
   i386pep
   i386pe
```
