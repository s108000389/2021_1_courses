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
