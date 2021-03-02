# gcc編譯技術
```
GCC, the GNU Compiler Collection
https://gcc.gnu.org/
```
# gcc 常用指令
```
gcc -v
```
```

```
# 範例
## 範例1>compile 32-bit program on 64-bit gcc in C and C++
```
https://www.geeksforgeeks.org/compile-32-bit-program-64-bit-gcc-c-c/
```
```
// C program to demonstrate difference 
// in output in 32-bit and 64-bit gcc 
// File name: geek.c 
#include<stdio.h> 
int main() 
{ 
    printf("Size = %lu", sizeof(size_t)); 
} 
```
```
gcc -m32 geek.c -o geek
./out
Size = 4
```
```
gcc -m64 geek.c -o out
./out
Size = 8
```
```
For C language: sudo apt-get install gcc-multilib
For C++ language: sudo apt-get install g++-multilib
```
## 範例2>
