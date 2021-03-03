#
```
The Shellcoder's Handbook: 
Discovering and Exploiting Security Holes, 2nd Edition

https://www.wiley.com/en-us/The+Shellcoder%27s+Handbook%3A+Discovering+and+Exploiting+Security+Holes%2C+2nd+Edition-p-9780470080238
```

```
Part I: Introduction to Exploitation: Linux on x86.
Chapter 1: Before You Begin.
Chapter 2: Stack Overflows.
Chapter 3: Shellcode.
Chapter 4: Introduction to Format String Bugs.
Chapter 5: Introduction to Heap Overflows.

Part II: Other Platforms—Windows, Solaris, OS/X, and Cisco.
Chapter 6: The Wild World of Windows.
Chapter 7: Windows Shellcode.
Chapter 8: Windows Overflows.
Chapter 9: Overcoming Filters.
Chapter 10: Introduction to Solaris Exploitation.
Chapter 11: Advanced Solaris Exploitation.
Chapter 12: OS X Shellcode.
Chapter 13: Cisco IOS Exploitation.
Chapter 14: Protection Mechanisms.

Part III: Vulnerability Discovery.
Chapter 15: Establishing a Working Environment.
Chapter 16: Fault Injection.
Chapter 17: The Art of Fuzzing.
Chapter 18: Source Code Auditing: Finding Vulnerabilities in C-Based Languages.
Chapter 19: Instrumented Investigation: A Manual Approach.
Chapter 20: Tracing for Vulnerabilities.
Chapter 21: Binary Auditing: Hacking Closed Source Software.

Part IV: Advanced Materials.
Chapter 22: Alternative Payload Strategies.
Chapter 23: Writing Exploits that Work in the Wild.
Chapter 24: Attacking Database Software.
Chapter 25: Unix Kernel Overflows.
Chapter 26: Exploiting Unix Kernel Vulnerabilities.
Chapter 27: Hacking the Windows Kernel.
```
# Chapter 2: Stack Overflows.

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
