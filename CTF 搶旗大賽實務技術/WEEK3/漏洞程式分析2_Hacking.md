#
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

### vuln.c
```
int main(int argc, char *argv[]) { 
   char buffer[5]; 
   strcpy(buffer, argv[1]); 
   return 0; 
} 
```
