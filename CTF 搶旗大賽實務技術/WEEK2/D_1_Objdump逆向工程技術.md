# Objdump逆向工程技術
```
objdump -d /bin/bash  ==> 預設使用 AT&T 語法格式
objdump -d -M intel /bin/bash ==> 使用intel 語法格式
```

```
objdump -S helloCTFer


注意編譯時要加

gcc helloCTFer.c -o helloCTFer -g
```

# 範例程式  
```
// helloCTFer.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n ”);
   return 0;
}
```

```
gcc helloCTFer.c -o helloCTFer -g
```
##
```
objdump -S helloCTFer

objdump -S -M intel helloCTFer

objdump -S -j .text -M intel helloCTFer --no-show-raw-insn  
```
### -M參數:
```
objdump: supported targets: elf32-i386 elf32-iamcu a.out-i386-linux pei-i386 elf32-little elf32-big elf64-x86-64 
elf32-x86-64 pei-x86-64 elf64-l1om elf64-k1om elf64-little elf64-big pe-x86-64 pe-bigobj-x86-64 pe-i386 plugin 
srec symbolsrec verilog tekhex binary ihex trad-core

objdump: supported architectures: i386 i386:x86-64 i386:x64-32 i8086 i386:intel i386:x86-64:intel i386:x64-32:intel 
        i386:nacl i386:x86-64:nacl i386:x64-32:nacl iamcu iamcu:intel l1om l1om:intel k1om k1om:intel plugin

The following i386/x86-64 specific disassembler options are supported for use
with the -M switch (multiple options should be separated by commas):
  x86-64      Disassemble in 64bit mode
  i386        Disassemble in 32bit mode
  i8086       Disassemble in 16bit mode
  
  att         Display instruction in AT&T syntax
  intel       Display instruction in Intel syntax
  
  
  att-mnemonic
              Display instruction in AT&T mnemonic
  intel-mnemonic
              Display instruction in Intel mnemonic

  addr64      Assume 64bit address size
  addr32      Assume 32bit address size
  addr16      Assume 16bit address size
  data32      Assume 32bit data size
  data16      Assume 16bit data size
  suffix      Always display instruction suffix in AT&T syntax
  amd64       Display instruction in AMD64 ISA
  intel64     Display instruction in Intel64 ISA
```

