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
