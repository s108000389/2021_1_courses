# radare2
```

```
# 安裝
```
sudo apt-get install radare2
```
# KALI 64 已安裝
```
r2 -v

radare2 3.2.1 0 @ linux-x86-64 git.
commit: unknown build: 2019-03-02__19:36:59
```
```
r2 -h
Usage: r2 [-ACdfLMnNqStuvwzX] [-P patch] [-p prj] [-a arch] [-b bits] [-i file]
          [-s addr] [-B baddr] [-m maddr] [-c cmd] [-e k=v] file|pid|-|--|=
 --           run radare2 without opening any file
 -            same as 'r2 malloc://512'
 =            read file from stdin (use -i and -c to run cmds)
 -=           perform !=! command to run all commands remotely
 -0           print \x00 after init and every command
 -2           close stderr file descriptor (silent warning messages)
 -a [arch]    set asm.arch
 -A           run 'aaa' command to analyze all referenced code
 -b [bits]    set asm.bits
 -B [baddr]   set base address for PIE binaries
 -c 'cmd..'   execute radare command
 -C           file is host:port (alias for -c+=http://%s/cmd/)
 -d           debug the executable 'file' or running process 'pid'
 -D [backend] enable debug mode (e cfg.debug=true)
 -e k=v       evaluate config var
 -f           block size = file size
 -F [binplug] force to use that rbin plugin
 -h, -hh      show help message, -hh for long
 -H ([var])   display variable
 -i [file]    run script file
 -I [file]    run script file before the file is opened
 -k [OS/kern] set asm.os (linux, macos, w32, netbsd, ...)
 -l [lib]     load plugin file
 -L           list supported IO plugins
 -m [addr]    map file at given address (loadaddr)
 -M           do not demangle symbol names
 -n, -nn      do not load RBin info (-nn only load bin structures)
 -N           do not load user settings and scripts
 -q           quiet mode (no prompt) and quit after -i
 -Q           quiet mode (no prompt) and quit faster (quickLeak=true)
 -p [prj]     use project, list if no arg, load if no file
 -P [file]    apply rapatch file and quit
 -r [rarun2]  specify rarun2 profile to load (same as -e dbg.profile=X)
 -R [rr2rule] specify custom rarun2 directive
 -s [addr]    initial seek
 -S           start r2 in sandbox mode
 -t           load rabin2 info in thread
 -u           set bin.filter=false to get raw sym/sec/cls names
 -v, -V       show radare2 version (-V show lib versions)
 -w           open file in write mode
 -x           open without exec-flag (asm.emu will not work), See io.exec
 -X           same as -e bin.usextr=false (useful for dyldcache)
 -z, -zz      do not load strings or load them even in raw
```
# BINARY 加載 與 退出
```
BINARY 加載 

$ r2 ./adder
 -- Learn pancake as if you were radare!
[0x004004b0]> quit

退出控制枱，==> 輸入 Quit 或 Exit 或按 Ctrl+D：
```
# 
```
https://www.mdeditor.tw/pl/gvNU/zh-hk
```
```
r2 控制枱

(1)先分析BINARY ==> 使用 aaa 命令

$ r2 ./adder
 -- Sorry, radare2 has experienced an internal error.
[0x004004b0]>
[0x004004b0]>
[0x004004b0]> aaa

(2)取得BINARY的基本信息  ==> iI 命令
    二進制文件的格式（ELF、PE 等）、二進制的架構（x86、AMD、ARM 等），以及二進制是 32 位還是 64 位
    ：
列出二進制中存在的函數==> afl 命令

使用 s main 尋找 main 函數的地址，然後運行 pdf 命令來查看反彙編的指令
```
# easyCTF-2018-Adder
```
easyCTF-2018-Adder
https://github.com/asinggih/easyCTF-2018-writeups/blob/master/Reverse_Engineering/Adder.md
```
```
r2 ./adder 
[0x00400860]> aaa
[x] Analyze all flags starting with sym. and entry0 (aa)
[x] Analyze function calls (aac)
[x] Analyze len bytes of instructions for references (aar)
[x] Constructing a function name for fcn.* and sym.func.* functions (aan)
[x] Type matching analysis for all functions (aaft)
[x] Use -AA or aaaa to perform additional experimental analysis.
[0x00400860]> pdf
            ;-- section..text:
            ;-- rip:
/ (fcn) entry0 41
|   entry0 (func rtld_fini);
|           ; arg func rtld_fini @ rdx
|           0x00400860      31ed           xor ebp, ebp                ; [13] -r-x section size 1106 named .text
|           0x00400862      4989d1         mov r9, rdx                 ; func rtld_fini
|           0x00400865      5e             pop rsi                     ; int argc
|           0x00400866      4889e2         mov rdx, rsp                ; char **ubp_av
|           0x00400869      4883e4f0       and rsp, 0xfffffffffffffff0
|           0x0040086d      50             push rax
|           0x0040086e      54             push rsp
|           0x0040086f      49c7c0b00c40.  mov r8, sym.__libc_csu_fini ; 0x400cb0 ; func fini
|           0x00400876      48c7c1400c40.  mov rcx, sym.__libc_csu_init ; 0x400c40 ; "AWA\x89\xffAVI\x89\xf6AUI\x89\xd5ATL\x8d%\x80\x11 " ; func init
|           0x0040087d      48c7c71e0b40.  mov rdi, main               ; sym.main ; 0x400b1e ; func main
\           0x00400884      e877ffffff     call sym.imp.__libc_start_main ; int __libc_start_main(func main, int argc, char **ubp_av, func init, func fini, func rtld_fini, void *stack_end)
[0x00400860]> 
[0x00400860]> pdf@main
==>你就會看到答案
```
