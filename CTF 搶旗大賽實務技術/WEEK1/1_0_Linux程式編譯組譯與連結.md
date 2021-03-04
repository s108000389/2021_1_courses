# Linux C 程式的編譯與運行:
## 範例
```
// helloCTFer.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n ”);
   return 0;
}
```
## Unumtu 16.04 LTS(32 bits)
```
(1)編譯
   ==> gcc helloCTFer.c  ==>  產生a.out執行檔   
   ==> gcc helloCTFer.c -o helloCTFer
   ==> gcc helloCTFer.c -o helloCTFer.exe

(2)執行
    ==> ./a.out
    ==> ./helloCTFer
    ==> ./helloCTFer.exe
    
 (3)檢查執行檔檔案格式
    ==> file ./a.out
    ==> file ./helloCTFer
    ==> file ./helloCTFer.exe
```
```
file helloCTFer.exe 

helloCTFer.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=4258888fd293dae24c8143c584f1514ddcc7db0e, not strippe
```
```
ls -al  helloCTFer.*

-rw-rw-r-- 1 ksu ksu    76  三   5 01:23 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   5 01:32 helloCTFer.exe
```
```
hexdump -C helloCTFer.exe

00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............|
00000010  02 00 03 00 01 00 00 00  10 83 04 08 34 00 00 00  |............4...|
00000020  e0 17 00 00 00 00 00 00  34 00 20 00 09 00 28 00  |........4. ...(.|
00000030  1f 00 1c 00 06 00 00 00  34 00 00 00 34 80 04 08  |........4...4...|
00000040  34 80 04 08 20 01 00 00  20 01 00 00 05 00 00 00  |4... ... .......|
00000050  04 00 00 00 03 00 00 00  54 01 00 00 54 81 04 08  |........T...T...|
00000060  54 81 04 08 13 00 00 00  13 00 00 00 04 00 00 00  |T...............|
00000070  01 00 00 00 01 00 00 00  00 00 00 00 00 80 04 08  |................|
00000080  00 80 04 08 c4 05 00 00  c4 05 00 00 05 00 00 00  |................|

....................
```
### ELF File magic
```
ELF ==> 可執行與可鏈接格式 （英語：Executable and Linkable Format，縮寫為ELF），常被稱為ELF格式，
        在電腦科學中，是一种用於執行檔、目的檔、共享库和核心转储(core dump)的标准檔案格式。 
        
ELF defines the binary format of executable files used by Linux. 
When you invoke an executable, the OS must know how to load the executable into memory properly, 
how to resolve dynamic library dependencies and then where to jump into 
the loaded executable to start executing it. 
The ELF format provides this information. ELF magic is used to identify ELF files
and is merely the very first few bytes of a file:

ELF Magic ==> "Magic numbers" is the name given to constant sequences of bytes (usually) 
               at the beginning of files, used to mark those files as 
               being of a particular file format. 
               They serve a similar purpose to file extensions.

What is ELF Magic?
https://unix.stackexchange.com/questions/153352/what-is-elf-magic

ELF File magic ==> 7f 45 4c 46 01 01 01 00 
```
### hexdump 的用法
```
usage: hexdump [-bcCdovx] [-e fmt] [-f fmt_file] [-n length]
               [-s skip] [file ...]
       hd      [-bcdovx]  [-e fmt] [-f fmt_file] [-n length]
               [-s skip] [file ...]

hexdump還有很多的用法，具體可以參看man hexdump

https://man.linuxde.net/hexdump
https://www.itread01.com/article/1513751613.html
https://www.itread01.com/p/1385440.html
```
# Linux C 程式的編譯與運行:
```
編譯的各階段
 原始程式碼 ===>  
 預處理 ===> 
 編譯 ===>
 彙編 ===>
 連結 ===>
```
```
編譯的各階段
 原始程式碼 ===>  XXX.c
 預處理 ===> gcc –E XXX.c –o XXX.i    ===> 查看XXX.i的架構
 編譯 ===> gcc –S XXX.i  –o XXX.s   ===> 查看XXX.s的架構
 彙編 ===> gcc –c XXX.s –o XXX.o ===> 查看XXX.o的架構
 連結 ===> gcc  XXX.o –o XXX  ===> 查看XXX的架構
```

### 預處理
```
gcc –E XXX.c –o XXX.i 
```

# 進階閱讀
```
 Advanced C and C++ Compiling by Milan Stevanovic (Apress, 2014).
 https://github.com/Apress/adv-c-cpp-compiling
```
