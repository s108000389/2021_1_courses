# 黑客之道_漏洞發掘的藝術
```
Hacking, 2nd Edition
The Art of Exploitation
by Jon Erickson
February 2008, 488 pp., w/ CD
ISBN-13: 9781593271442

黑客之道 : 漏洞發掘的藝術, 2/e (Hacking: The Art of Exploitation, 2/e)
簡體中文/[美]喬恩·埃里克森（Jon Erickson）/人民郵電出版日期：2020-07-01
https://www.tenlong.com.tw/products/9787115535559
```

### 範例程式
```
https://github.com/intere/hacking
https://github.com/hayatoito/hacking-2nd

http://www.nostarch.com/download/booksrc.zip
```
### 下載live CD
```
http://www.nostarch.com/download/booksrc.zip

https://nostarch.com/hackingCD.htm
```
### 章節目錄_英文
```
0x100. INTRODUCTION

0x200. PROGRAMMING
0x210. What Is Programming?
0x220. Pseudo-code
0x230. Control Structures
0x231. If-Then-Else
0x232. While/Until Loops
0x233. For Loops
0x240. More Fundamental Programming Concepts
0x241. Variables
0x242. Arithmetic Operators
0x243. Comparison Operators
0x244. Functions
0x250. Getting Your Hands Dirty
0x250. Getting Your Hands Dirty
firstprog.c
0x251. The Bigger Picture
0x252. The x86 Processor
0x253. Assembly Language
ASCII Table
0x260. Back to Basics
0x261. Strings
char_array.c
char_array2.c
0x262. Signed, Unsigned, Long, and Short
datatype_sizes.c
0x263. Pointers
pointer.c
addressof.c
addressof2.c
0x264. Format Strings
fmt_strings.c
input.c
0x265. Typecasting
typecasting.c
pointer_types.c
pointer_types2.c
pointer_types3.c
pointer_types4.c
pointer_types5.c
0x266. Command-Line Arguments
commandline.c
convert.c
convert2.c
0x267. Variable Scoping
scope.c
scope2.c
scope3.c
static.c
static2.c
0x270. Memory Segmentation
0x270. Memory Segmentation
stack_example.c
0x271. Memory Segments in C
memory_segments.c
0x272. Using the Heap
heap_example.c
0x273. Error-Checked malloc()
errorchecked_heap.c
0x280. Building on Basics
0x281. File Access
simplenote.c
bitwise.c
fcntl_flags.c
0x282. File Permissions
0x283. User IDs
uid_demo.c
hacking.h
notetaker.c
notesearch.c
0x284. Structs
time_example.c
time_example2.c
0x285. Function Pointers
funcptr_example.c
0x286. Pseudo-random Numbers
rand_example.c
0x287. A Game of Chance
game_of_chance.c


0x300. EXPLOITATION
0x310. Generalized Exploit Techniques
0x320. Buffer Overflows
0x320. Buffer Overflows
overflow_example.c
exploit_notesearch.c
0x321. Stack-Based Buffer Overflow Vulnerabilities
auth_overflow.c
auth_overflow2.c
0x330. Experimenting with BASH
0x330. Experimenting with BASH
From exploit_notesearch.c
0x331. Using the Environment
getenv_example.c
getenvaddr.c
Code from libc-2.2.2
exploit_notesearch_env.c
0x340. Overflows in Other Segments
0x341. A Basic Heap-Based Overflow
Excerpt from notetaker.c
0x342. Overflowing Function Pointers
From game_of_chance.c
0x350. Format Strings
0x351. Format Parameters
fmt_uncommon.c
0x352. The Format String Vulnerability
fmt_vuln.c
0x353. Reading from Arbitrary Memory Addresses
0x354. Writing to Arbitrary Memory Addresses
0x355. Direct Parameter Access
0x356. Using Short Writes
0x357. Detours with .dtors
dtors_sample.c
0x358. Another notesearch Vulnerability
0x359. Overwriting the Global Offset Table


0x400. NETWORKING  網路
0x410. OSI Model
0x420. Sockets
0x421. Socket Functions
From /usr/include/bits/socket.h
From /usr/include/bits/socket.h
0x422. Socket Addresses
From /usr/include/bits/socket.h
From /usr/include/bits/socket.h
From /usr/include/netinet/in.h
0x423. Network Byte Order
0x424. Internet Address Conversion
0x425. A Simple Server Example
Added to hacking.h
simple_server.c
From a Remote Machine
On a Local Machine
0x426. A Web Client Example
From /etc/services
hacking-network.h
From /usr/include/netdb.h
host_lookup.c
webserver_id.c
0x427. A Tinyweb Server
tinyweb.c
0x430. Peeling Back the Lower Layers
0x431. Data-Link Layer
0x432. Network Layer
From RFC 791
0x433. Transport Layer
From RFC 793
0x440. Network Sniffing
0x441. Raw Socket Sniffer
raw_tcpsniff.c
0x442. libpcap Sniffer
pcap_sniff.c
0x443. Decoding the Layers
From /usr/include/if_ether.h
Added to hacking-network.h
From /usr/include/netinet/ip.h
From RFC 791
Added to hacking-network.h
From /usr/include/netinet/tcp.h
From RFC 793
Added to hacking-network.h
decode_sniff.c
0x444. Active Sniffing
From nemesis-arp.c
From nemesis.h
From nemesis-arp.c
From nemesis-proto_arp.c
From the libnet Man Page
From the arpspoof Man Page
arpspoof.c
From the libnet Man Page
0x450. Denial of Service
0x451. SYN Flooding
synflood.c
0x452. The Ping of Death
0x453. Teardrop
0x454. Ping Flooding
0x455. Amplification Attacks
0x456. Distributed DoS Flooding
0x460. TCP/IP Hijacking
0x461. RST Hijacking
rst_hijack.c
0x462. Continued Hijacking
0x470. Port Scanning
0x471. Stealth SYN Scan
0x472. FIN, X-mas, and Null Scans
0x473. Spoofing Decoys
0x474. Idle Scanning
0x475. Proactive Defense (shroud)
FIN Scan Before the Kernel Modification
FIN Scan After the Kernel Modification
shroud.c
0x480. Reach Out and Hack Someone
0x480. Reach Out and Hack Someone
From hacking-network.h
0x481. Analysis with GDB
0x482. Almost Only Counts with Hand Grenades
tinyweb_exploit.c
0x483. Port-Binding Shellcode
New Line from tinyweb_exploit2.c


0x500. SHELLCODE
0x510. Assembly vs. C
0x510. Assembly vs. C
helloworld.c
Man Page for the write() System Call
From /usr/include/unistd.h
0x511. Linux System Calls in Assembly
From /usr/include/asm-i386/unistd.h
helloworld.asm
0x520. The Path to Shellcode
0x521. Assembly Instructions Using the Stack
helloworld1.s
0x522. Investigating with GDB
0x523. Removing Null Bytes
helloworld2.s
helloworld3.s
0x530. Shell-Spawning Shellcode
0x530. Shell-Spawning Shellcode
exec_shell.c
exec_shell.s
tiny_shell.s
0x531. A Matter of Privilege
drop_privs.c
priv_shell.s
0x532. And Smaller Still
shellcode.s
0x540. Port-Binding Shellcode
0x540. Port-Binding Shellcode
bind_port.c
From /usr/include/linux/net.h
bind_port.s
0x541. Duplicating Standard File Descriptors
New Instructions from bind_shell1.s
0x542. Branching Control Structures
bind_shell.s
0x550. Connect-Back Shellcode
0x550. Connect-Back Shellcode
connectback_shell.s
From Another Terminal Window


0x600. COUNTERMEASURES
0x610. Countermeasures That Detect
0x620. System Daemons
0x621. Crash Course in Signals
signal_example.c
0x622. Tinyweb Daemon
tinywebd.c
0x630. Tools of the Trade
0x631. tinywebd Exploit Tool
xtool_tinywebd.sh
0x640. Log Files
0x640. Log Files
tinywebd Log File
0x641. Blend In with the Crowd
xtool_tinywebd_stealth.sh
0x650. Overlooking the Obvious
0x651. One Step at a Time
mark.s
0x652. Putting Things Back Together Again
mark_break.s
mark_restore.s
0x653. Child Laborers
loopback_shell_restore.s
0x660. Advanced Camouflage
0x661. Spoofing the Logged IP Address
Code Segment from tinywebd.c
addr_struct.c
xtool_tinywebd_spoof.sh
0x662. Logless Exploitation
xtool_tinywebd_silent.sh
0x670. The Whole Infrastructure
0x671. Socket Reuse
Excerpt from tinywebd.c
socket_reuse_restore.s
xtool_tinywebd_reuse.sh
0x680. Payload Smuggling
0x681. String Encoding
encoded_sockreuserestore_dbg.s
From Another Terminal
0x682. How to Hide a Sled
0x690. Buffer Restrictions
0x690. Buffer Restrictions
update_info.c
0x691. Polymorphic Printable ASCII Shellcode
printable_helper.c
printable.s
0x6a0. Hardening Countermeasures
0x6b0. Nonexecutable Stack
0x6b1. ret2libc
0x6b2. Returning into system()
vuln.c
0x6c0. Randomized Stack Space
0x6c0. Randomized Stack Space
aslr_demo.c
0x6c1. Investigations with BASH and GDB
0x6c2. Bouncing Off linux-gate
find_jmpesp.c
0x6c3. Applied Knowledge
0x6c4. A First Attempt
aslr_execl.c
0x6c5. Playing the Odds
aslr_execl_exploit.c


0x700. CRYPTOLOGY  密碼
0x710. Information Theory  資訊理論
0x711. Unconditional Security
0x712. One-Time Pads
0x713. Quantum Key Distribution
0x714. Computational Security
0x720. Algorithmic Run Time
0x721. Asymptotic Notation
0x730. Symmetric Encryption
0x731. Lov Grover's Quantum Search Algorithm
0x740. Asymmetric Encryption
0x741. RSA
0x742. Peter Shor's Quantum Factoring Algorithm
0x750. Hybrid Ciphers
0x751. Man-in-the-Middle Attacks
On Machine 192.168.42.250 (tetsuo), Connecting to 192.168.42.72 (loki)
On the Attacker's Machine
0x752. Differing SSH Protocol Host Fingerprints
From 192.168.42.250 (tetsuo), Just an Innocent Machine on the Network
On the Attacker's Machine, Setting Up mitm-ssh to Only Use SSH1 Protocol
Now Back on 192.168.42.250 (tetsuo)
0x753. Fuzzy Fingerprints
Normal Connection
MitM-Attacked Connection
0x760. Password Cracking
0x760. Password Cracking
crypt_test.c
0x761. Dictionary Attacks
crypt_crack.c
0x762. Exhaustive Brute-Force Attacks
0x763. Hash Lookup Table
0x764. Password Probability Matrix
ppm_gen.c
ppm_crack.c
0x770. Wireless 802.11b Encryption
0x771. Wired Equivalent Privacy
0x772. RC4 Stream Cipher
0x780. WEP Attacks
0x781. Offline Brute-Force Attacks
0x782. Keystream Reuse
0x783. IV-Based Decryption Dictionary Tables
0x784. IP Redirection
0x785. Fluhrer, Mantin, and Shamir Attack
fms.c


0x800. CONCLUSION
0x810. References
0x820. Sources
```
### 章節目錄_中文
```
第 1章 簡介 1

第 2章 編程 5
2.1 編程的含義 5
2.2 偽代碼 6
2.3 控制結構 7
2.3.1 If-Then-Else 7
2.3.2 While/Until循環 9
2.3.3 For循環 9
2.4 更多編程基本概念 10
2.4.1 變量 11
2.4.2 算術運算符 11
2.4.3 比較運算符 13
2.4.4 函數 15

2.5 動手練習 18
2.5.1 瞭解全域 19
2.5.2 x86處理器 22
2.5.3 匯編語言 23

2.6 接著學習基礎知識 36
2.6.1 字符串 36
2.6.2 signed、unsigned、long和short 40
2.6.3 指針 41
2.6.4 格式化字符串 46
2.6.5 強制類型轉換 49
2.6.6 命令行參數 56
2.6.7 變量作用域 60

2.7 內存(記憶體memory)分段 68
2.7.1 C語言中的內存分段 73
2.7.2 使用堆(heap) 75
2.7.3 對malloc()進行錯誤檢查 78

2.8 運用基礎知識構建程序 79
2.8.1文件訪問 80
2.8.2 文件權限 85
2.8.3 用戶ID 86
2.8.4 結構 94
2.8.5 函數指針 98
2.8.6 偽隨機數 99
2.8.7 猜撲克遊戲 100

第3章 漏洞發掘 113
3.1 通用的漏洞發掘技術 115
3.2 緩沖區溢出 116
3.3 嘗試使用BASH 131
3.4 其他內存段中的溢出 147
3.4.1 一種基本的基於堆的溢出 148
3.4.2 函數指針溢出 153

3.5 格式化字符串 166
3.5.1 格式化參數 166
3.5.2 格式化參數漏洞 168
3.5.3 讀取任意內存地址的內容 170
3.5.4 向任意內存地址寫入 171
3.5.5 直接參數訪問 178
3.5.6 使用short寫入 181
3.5.7 使用.dtors 182
3.5.8 notesearch程序的另一個漏洞 187
3.5.9 重寫全域偏移表 189

第4章 網絡 193
4.1 OSI模型 193

4.2 套接字 195
4.2.1 套接字函數 196
4.2.2 套接字地址 198
4.2.3 網絡字節順序 200
4.2.4 Internet地址轉換 200
4.2.5 一個簡單的服務器示例 201
4.2.6 一個Web客戶端示例 204
4.2.7 一個微型Web服務器 210

4.3 分析較低層的處理細節 214
4.3.1 數據鏈路層 215
4.3.2 網絡層 216
4.3.3 傳輸層 218

4.4 網絡嗅探 221
4.4.1 原始套接字嗅探 223
4.4.2 libpcap嗅探器 225
4.4.3 對層進行解碼 227
4.4.4 活動嗅探 237

4.5 拒絕服務 250
4.5.1 SYN泛洪 250
4.5.2 死亡之ping 254
4.5.3 淚滴攻擊 255
4.5.4 ping泛洪 255
4.5.5 放大攻擊 255
4.5.6 分布式DoS泛洪 256

4.6 TCP/IP劫持 256
4.6.1 RST劫持 257
4.6.2 持續劫持 262

4.7 端口掃描 262
4.7.1 秘密SYN掃描 263
4.7.2 FIN、X-mas和掃描 263
4.7.3 欺騙誘餌 264
4.7.4 空閒掃描 264
4.7.5 主動防禦(shroud) 266

4.8 發動攻擊 272
4.8.1 利用GDB進行分析 273
4.8.2 投彈 275
4.8.3 將shellcode綁定到端口 278

第5章 shellcode 281
5.1 對比匯編語言和C語言 281

5.2 開始編寫shellcode 286
5.2.1 使用堆棧的匯編語言指令 286
5.2.2 使用GDB進行分析 289
5.2.3 刪除字節 290

5.3 衍生shell的shellcode 295
5.3.1 特權問題 299
5.3.2 進一步縮短代碼 302

5.4 端口綁定shellcode 303
5.4.1 複製標準文件描述符 308
5.4.2 分支控制結構310

5.5 反向連接shellcode 315

第6章 對策 320
6.1 用於檢測入侵的對策 320

6.2 系統守護程序 321
6.2.1 信號簡介 322
6.2.2 tinyweb守護程序 325

6.3 攻擊工具 329

6.4 日誌文件 335

6.5 忽略明顯徵兆 337
6.5.1 分步進行 337
6.5.2 恢復原樣 342
6.5.3 子進程 348

6.6 高級偽裝 349
6.6.1 偽造記錄的IP地址 349
6.6.2 無日誌記錄的漏洞發掘 354

6.7 完整的基礎設施 357

6.8 偷運有效載荷 361
6.8.1 字符串編碼 362
6.8.2 隱藏NOP雪橇的方式 365

6.9 緩衝區約束 366

6.10 加固對策 379

6.11 不可執行堆棧 380
6.11.1 ret2libc 380
6.11.2 進入system() 380

6.12 隨機排列的堆棧空間 382
6.12.1 用BASH和GDB進行研究 384
6.12.2 探測linux-gate 388
6.12.3 運用知識 391
6.12.4 第 一次嘗試 392
6.12.5 多次嘗試終獲成功 393

第7章 密碼學 396
7.1 信息理論 397
7.1.1 絕對安全 397
7.1.2 一次性密碼簿 397
7.1.3 量子密鑰分發 397
7.1.4 計算安全性 398

7.2 算法運行時間 399
7.3 對稱加密 400

7.4 非對稱加密 402
7.4.1 RSA 402
7.4.2 Peter Shor的量子因子算法 405

7.5 混合密碼 406
7.5.1 中間人攻擊 407
7.5.2 不同的SSH協議主機指紋 411
7.5.3 模糊指紋 414

7.6 密碼攻擊 419
7.6.1 字典攻擊 420
7.6.2 窮舉暴力攻擊 423
7.6.3 散列查找表 424
7.6.4 密碼概率矩陣 425

7.7 無線802.11b加密 435
7.7.1 WEP 435
7.7.2 RC4流密碼 436

7.8 WEP攻擊 437
7.8.1 離線暴力攻擊 437
7.8.2 密鑰流重用 438
7.8.3 基於IV的解密字典表 439
7.8.4 IP重定向 439
7.8.5 FMS攻擊 440

第8章 寫在最後 451
```
### vuln.c
```
int main(int argc, char *argv[]) { 
   char buffer[5]; 
   strcpy(buffer, argv[1]); 
   return 0; 
} 
```
