#
```

```

#
```
#include <stdio.h>
#include <stdlib.h>

int main(int argc,char *argv[])
{
   if(argc != 3){ 
      printf("Usage:hello wordl word2");
      exit(0);
   }
   
   printf("wordl is %s \n word2 is %s \n" , argv[1] , argv[1]);

   //printstar();
   return (0);
}
```

## 
```
gcc test2.c -o test2

./test2

./test2 Google Linux
```

```
gcc -g test2.c -o test2

gdb ./test2
(gdb) run linux gdb
(gdb) show args
```
