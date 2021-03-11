# 教科書
```
王者歸來－Linux C 系統整合開發設計, 4/e
吳岳  佳魁資訊  2016-04-19

第9 章 gdb
9.1 列出來源程式
9.2 執行程式的指令 
9.3 操作中斷點的指令
9.4 檢視執行時資料 
9.5 改變程式的執行
9.6 gdb 高級應用
```

# 9.3 操作中斷點的指令
```
使用中斷點，是在偵錯工具過程中儘快找出問題所在的最佳方法。

break 指令用在偵錯工具的過程中為偵錯的程式設定中斷點。

在gdb 環境下，被偵錯工具將在執行時停止於中斷點處，
以進行檢視變數、設定訊號、改變程式執行等操作。
```

```
9.3.1 設定中斷點==>  使用者可以根據不同的需求，在多種情況下設定中斷點。
      1.在來源程式中指定的行上設定中斷點
         在來源程式檔賽中指定的行上設定中斷點，使程式執行到設定中斷點的行之前停止。
         break <line-number>
         (gdb) break 6
         實戰技術 ==> 首先使用list 指令列出原始檔案，
                     之後使用break 指令在原始檔案的一行上設定中斷點
                     
      2.在指定的函數前設定中斷點==>使程式執行到將要呼叫此函數之前停止
             break< function-name>
             (gdb) break printstar
             
      3.使用運算式設定中斷點 ==> 檢視執行中變數等於某值時程式的狀態
            break <line number> if <conditional expression>
            (gdb) break 12 if i==9  [在來源程式變數1 的值為9 時毆動在12 行的中斷點功能]
            
      4.在指定例程的入口處設定中斷點
            如果該程式是由很多原始檔案構成的，則可以在各個原始檔案中設定中斷點
            break <filename :line-number >
            break <filename : function-name>

            (gdb) break temp.c :10
            (gdb) break temp.c :main

9.3.2 顯示目前gdb 的中斷點資訊 ==> Info break

9.3.3 刪除指定的中斷點 ==> delete breakpoint <point-number>
                         (gdb) delete breakpoint 1
                         (gdb) d breakpoint 1
9.3.4 禁止或啟用中斷點==> 
       啟用中斷 ==> enable breakpoint <point-number>
                  (gdb) enable breakpoint 1   [敢用己禁用的1 號中斷點]
       禁止中斷 ==>disable breakpoint <point-number>
                  (gdb) disable breakpoint 1  [禁用1 號中斷點]
                  
9.3.5 清除中斷點==> clear 指令
      兩種方式，
           1.不帶參數的Clear 指令  ==> clear     [刪除程式上次停止處的中斷點]
           2. 帶參數的clear 指令  ==> clear <number>

9.3.6 觀察點 ==> watch 指令
                watch <condition>
                觀察點的用法與中斷點很相似，所有操作breakpoint 的指令對watchpoint 都適用。
                但區別在於:中斷點是在CPU 到某一位址取指令時中斷，而觀察點是在CPU 到某一位址讀寫資料時中斷。
```


## 觀察點實戰 ==> test3.c
```
#include <stdio.h>

int sum (inta){
  int i ,res=O;
  
  for(i=O ; i<a ;i ++){
    res +=i;

    return res ;
}

int main(void){
   int a= 10;
   int asum = sum(a);
   printf("sum is %d \n", asum); 
   return O;
}
```
```
(1)使用break 指令設定中斷點。
(gdb) break 7

(2)執行程式並使用 watch指令，設定觀察點運算式為i=3 。
(gdb) watch i ==3

(3)刪除中斷點1 。
(gdb) db 1

(4）繼續執行程式。
(gdb) continue
```
# GDB 實戰 ==>程式除錯
```
由程式的輸入 hello there
產生逆向文字的輸出
找出下列程式的錯誤!
```
## test4.c
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void my_print(char *string){
  printf("The string is %s\n", string);
}

void my_print2 (char *string){
   char *string2;
   int size, i;
   size = strlen(string);
    
   string2 = (char*) malloc(size+ 1);  /*為string2 分配儲存空間*/
  
    for(i = 0; i < size; i++)
       string2[size-i]= string[i];
       
    string2[size+1] = '\0' ;      /* ==>結束符號*/
    
    printf("The string printed backward is %s \n ", string2);
}

int main (void){
    char my_string[] = "hello there"; 
    my_print(my_string);
    my_print2(my_string);
    return 0;
}
```
### 執行此錯誤程式
```

gcc -g -o test4 test4.c

./test4
```

```
./test4

The string is hello there
The string printed backward is
```

### 使用gdb除錯
```

```
