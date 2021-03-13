# Linux 工具集
```
file 
size 
string
hexdump | hd
```
### 資訊分析工具
```
ldd 
nm
objdump
readelf
```
### 部署階段工具
```
chrpath
patcheif
strip
ldconfig
```
### 運行時分析工具
```
strace
addr2line
gdb (GNU 調試器）
```
### 靜態庫工具


# 在 Linux 上分析二進位檔案的 10 種方法[作業:完成練習]
```
在 Linux 上分析二進位檔案的 10 種方法
https://linux.cn/article-12187-1.html

ltrace 命令==>顯示運行時從函數庫中調用的所有函數
strace 工具==>不是追蹤呼叫的函數庫，而是追蹤系統呼叫。系統呼叫是你與內核對接來完成工作的。


```

# 進階閱讀
### PRACTICAL BINARY ANALYSIS
```
Build Your Own Linux Tools for Binary Instrumentation, Analysis, and Disassembly
by Dennis Andriesse

https://practicalbinaryanalysis.com/

Virtual Machine and Code Samples
```
### Binary Hacks：駭客秘傳技巧一百招
```
高林哲, 鵜飼文敏, 佐藤祐介等  譯者：Studio Tib.
歐萊禮出版社：2013/05/30

以BH編號  ==>
BH3.使用file 檢查檔案種類
BH4.使用od 傾印binary檔  ==> hexdump
BH11.使用objcopy對執行檔嚴入資料
BH13.使用strings 抽出binary 檔案內的字串
```
# 實戰主題
```
高級C/C++編譯技術
（美）斯特瓦諾維奇
機械工業出版社  2015/04/01

Advanced C and C++ Compiling (Paperback)
英文/Milan Stevanovic/Apress出版日期：2014-04-28

https://github.com/apress/adv-c-cpp-compiling

https://book.douban.com/subject/26414485/
```
```
第13章平臺實戰
13.1 連結過程調試 238

13.2 確定二進位檔案類型 239

13.3 確定二進位檔案入口點 240
13.3.1 獲取可執行檔入口點 240
13.3.2 獲取動態庫入口點 240

13.4 列出符號資訊 241

13.5 查看節的信息 242
13.5.1 列出所有節的資訊 242
13.5.2 查看節的信息 242

13.6 查看段的信息 243

13.7 反彙編代碼 244
13.7.1 反彙編二進位檔案 244
13.7.2 反彙編正在運行的進程 244

13.8 判斷是否為調試構建 244
13.9 查看載入時依賴項 245
13.10 查看裝載器可以找到的庫檔 245


13.11 查看運行時動態連結的庫檔 245
13.11.1 strace實用程式 245
13.11.2 LD_DEBUG環境變數 246
13.11.3 /proc//maps文件 246
13.11.4 lsof實用程式 247
13.11.5 通過程式設計方式查看 248

13.12 創建和維護靜態程式庫 251
```

