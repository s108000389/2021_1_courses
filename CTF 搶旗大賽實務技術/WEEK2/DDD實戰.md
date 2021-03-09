

# 安裝
```
ksu@KSU-Ubuntu-1604-32:~/Downloads$ddd
The program 'ddd' is currently not installed. You can install it by typing:
sudo apt install ddd

ksu@KSU-Ubuntu-1604-32:~/Downloads$ sudo apt install ddd
[sudo] password for ksu: 
....一路安裝到底
```
# 範例學習
```
資料來源:
https://www.gnu.org/software/ddd/manual/html_mono/ddd.html#Sample%20Session
```
## 範例程式
```
/* sample.c -- Sample C program to be debugged with DDD */
     
     #include <stdio.h>
     #include <stdlib.h>
     
     static void shell_sort(int a[], int size)
     {
         int i, j;
         int h = 1;
         do {
             h = h * 3 + 1;
         } while (h <= size);
         do {
             h /= 3;
             for (i = h; i < size; i++)
             {
                 int v = a[i];
                 for (j = i; j >= h && a[j - h] > v; j -= h)
                     a[j] = a[j - h];
                 if (i != j)
                     a[j] = v;
             }
         } while (h != 1);
     }
     
     int main(int argc, char *argv[])
     {
         int *a;
         int i;
     
         a = (int *)malloc((argc - 1) * sizeof(int));
         for (i = 0; i < argc - 1; i++)
             a[i] = atoi(argv[i + 1]);
     
         shell_sort(a, argc);
     
         for (i = 0; i < argc - 1; i++)
             printf("%d ", a[i]);
         printf("\n");
     
         free(a);
         return 0;
     }
```

## 執行  ===> 由小排到大
```
ksu@KSU-Ubuntu-1604-32:~$ gedit sample.c
ksu@KSU-Ubuntu-1604-32:~$ gcc -g -o sample sample.c
ksu@KSU-Ubuntu-1604-32:~$ ./sample 8 7 5 4 1 3
0 1 3 4 5 7 
ksu@KSU-Ubuntu-1604-32:~$ ./sample 8000 7000 5000 1000 4000
1000 4000 5000 7000 8000 
```

## 除錯
```


```
