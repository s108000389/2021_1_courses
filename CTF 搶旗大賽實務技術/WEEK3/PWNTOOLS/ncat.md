# netcat(nc) | socat | Ncat
```
netcat(nc)原始版本是一個類Unix程式。原作者叫做*Hobbit*。
socat是netcat較複雜的姊妹程式。它比起netcat功能更多。
Ncat是由Nmap開發團隊實做的另一個netcat版本。
```
### nc
```
https://zh.wikipedia.org/wiki/Netcat

netcat (often abbreviated to nc) is a computer networking utility for 
reading from and writing to network connections using TCP or UDP. 

The command is designed to be a dependable back-end 
that can be used directly or easily driven by other programs and scripts. 

At the same time, it is a feature-rich network debugging and investigation tool, 
since it can produce almost any kind of connection its user could need 
and has a number of built-in capabilities.

Its list of features includes port scanning, transferring files, and port listening, 
and it can be used as a backdoor.
```
# ncat 
```

Ncat Reference Guide
https://nmap.org/book/ncat-man-options-summary.html
```
```
https://nmap.org/ncat/guide/ncat-exec.html

There are three ways of running a command:
--exec runs a command without shell interpretation.
--sh-exec runs a command by passing a string to a system shell.
--lua-exec runs a Lua program using Ncat's built-in Lua interpreter.
```
```
ncat -lkv -p port -c 'command'    
ncat -lkv -p port -e 'command'
```
# nc -h
```
[v1.10-41.1]
connect to somewhere:	nc [-options] hostname port[s] [ports] ... 
listen for inbound:	nc -l -p port [-options] [hostname] [port]
options:
	-c shell commands	as `-e'; use /bin/sh to exec [dangerous!!]
	-e filename		program to exec after connect [dangerous!!]
	-b			allow broadcasts
	-g gateway		source-routing hop point[s], up to 8
	-G num			source-routing pointer: 4, 8, 12, ...
	-h			this cruft
	-i secs			delay interval for lines sent, ports scanned
        -k                      set keepalive option on socket
	-l			listen mode, for inbound connects
	-n			numeric-only IP addresses, no DNS
	-o file			hex dump of traffic
	-p port			local port number
	-r			randomize local and remote ports
	-q secs			quit after EOF on stdin and delay of secs
	-s addr			local source address
	-T tos			set Type Of Service
	-t			answer TELNET negotiation
	-u			UDP mode
	-v			verbose [use twice to be more verbose]
	-w secs			timeout for connects and final net reads
	-C			Send CRLF as line-ending
	-z			zero-I/O mode [used for scanning]
port numbers can be individual or ranges: lo-hi [inclusive];
hyphens in port names must be backslash escaped (e.g. 'ftp\-data').
```
