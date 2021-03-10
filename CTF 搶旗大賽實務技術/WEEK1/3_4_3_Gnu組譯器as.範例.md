#
```
32bit Helloworld
64bit Helloworld
```

# 32bit Helloworld
```
.global	_start

.text
_start:
	movl  $4, %eax   # 4 (code for "write" syscall) -> EAX register
	movl  $1, %ebx   # 1 (file descriptor for stdout) -> EBX (1st argument to syscall)
	movl  $msg, %ecx # address of msg string -> ECX (2nd argument)
	movl  $len, %edx # len (32 bit address) -> EDX (3rd arg)
	int   $0x80      # interrupt with location 0x80 (128), which invokes the kernel's system call procedure

	movl  $1, %eax   # 1 ("exit") -> EAX
	movl  $0, %ebx   # 0 (with success) -> EBX
	int   $0x80      # see previous
.data
msg:
	.ascii  "Hello, world!\n" # inline ascii string
	len =   . - msg           # assign value of (current address - address of msg start) to symbol "len"
```
```
as -c helloworld.s
ld helloworld.o -o helloworld
./helloworld
```
# 64 bit helloworld.s
```
https://gist.github.com/carloscarcamo/6833d19b726af698e62b
```
```
.global _start

.text

_start:
    # write (1, msj, 13)
    mov $1, %rax            # system call 1 is write
    mov $1, %rdi            # file handler 1 is stdout
    mov $message, %rsi      # address of string to output
    mov $13, %rdx           # number of bytes
    syscall

    # exit(0)
    mov $60, %rax           # system call 60 is exit
    xor %rdi, %rdi          # we want to return code 0
    syscall

message:
    .ascii "Hello, world\n"
```
## 組譯成64位元執行檔並執行
```
gcc -c hello.s && ld hello.o -o hello2 && ./hello2

file hello2 ==>
hello2: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, not stripped
```
```
as hello.s -o hello3.o && ld hello3.o -o hello3 && ./hello3

file hello3 ==>
```
```
[殘念]gcc -nostdlib hello.s -o hello3 && ./hello3
```
## 組譯成32位元執行檔並執行
```
as -- 32 -c hello32.s && ld hello32.o -o hello32 && ./hello32
```
