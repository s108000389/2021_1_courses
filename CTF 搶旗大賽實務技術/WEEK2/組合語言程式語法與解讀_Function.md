#
```


```

```
#include <stdio.h>
 
/* 函式宣告 */
int max(int num1, int num2);
 
int main ()
{
   /* 區域變數定義 */
   int a = 100;
   int b = 200;
   int ret;
 
   /* 調用函數來獲取最大值 */
   ret = max(a, b);
 
   printf( "Max value is : %d\n", ret );
 
   return 0;
}
 
/* 函數返回兩個數中較大的那個數 */
int max(int num1, int num2) 
{
   /* 區域變數聲明 */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```
