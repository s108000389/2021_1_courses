# Chapter 4: Introduction to Format String Bugs
## 格式化輸出之美  ascii.c
```
#include <stdlib.h>
#include <stdio.h>

int main( int argc, char *argv[] )
{
     int c;

     printf( "Decimal Hex Character\n" );
     printf( "======= === =========\n" );

     for( c = 0x20; c < 256; c++ )
     {
            switch( c )
            {
                    case 0x0a:
                    case 0x0b:
                    case 0x0c:
                    case 0x0d:
                    case 0x1b:
                           printf( "%7d  %02x \n", c, c );
                           break;
                    default:
                           printf( "%7d  %02x %c\n", c, c, c );
                           break;
             } 
     } 

     return 1;
}
```
```
編輯程式 ==> gedit ascii.c
編譯==>  gcc ascii.c -o ascii
執行 ==> ./ascii 

Decimal Hex Character
======= === =========
     32  20  
     33  21 !
     34  22 "
     35  23 #
     36  24 $
     37  25 %
     38  26 &
     39  27 '

```
## 格式化輸出之漏洞 fmt.c
```
#include <stdio.h>
#include <stdlib.h>

int main( int argc, char *argv[] )
{
        if( argc != 2 )
        {
                printf("Error - supply a format string please\n");
                return 1;
        }

        printf( argv[1] );
        printf( "\n" );

        return 0;
}
```
```
編輯程式 ==> gedit fmt.c
編譯==>  gcc fmt.c -o fmt

執行 1 ==> ./fmt
  Error - supply a format string please

執行 2 ==> ./fmt aaa
  aaa
  
執行 3 ==>./fmt aaa bbb
Error - supply a format string please

```
