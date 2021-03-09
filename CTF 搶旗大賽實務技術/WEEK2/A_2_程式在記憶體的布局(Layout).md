# 程式在記憶體的布局(Layout)  
```
Memory Layout of C Programs
https://www.geeksforgeeks.org/memory-layout-of-c-program/
```
```
==> 特別注意 高位址(stack) 與 低位址(heap)
```
## 使用到 Linux size command
```
The size command basically lists section sizes as well as total size for the input object file(s). 

指令語法 syntax:
size [-A|-B|--format=compatibility]
            [--help]
            [-d|-o|-x|--radix=number]
            [--common]
            [-t|--totals]
            [--target=bfdname] [-V|--version]
            [objfile...]
            
https://www.howtoforge.com/linux-size-command/
```

# 測試範例:變數的記憶體儲存
```
測試1:測試基準

```

## 測試1:測試基準
```
#include <stdio.h>
 
int main(void)
{
    return 0;
}
```

```
gcc memory-layout.c -o memory-layout
size memory-layout
```
### 32bit  Ubuntu 16.04 LTS

```
gcc ML.c -o ML
size ML
```
```
   text	   data	    bss	    dec	    hex	filename()
   1017	    272	      4	   1293	    50d	ML
   
 1017+272+4 = 1293() = ()
```

## 測試2:增加 未初始化 的 全域變數(Global variable)
```
#include <stdio.h>
 
int global; /* Uninitialized variable stored in bss*/
 
int main(void)
{
    return 0;
}
```
```
gcc memory-layout.c -o memory-layout
size memory-layout
```
## 測試3:增加 未初始化 的 靜態變數(static variable)
```
#include <stdio.h>
 
int global; /* Uninitialized variable stored in bss*/
 
int main(void)
{
    static int i; /* Uninitialized static variable stored in bss */
    return 0;
}
```

## 測試4:增加 初始化 的 靜態變數(static variable)
```
#include <stdio.h>
 
int global; /* Uninitialized variable stored in bss*/
 
int main(void)
{
    static int i = 100; /* Initialized static variable stored in DS*/
    return 0;
}
```

## 
```
#include <stdio.h>
 
int global = 10; /* initialized global variable stored in DS*/
 
int main(void)
{
    static int i = 100; /* Initialized static variable stored in DS*/
    return 0;
}
```
