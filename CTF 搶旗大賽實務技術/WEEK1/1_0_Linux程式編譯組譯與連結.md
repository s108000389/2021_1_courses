# Linux C 程式的編譯與運行:


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
### 預處理
```
gcc –E XXX.c –o XXX.i 
```

# 進階閱讀
```
 Advanced C and C++ Compiling by Milan Stevanovic (Apress, 2014).
 https://github.com/Apress/adv-c-cpp-compiling
```
