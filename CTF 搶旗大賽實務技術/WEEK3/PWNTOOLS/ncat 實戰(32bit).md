# 32bit Ubuntu 16.04 LTS
```
nc 已安裝

須裝ncat

==> 居然是
sudo apy install nmap
```
```
ncat -h
Ncat 7.01 ( https://nmap.org/ncat )
Usage: ncat [options] [hostname] [port]

Options taking a time assume seconds. Append 'ms' for milliseconds,
's' for seconds, 'm' for minutes, or 'h' for hours (e.g. 500ms).
  -4                         Use IPv4 only
  -6                         Use IPv6 only
  -U, --unixsock             Use Unix domain sockets only
  -C, --crlf                 Use CRLF for EOL sequence
  -c, --sh-exec <command>    Executes the given command via /bin/sh
  -e, --exec <command>       Executes the given command
      --lua-exec <filename>  Executes the given Lua script
  -g hop1[,hop2,...]         Loose source routing hop points (8 max)
  -G <n>                     Loose source routing hop pointer (4, 8, 12, ...)
  -m, --max-conns <n>        Maximum <n> simultaneous connections
  -h, --help                 Display this help screen
  -d, --delay <time>         Wait between read/writes
  -o, --output <filename>    Dump session data to a file
  -x, --hex-dump <filename>  Dump session data as hex to a file
  -i, --idle-timeout <time>  Idle read/write timeout
  -p, --source-port port     Specify source port to use
  -s, --source addr          Specify source address to use (doesn't affect -l)
  -l, --listen               Bind and listen for incoming connections
  -k, --keep-open            Accept multiple connections in listen mode
  -n, --nodns                Do not resolve hostnames via DNS
  -t, --telnet               Answer Telnet negotiations
  -u, --udp                  Use UDP instead of default TCP
      --sctp                 Use SCTP instead of default TCP
  -v, --verbose              Set verbosity level (can be used several times)
  -w, --wait <time>          Connect timeout
      --append-output        Append rather than clobber specified output files
      --send-only            Only send data, ignoring received; quit on EOF
      --recv-only            Only receive data, never send anything
      --allow                Allow only given hosts to connect to Ncat
      --allowfile            A file of hosts allowed to connect to Ncat
      --deny                 Deny given hosts from connecting to Ncat
      --denyfile             A file of hosts denied from connecting to Ncat
      --broker               Enable Ncat's connection brokering mode
      --chat                 Start a simple Ncat chat server
      --proxy <addr[:port]>  Specify address of host to proxy through
      --proxy-type <type>    Specify proxy type ("http" or "socks4" or "socks5")
      --proxy-auth <auth>    Authenticate with HTTP or SOCKS proxy server
      --ssl                  Connect or listen with SSL
      --ssl-cert             Specify SSL certificate file (PEM) for listening
      --ssl-key              Specify SSL private key (PEM) for listening
      --ssl-verify           Verify trust and domain name of certificates
      --ssl-trustfile        PEM file containing trusted SSL certificates
      --ssl-ciphers          Cipherlist containing SSL ciphers to use
      --version              Display Ncat's version information and exit

See the ncat(1) manpage for full options, descriptions and usage examples

```
# 使用ncat建立程式運作方式

```
ncat -vc ./程式 -kl 127.0.0.1 8888

  -c, --sh-exec <command>    Executes the given command via /bin/sh
  -v, --verbose              Set verbosity level (can be used several times)

  -l, --listen               Bind and listen for incoming connections
  -k, --keep-open            Accept multiple connections in listen mode

持續等待 TCP 8888 連入，有的話就把 socket 接上 std I/O 並執行 ./oob1
Bind 在 localhost (127.0.0.1) 就好，不然其它人也會打得進來
```

# 連線方式 ==> 使用 nc 
```
nc 127.0.0.1 8888
```

# 範例 1:
### 使用ncat啟動連線與服務
```
//  1.c
#include <stdio.h>
 
int main()
{
    printf("Hello, CTFer! \n");
    return 0;
}
```

```
gcc -g 1.c -o 1
```

```
ncat -vc ./1 -kl 127.0.0.1 2000
```
### 使用nc進行連線
```
nc 127.0.0.1 2000
```

#
```
package main

import "fmt"

func main() {
    fmt.Println("Hello, CTFer!")
}
```
```
安裝 go

sudo apt install golang-go
```

```
 go -version
flag provided but not defined: -version
Go is a tool for managing Go source code.

Usage:

	go command [arguments]

The commands are:
	build       compile packages and dependencies
	clean       remove object files
	doc         show documentation for package or symbol
	env         print Go environment information
	fix         run go tool fix on packages
	fmt         run gofmt on package sources
	generate    generate Go files by processing source
	get         download and install packages and dependencies
	install     compile and install packages and dependencies
	list        list packages
	run         compile and run Go program
	test        test packages
	tool        run specified go tool
	version     print Go version
	vet         run go tool vet on packages

Use "go help [command]" for more information about a command.

Additional help topics:

	c           calling between Go and C
	buildmode   description of build modes
	filetype    file types
	gopath      GOPATH environment variable
	environment environment variables
	importpath  import path syntax
	packages    description of package lists
	testflag    description of testing flags
	testfunc    description of testing functions

Use "go help [topic]" for more information about that topic.
```

```
go run 2.go
Hello, CTFer!
```
```
go build 2.go
./2
```

```
ncat -vc ./2 -kl 127.0.0.1 2000
```
### 使用nc進行連線
```
nc 127.0.0.1 2000
```

```

```
