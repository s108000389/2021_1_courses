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

# 測試範例A :變數的記憶體儲存
```
測試1:測試基準
測試2:增加 未初始化 的 全域變數(Global variable)
測試3:增加 未初始化 的 靜態變數(static variable)
測試4:增加 初始化 的 靜態變數(static variable)
測試5:增加 未初始化 的 全域變數(Global variable)
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

## 測試5:增加 未初始化 的 全域變數(Global variable)
```
#include <stdio.h>
 
int global = 10; /* initialized global variable stored in DS*/
 
int main(void)
{
    static int i = 100; /* Initialized static variable stored in DS*/
    return 0;
}
```
# 測試範例B:
```
http://www.cyberplusindia.com/blog/index.php/2008/10/16/memory-layout-for-c-programs-in-linux/
```

```
/*
 * memorySegments.c
 * A program to illustrate the logical addressing space within processes
 * (c) 2008 Nagesh Rao, CyberPlus Infotech Pvt. Ltd.
 */

#include <stdio.h>
#include <stdlib.h>

int init_global_var = 10;        /* Initialized global variable */
int global_var;                  /* Uninitialized global variable */
static int init_static_var = 20; /* Initialized static variable in global scope */
static int static_var;           /* Uninitialized static variable in global scope */

int main(int argc, char **argv, char **envp)
{
        static int init_static_local_var = 30;   /* Initialized static local variable */
	static int static_local_var;             /* Uninitialized static local variable */
	int init_local_var = 40;                 /* Initialized local variable */
	int local_var;                           /* Uninitialized local variable */
	char *dynamic_var = (char*)malloc(100);  /* Dynamic variable */

	printf("Address of initialized global variable: %p\n", &init_global_var);
	printf("Address of uninitialized global variable: %p\n", &global_var);
	printf("Address of initialized static variable in global scope: %p\n", &init_static_var);
	printf("Address of uninitialized static variable in global scope: %p\n", &static_var);
	printf("Address of initialized static variable in local scope: %p\n", &init_static_local_var);
	printf("Address of uninitialized static variable in local scope: %p\n", &static_local_var);
	printf("Address of initialized local variable: %p\n", &init_local_var);
	printf("Address of uninitialized local variable: %p\n", &local_var);
	printf("Address of function (code): %p\n", &main);
	printf("Address of dynamic variable: %p\n", dynamic_var);
	printf("Address of environment variable: %p\n", &envp[0]);

	exit(0);
}
```
