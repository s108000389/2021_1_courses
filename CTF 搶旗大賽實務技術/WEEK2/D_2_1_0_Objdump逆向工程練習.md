
# Objdump逆向工程練習.md
```

```
## objd1.c
```
// objd1.c
int main()
{
   return 0;
}
```
## objd2.c
```
// objd2.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n ”);
   return 0;
}
```
# IF SWITCH 測試


## objd2.c
```
#include<stdio.h>
 
int main()
{
    int num;
 
    printf("PLEASE INPUT A POSITIVE INTERGER: ");
    scanf("%d",&num);
 
    (num%2==0)?printf("EVEN"):printf("ODD");
}
```

## objd2.c
```

```

## objd2.c
```

```

## objd2.c
```

```

## objd2.c
```

```
# LOOP迴圈


## objd2.c
```

```


## objd2.c
```

```


## objd2.c
```

```
## objd2.c
```

```


## objd2.c
```

```

# 函數呼叫


## objd2.c
```

```

## objd2.c
```
#include <stdio.h>

/* 函數勳告 */
int max(int num1, int num2);
 
int main ()
{
   int a = 100;
   int b = 200;
   int ret;
 
   ret = max(a, b); 
   printf( "Max value is : %d\n", ret );
   return 0;
}
 

int max(int num1, int num2) 
{
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```
### RECURSIVE FUNCTION 遞迴函數
```
#include <stdio.h>
 
double factorial(unsigned int i)
{
   if(i <= 1)
   {
      return 1;
   }
   return i * factorial(i - 1);
}

int  main()
{
    int i = 15;
    printf("%d FACTORIAL IS %f\n", i, factorial(i));
    return 0;
}
```
# 指標 POINTER

## objd2.c
```

```


## objd2.c
```

```


## objd2.c
```

```
