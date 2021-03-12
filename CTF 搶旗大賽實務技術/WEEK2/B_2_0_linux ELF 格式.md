# linux ELF 分析
```
ELF
使用readelf分析ELF
使用objdump分析ELF
```
# ELF (Executable and Linkable Format)
```
https://en.wikipedia.org/wiki/Executable_and_Linkable_Format


Unix-like 系統中一種常用的 binary 封裝格式
以 segment + section 的方式劃出不同用途的區塊

一個 segment 可以包含多個 sections
Segment 和 section 的劃分都是編譯時決定的


Segment
符合記憶體的配置方式 (以 page 為單位，具特定權限)

Section
同樣特性的 section 可以集中在一個 segment 裡
每個 section 對應一個特定用途
.text (code) / .data / .rodata / .bss
```
```
Runtime執行時期

Binary (ELF) 中部份 segment 會被建立
內容來自檔案裡 (FileSiz)，也有可能是要一塊空的記憶體 (MemSiz)
實際上會消耗以 page (4096 bytes) 為單位的記憶體，多的部份一樣補零

Stack ==>  可能隨程式的執行而動態增減
Heap==> 在呼叫 malloc() 時會使用到

動態連結函式庫 (libraries)
通用的函式不會被編譯進 .text (code)，而是放在公用的函式庫裡
EX. libc.so (stdio.h, stdlib.h, string.h, …)
```
```
Runtime Memory Mapping: /proc/pid/maps
[1]讓程式在背景執行 ==>  ./a.out &
[2]查看 process ID ==> pidof a 
     29373
[3]再查看 ==>cat /proc/29373/maps
```
```
執行流程 ==>程式執行細節  組合語言說了算!
1.Entrypoint: _start
2.libc_start_main(main)
3.main(argc, argv)
4.Sub function calls (if any)
5.exit(0)
```
```
函式呼叫流程 (x86)

1.設定呼叫時參數
64 位元: 直接放在特定 register 上 (rdi, rsi, rdx, rcx, r8, r9)
32 位元: 依序放在 stack 上

2.使用 call 指令來呼叫函式
3.執行被呼叫的函式 (callee)
4.執行完後，使用 return 指令返回呼叫點的下一條指令
5.繼續執行原函式 (caller)
![image](https://user-images.githubusercontent.com/37649784/110990720-a8888700-83ae-11eb-8dea-a6085cec498e.png)

```
# 學習資源與推薦書
```
Binary Hacks － 駭客秘傳技巧一百招
高林 哲、鵜飼 文敏、佐藤 祐介、恩a 慎一郎、首藤 一幸 著、Studio Tib. 譯 歐萊禮 2013-05-29
https://www.tenlong.com.tw/products/9789862767665
```
      
```
The 101 of ELF files on Linux: Understanding and Analysis
https://linux-audit.com/elf-binaries-on-linux-understanding-and-analysis/

https://security-onigiri.github.io/2018/03/08/the-101-of-elf-binaries-on-linux-understanding-and-analysis.html

Linux ELF 二進位檔案入門：搞懂兼分析
https://security-onigiri.github.io/2018/03/08/the-101-of-elf-binaries-on-linux-understanding-and-analysis.html
```
```
In-depth: ELF - The Extensible & Linkable Format
觀看次數：57,548次•2020年10月28日
https://www.youtube.com/watch?v=nC1U1LJQL8o
```

```
readelf elf文件格式分析
https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/readelf.html
```
